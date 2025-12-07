# Resilient Architectures

* Resiliency is the ability of an application to avoid and recover from failures. 
* Resilience is quantified in terms of availability.
* Availability is a metric as the percentage of time the application is performing as expected.

## Availability

Availability if often referred to by the number of nines. 

| Number of Nines | Availability | Annual Downtime              |
|-----------------|--------------|------------------------------|
| 2               | 99%          | 3 days, 15 hours, 39 minutes |
| 3               | 99.9%        | 8 hours, 45 minutes          |
| -               | 99.95%       | 4 hours, 22 minutes          |
| 4               | 99.99%       | 52 minutes                   |
| 5               | 99.999%      | 5 minutes                    |


* Many factors impact availability. The calculations covered by the AWS exam only cover AWS services.
* The best way to maximize availability is to avoid failure. This can be done by deploying multiple smaller application isntances across multiple availability zones instead of a single instance. This prevents the failure of an entire availability zone from bringing your application down.
* If enough of your instances fail you can experience performance issues or more application failures. So, you need a way to recreate instances after failure.

## Traditional Applications

Applications that are written to utilize traditional Linux or Windows servers. To run these applications on AWS you will
use one or more EC2 instances. Databases can either be run on an EC2 instance you manage or using a managed service
such as Amazon Relational Database Service (RDS).

* Dependencies on AWS services such as RDS or EC2 are hard dependencies.
* To calculate the availability multiply the availability of each service.

```
 .9 (single EC2) x .9995 (RDS multi-AZ) = 0.89955 (89.995%)
```

* To increase availability you can add multiple EC2 instances and load balance traffic.
* To calculate the availability of three EC2 instances in a cluster take 100% minus the product of the instance failure rate.

```
1 - (.1 x .1 x .1) = .999
```

Page 250

## Cloud-Native Applications

Cloud-Native applications are written to use the resources of a specific cloud platform. 

## AWS Lambda

