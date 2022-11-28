# AWS Cloud Overview / Review Notes

## Fundamental Concepts

### Benefits of Cloud

  * **Cost Savings** - Trade fixed up front (capital) expenses for variable expenses paying only for what you use.
  * **Agility** - The cloud gives you easy access to a wide range of technologies and lowers the cost of trying new things.
  * **Elasticity** - Scale resources up or down easily based on need / usage.
  * **Reliability** - Ability to provide functionality when needed.

### AWS Global Infrastructure

  * **Region** - A specific geographic location containing a number of data centers working together.
  * **Availability Zone** - A cluster of one or more data centers within an AWS Region.
  * **Edge Locations** - More than 200 global locations used to support CloudFront CDN and Route 53 DNS.  

### Cost Estimation Tools

  * **AWS Cost Explorer** - Interface for exploring your AWS costs broken down by Service and Cost Tag. Provides predictions
                            for the next three months of cost and recommendations for cost optimization. 
  * **AWS Budgets** - Plan and track usage across your AWS services. 
  * **AWS TCO Calculator** - Enables determination of costs for leveraging cloud infrastructure.
  * **AWS Simple Monthly Calculator** - Calculate costs of running specific AWS infrastructure. 

## AWS Cloud Services

### Compute Services
  * **EC2** - Elastic Compute Cloud provides access to on-demand compute resources. EC2 is basically a virtual machine
              running in the cloud on AWS infrastructure.
  * **Elastic Beanstalk** - Automates the deployment and scaling of workloads on EC2 (PaaS). You only pay for other
                            services used and not for elastic beanstalk itself. Works for specific application platforms
                            (Java, .NET, Node, Docker, etc).
  * **AWS Lambda** - Platform for running serverless applications (cloud functions). You pay based on function execution
                     time and memory.

### Content and Network Delivery Services
  * **Amazon Virtual Private Cloud (VPC)** - A VPC is a "container" in which you run all of your services. It is a logically
                                             separated part of AWS for your use and provides virtual networking configurable 
                                             for your application. 
  * **AWS Direct Connect** - Allows for establishing a connection from AWS directly to your data center.
  * **Amazon Route 53** - Global service (no regions) for providing DNS.
  * **Elastic Load Balancing** - Cloud based load balancers to distribute traffic across multiple EC2, ECS, or Lambda
                                 targets. Multiple types of load balancers available: application (ALB), network (NLB),
                                 or classic.
  * **Cloud Front** - Global content delivery network (CDN) utilizing AWS edge locations. Can be used for both static
                      and dynamic content. Includes security features such as DDoS protection and web application firewall (WAF). 
  * **Amazon API Gateway** - Fully managed API service. Integrates with multiple AWS services and provides monitoring 
                             and metrics on API calls.
  * **AWS Global Accelerator** - Routes via AWS global edge locations. Once a request reaches an edge location it is 
                                 routed within AWS network instead of internet. Improves performance and has superior
                                 fault tolerance. 

### File Storage Services
  * **Amazon Simple Storage Service (S3)** - Fully managed file storage service that stores files as objects in buckets.
                                             Storage across multiple AZs with multiple storage classes and lifecycle policies.
  * **Elastic Block Store (EBS)** - Persistent block storage for use on EC2 instances. Allows for redundancy within AZ
                                    and can scale to support petabytes of data.
  * **Elastic File System (EFS)** - Fully managed NFS file system designed for linux workloads. Supports petabyte scale
                                    and storage across multiple AZs.
  * **Amazon FSx** - Fully managed Windows file system with SMB/NTFS support and AD integration.
  * **AWS Snow Ball** - Physical device shipped to your location to move petabyte scale information into S3.
  * **AWS Snow Mobile** - Shipping container brought to your location for moving exabyte scale information into S3.

### Database Services
  * **Amazon Relational Database Service (RDS)** - Fully managed relational database service supporting common database
                                                   engines such as MySQL, PostgreSQL, Oracle, etc.
  * **Amazon Aurora** - MySQL/PostgreSQL compatible database built for the cloud.
  * **Amazon Database Migration Service (DMS)** - Tooling for one time or continual data migration into Amazon RDS from
                                                  many different commercial database systems.
  * **Amazon Dynamo DB** - Fully managed no SQL DB. Support key-value storage or document storage. Has extremely low latency
                           and automatic scaling. Can handle up to 20 millions requests per second.
  * **Amazon ElastiCache** - Fully managed in memory datastore with on demand scaling and replication. Used for caching
                             and session storage. Compatible with redis and memcached. 
  * **Amazon Red Shift** - Data warehouse service supporting high performance and petabyte scale. Uses column oriented storage.

### Integration Services
  * **Simple Notification Service (SNS)** - Publish / subscribe messaging service supporting topics. Supports notifications
                                            via SMS, email, or push.
  * **Simple Queue Service (SQS)** - Message queueing service that supports up to 256k payload. Message can be stored up
                                     to 14 days. Supports standard (order not guaranteed) or FIFO (order guaranteed) queues.
  * **AWS Step Functions** - Serverless tool for orchestration of workflows. Amazon states language (DSL) for defining workflows.

### Management and Governance Services
  * **AWS Cloud Trail** - Logging and monitoring of interactions across all AWS services into S3 buckets. Used for 
                          compliance, forensic analysis, operational analysis, and troubleshooting. 
  * **AWS Cloud Watch** - Logging service for your application and AWS services. Metrics, alarms, and logs for infrastructure. 
  * **AWS Config** - Monitors and records configuration and history of infrastructure. 
  * **AWS Systems Manager** - Set of tools for managing infrastructure. Secure way to access server using AWS credentials.
  * **AWS Cloud Formation** - Automates provisioning of cloud infrastructure by building templates in YAML or JSON. 
  * **AWS OpsWorks** - Managed instances of chef and puppet.
  * **AWS Organizations** - Provides consolidated billing, logging, security, and account management for multiple accounts
                            under a single master account.
  * **AWS Control Tower** - Centralize user access and management across multiple accounts.

### Identity and User Management

* **AWS Identity and Access Management (IAM)** - Service for defining users and controlling access to AWS services. Performs
                                                 authentication and authorization management (including multi-factor authentication).
* **Amazon Cognito** - Manage authentication / authorization for your custom applications and provides a fully managed user 
                       directory service. Enabled controlled access to AWS resources (e.g. S3 bucket) and works with enterprise
                       IdPs (e.g. AD, SAML).

### Data Processing Services
* **AWS Glue** - Serverless extract, transform, and load (ETL) service for RDS, DynamoDB, RedShift, S3. 
* **Amazon EMR** - Elastic map reduce service for big data processing (includes Spark, Flink, Hive, HBase, Hudi, and Presto support).
* **AWS Data Pipeline** - Managed extract, transform, and load (ETL) service with data workflows.
* **Amazon Athena** - Managed service for querying large scale data in S2 using standard SQL style queries.
* **Amazon Quick Sight** - Managed business intelligence service and dynamic dashboards.
* **Amazon Cloud Search** - Managed service that enables developers to build search capabilities into custom applications.
* **Amazon Rekognition** - Computer vision image/video recognition used to identify object, actions, or perform facial recognition. 
* **Amazon Translate** - Text translation service for 54 different languages.
* **Amazon Transcribe** - Speech recognition / transcription for 31 different languages.

### Developer Tools

* **AWS CodeCommit** - Private Git repository hosting on AWS cloud.
* **AWS CodeBuild** - CI tool that compiles code, runs test, and produces deployable software packages. 
* **AWS CodePipeline** - Continuous delivery tool for building build/deployment pipelines. 