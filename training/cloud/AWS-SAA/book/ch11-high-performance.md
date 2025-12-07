# High-Performance Architectures

## Optimizing for performance

### Compute

* EC2 Instance parameters to consider
  * **ECUs** - EC2 Compute Units that allow comparison of compute power between
    instance types.
  * **vCPUs** - Number of virtual CPUs assigned to the instance type.
  * **Physical Processor** - Host processor family (e.g. Intel, Graviton2).
  * **Clock Speed** - Clock speed of the host server.
  * **Memory** - The amount of RAM assigned to the instance type.
  * **Instance Storage** - The amount of ephemeral local storage the instance
    type includes.
  * **EBS-Optimized Available** - Whether or not an instance can be configured
    to use EBS optimized I/O throughput.
  * **Network Performance** - Data transfer rate allowed to instances.
  * **IPv6 Support** - Whether IPv6 is supported.
  * **Intel AES-NI** - Availability of the Advanced Encryption Standard - New 
    Instructions (AES-NI).
  * **Intel AVS** - Whether the hardware supports a floating-point intensive
    instruction set.
  * **Intel Turbo** - Whether the hardware supports short term performance
    boosts.
* Auto scaling
  * Scaling out (horizontally) can be used to improve performance if a single
    instance type is not enough.
  * Particularly useful for web applications.
* Serverless Workloads
  * Container tools like docker or code-only functions like Lambda.
  * Can provide "instant on" compute with less overhead.
  * Tools like Elastic Container Service (ECS) or AWS Fargate can help maximize
    resource utilization.

#### Common Use Cases

* **EC2 Instances** - Long-lived and complex applications that require in-depth 
  monitoring and tracking.
* **ECS Containers** - Highly scalable and automated applications that still 
  require control of the underlying resources. Often used for microservice
  deployments.
* **Lambda Functions** - Data retrieval, transaction processing, and 
  stream parsing.

### Storage

* RAID-Optimized EBS Volumes
  * Redundant Array of Independent Disks (RAID)
  * Can be applied to EBS volumes, but must be done at the OS level.
  * Levels
    * *RAID 0* - Striping, spreads data across more than one drive and can 
      greatly speed up I/O performance. Does not add durability.
    * *RAID 1* - Mirroring, duplicates data to additional drives which increases
      reliability, but not performance. Not recommended for use on AWS due to 
      increase in EC2-to-EBS bandwidth. 
    * *RAID 5 & 6* - Combine both performance and reliability features. 
      Increased IOPS considerations make this not recommended for AWS. 
  * AWS does not recommend using RAID configured volumes as a boot volume.
* S3 Cross-Region Replication
  * S3 is a global service, but buckets exist within a specific region.
  * Cross-Region Replication lets you automatically sync (asynchronously) data
    to a bucket in a second region.
  * Destination bucket can be in a different region and even in a different AWS
    account. 
* S3 Transfer Acceleration
  * Routes transfers between S3 and the local PC through CloudFront edge 
    locations to increase speed.
  * Adds an additional charge per-gigabyte transferred.
  * AWS has a speed comparison tool that will let you test to see your potential
    improvement between S3 Direct and S3 Transfer Acceleration.
* CloudFront and S3 Origins
  * S3 is an good platform for hosting a wide range of files and resources.
  * You can create a CloudFront distribution that uses an S3 bucket containing
    files rather than creating a load balancer in front of EC2 instances.
* Databases
  * *Consistency, Availability, and Partition Tolerance (CAP) - How to balance
    consistency, availability, and reliability concurrently in a distributed
    system.
  * *Latency* - Appropriate storage volume type and IOPS class.
  * *Durability* - How data will be protected from hardware failures.
  * *Scalability* - How does the system allow for automated resource growth.
  * *Non-Database Hosting* - Sometimes a non-database solution like S3
    might be more appropriate for your use case.

## Network Optimization

* Geolocation and latency-based routing from Route 53 and CloudFront.
* High-bandwidth EC2 instance types.
* Load Balancing using Elastic Load Balancing (ELB)
  * **Application Load Balancer** - For HTTP and HTTPS web traffic and operates 
    at the application layer (OSI Layer 7) and permit path-based routing.
  * **Network Load Balancer** - For generic TCP traffic and operates ad the 
    transport layer (OSI Layer 4). Network load balancers are built for 
    high-volumes and tightly integrate with Auto Scaling, ECS, and Cloud 
    Formation. NLBs also work for non HTTP/HTTPS TCP traffic. 
  * **Gateway Load Balancer** - For managing third-party virtual appliances 
    supporting the GENEVE protocol. Operates on the network layer (OSI Layer 3).
  * 