* Allows you to write serverless functions using a variety of languages 
  (e.g. C#, Go, Java, Python, JavaScript, etc.).
* Useful for performing intermittent tasks that don't warrant keeping a running EC2 instance.
* You are only billed for the time that the function runs.
  
## Limits

* AWS imposes limits to prevent anyone (accidentally or intentionally) from consuming all resources. 
* Limits vary by service and can be viewed for your account in the AWS Trusted Advisor tool.
* Limits can be increased by request to AWS support or by adding another availability zone/region. 

## EC2 Auto Scaling

EC2 Auto Scalingh offers a way to prevent and recover from application 
failure automatically. It can add and remove instances automatically based
on defined rules.

* **Launch Configurations** - A document that contains the information needed
  to launch an EC2 instance (the same details you would provide through the
  web console). A Launch Configuration can be created based off of an existing
  EC2 instance.
* **Launch Templates** - A document that contains information needed to    
  launch an EC2 instance and can be used for EC2 Auto Scaling, creation of 
  one-off instances, or for spot fleets. Templates are versioned allowing you 
  to change them after creation.

Launch configurations are the older of the two mechanisms and AWS recommends
using Launch Templates

### Auto Scaling Groups

* A group of EC2 instances that auto scaling manages.
* You must specify a launch configuration or template.
* You then have options to set the minimum and maximum sizes of the auto scaling group.
  * **Minimum** - Ensures that the minimum number of healthy EC2 instances
    never drops below the requested value.
  * **Maximum** - Ensures that the maximum number of healthy EC2 instances
    never exceeds the requested value.
  * **Desired Capacity** - Optional setting that must be between the minimum
    and maximum values. Auto scaling will add or remove the required number
    of instances to maintain the desired capacity.
* To enable application load balancing you can specify an application load 
  balancer target group. Auto scaling will then automatically add/remove 
  instances from the target group.
* When configuring an auto scaling group you can configure health checks to 
  be used to monitor your application. When an instance fails the health
  check traffic will be routed elsewhere. 

### Auto Scaling Options

* **Manual Scaling** - You manage the scaling parameters yourself.
* **Dynamic Scaling Policies** - Scaling rules can be configured to apply 
  based on metrics such as CPU usage, request count per target, etc. You
  can also use metrics filters from CloudWatch logs.
* **SimpleScaling Policies** - Whenever a metric goes above a threshold
  Auto Scaling increases the desired capacity.
  * *ChangeInCapacity* - Increase by a specified amount.
  * *ExactCapacity* - Set to a specific value regardless of current value.
  * *PercentChangeInCapacity* - Increase capacity by a percentage of the 
    current amount.
* **Step Scaling Policies** - Add instances based on how much the aggregate
  metric exceeded the threadhold. This can be useful when demand on your
  application increases rapidly and simple scaling might not keep up.
* **Target Tracking Policies** - You select a metric and a target value. 
  Then Auto Scaling will create a CloudWatch Alarm and a scaling policy
  to try to keep the metric near the target.
* **Scheduled Actions** - Can be useful for predictable workloads where 
  you want to increase or decrease capacity at specific times.

## Data Backup & Recovery

### S3

* Aside from One-Zone Infrequent Access all classes distribute data
  across multiple availability zones.
* Enable S3 versioning to protect against deletion and data corruption.
* Enable cross region replication to protect against region or multiple
  availability zone failures.


### Elastic File System (EFS)

* Backup data to an S3 bucket or to an EFS volume in another region.
* AWS Backup Service can be used to schedule incremental backups.

### Elastic Block Storage (EBS)

* Automatically replicated to multiple availability zones in a region
  to protect against single availability zone failures.
* Easiest way to back up an EBS volume is to create a snapshot. Snapshots
  are stored in multiple availability zones in S3. 
* Note: Often application logs get stored on an EBS volume. When an EC2 
  instance is terminated the associated EBS volume is deleted. CloudWatch
  Logs can collect and store the logs from an instance in real time.

### Databases

* Options for backups will vary depending on the database being used.
* **Your Own Server** - If you are running your own database server on EC2
  then you will need to use your database's native backup tools. The backup
  files can then be stored on S3.
* **Relational Database Service (RDS)** - Easy option of making a database
  instance snapshot. You can also add a multi-AZ RDS deployment for additional
  resiliency.
* **Amazon Aurora** - Can provide maximum resiliency by using Amazon Aurora
  with multiple Aurora replicas. Aurora automatically stores data across three
  availability zones. Allows for the creation of up to 15 replicas. 
* **DynamoDB** - Stores tables across multiple availibility zones. You can
  configure point in time recovery to automatically take backups of your data.
  This allows you to recover to any point in time from 5 minutes before the
  current time up to 35 days.

## Network Resilience

* VPC considerations
  * When creating a VPC be sure to choose a sufficiently large CIDR block for
    your network. As you add redundancy you will need more IPs. 
  * When creating subnets leave unused capacity within your CIDR block to add
    additional subnets later.
  * Extra capacity for IP addresses in your subnets and VPC will be needed if
    you have to later scale your application.
* External Connectivity
  * The most common way to connect to AWS hosted resources is over the 
    internet.
  * For mission critical applications you may want to use Direct Connect
    to avoid a slow internet connection. This can offer speeds of 1Gbps or 
    10 Gbps with consistent latency.

## Simple Queue Service (SQS)

* Useful in building applications with loose coupling between services.
* A managed service that allows different application components to pass
  messages back and forth via queues.
* Queues
  * A producer creates a message and places it on the queue.
  * A consumer takes a message from the queue and processes it.
  * Messages can be up to 256KB in size.
* **Visibility Timeout** - Prevents any other consumers from reading a message
  within a specified amount of time. This is to help prevent multiple 
  consumers processing the same message. Default is 30 seconds, but can range
  from 0 seconds to 12 hours.
* **Retention Period** - Specifies how long a message can remain in a queue. 
  Default value is 4 days, but can be configured to be anwhere from 1 minute
  to 14 days.
* **Delay Queues** - By default the per-queue delay is 0 seconds, but can be 
  set to up to 15 minutes. 
* **Message Timers** - Delay can also be set for an individual message and
  defaults to 0 seconds. This can be configured as high as 15 minutes.

### Queue Types

* Standard
  * Approx. 120,000 in-flight messages.
  * This is the default queue type. 
  * Messages may be delivered out of order.
  * Can result in duplicate messages.
* First-In, First-Out (FIFO)
  * Support sending about 3,000 messages per second.
  * Messages are guaranteed to be delivered in the order they are sent.
  * Eliminates the possibility of duplicate messages.
  * Can handle about 20,000 in-flight messages.
* Dead Letter Queues
  * If your application cannot process a message for some reason you can 
    have SQS pull the message from your queue and place it in a dead letter
    queue.
  * Has a retention policy like all queue types and the deletion will be 
    based on the timestamp of the original creation.
 * Polling
   * Short Polling - SQS checks only a subset of servers for waiting messages 
     and gives an immediate response of either a message or a response
     indicating there are no messages.
   * Long Polling - SQS ensures you receive any message waiting in the queue. 
     A long polling request can take up to 20 seconds to return a response. 
     This is the cheaper option since you do not have to make as many 
     requests to the SQS service.