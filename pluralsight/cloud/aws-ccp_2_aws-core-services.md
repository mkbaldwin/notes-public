# Understanding AWS Core Services

## Interacting with AWS

  * Interacting with AWS Services
    * Web Console
    * CLI
    * SDK
  * Web Console
    * basic interface for most of the 150+ AWS services
    * Console is great for testing things out
  * CLI
    * Available for windows, mac, linux
  * SDK
    * Allows for scripting our interactions
    * Allows automation of tasks from custom applications
    * Java
    * Node
    * Python
    * Go
    * etc.
  * CLI/SDK - Great for automating repeated tasks
  * Most services can be performed from any of these
  * AWSRoot user is the one used to create the account

## Compute Services

### EC2
  * Use Cases:
    * Web App Hosting
    * Batch Processing
    * API Server
    * Desktop in the cloud
  * Core concepts
    * Instance type
      * Defines processor, memory, storage
      * Cannot be changed without downtime
      * Categories:
        * General Purpose
        * Compute, memory or storage optimized
        * Accelerated computing
  * Root device types
    * Instance Store - Ephemerl storage physically attached to the host the server is running on
    * Elastic Block Store
      * Persistent block store that is separate from the EC2 instance
      * Most commonly used of the two
  * Amason Machine Images (AMI)
    * Template for an EC2 instance including config, OS, data
    * AWS provides many
    * Can be shared across accounts / can make custom ones
  * Purchase Options
    * On-demand - Standard / Default
    * Reserved - Discounts if you commit to a fixed amount of time
    * Savings Plan - Supports EC2, FarGate, Lambda. Similar to reserved.
    * Spot - Significant discount. Market price per AZ. If price exceeds your bid then the job is terminated.
    * Dedicated - Most expensive. Good if you have a per server licensing model to adhere to. Some types of compliance models need this.
  * EC2 is basically a VM in the cloud on AWS infrastructure

### Elastic Beanstalk
  * Automates deploying and scaling workloads on EC2 (PaaS)
  * Supports specific technologies
  * Leverages other AWS technologies
    * You only pay for the other services you use (not for elastic beanstalk itself)
  * Handles provisioning, monitoring, etc.
  * Supports: Java, .NET, Node.js, Python, Go, Ruby, Docker, etc.
  * Features
    * Monitoring
    * Deployment
    * Scaling
    * EC2 Customization
    * Deploy an app with minimal knowledge of other services
    * Lower maintenance
    * Less customization

### AWS Lambda
  * Run code without provisioning / managing servers
  * Pay based on execution time and memory
  * Functions as a Service
  * Works out of the box with other services
  * Good for event driven architecture
  * Benefits
    * Low maintenance 
    * Auto scales
    * Fauly Tolerent
    * Pay by usage
    * Serverless architecture

## Content and Network Delivery Services

### Amazon Virtual Private Cloud (VPC)
  * Logically separated part of AWS for you
  * Virtual network you can configure (IPv4, IPv6)
    * IP Ranges
    * Subnets
    * Route Tables
    * Network Gateways
    * Private & Public Subnets
    * Can use NAT
    * Connection to data center
    * Private connection to AWS Services

### AWS Direct Connect
  * Establish connection from AWS directly to your data center

### Amazon Route 53
  * DNS Service
  * Global Service (no region selection)
  * Highly Available
  * Global resource routing - route to closest server
  * DNS changes are not instantaneous - takes time to propagate
  * Route 53 High Availability:
    * Can configure to have failover to route to a different server automatically if a server goes down

### Elastic Load Balancing
  * Distribute traffic across multiple targets
  * Works with EC2, ECS, Lambda
  * Supports one or more AZs in a region
  * Three types of load balancer
    * Application LB (ALB)
    * Network (NLB)
    * Classic
  * Scaling on EC2
    * Vertical Scaling / Scale Up
      * Move to larger instance with more resources
    * Horizontal Scaling / Scale Out
      * Additional Instances to handle load

### Cloud Front
  * Content Delivery Network [CDN]
  * Uses AWS Edge locations
  * Static & Dynamic Content
  * Security Features
    * Shield for DDoS
    * Web Application Firewall (WAF)

### Amazon API Gateway
  * Fully managed API Management Service
  * Directly integrates with multiple AWS services
  * Monitoring & Metrics on API Calls
  * Works with VPC & on-prem

### AWS Global Accelerator
  * Uses IP addresses that route to edge locations
  * Once request reaches an edge location it is routed within AWS network vs internet
  * Can route to many AWS resources
  * Performance Improvements
    * Minimizes the distance from user to initial endpoint
    * Optimized by using AWS network instead of internet
    * Superior fault tolerance than DNS resolution
  * Use Cases
    * Non HTTP protocol (UDP, VOIP, MQQT)
    * Need for static IP
    * Instant failover

## File Storage Services

### Amazon Simple Storage Service (S3)
  * Stores files as objects in buckets
  * Store across multiple AZs
  * Enables URL access for files
  * Rules for data life cycle
  * Non-archival storage classes
    * S3 Standard
    * S3 Intelligent Tiering
      * Automatically moves between frequent & infrequent based on access
    * S3 Standard-IA
      * Infrequent access, same resiliance, multiple AZs
    * S3 OneZone-IA
      * Infrequent access, only in one AZ
  * Lifecycle policies
    * Move to different storage class bsaed on time
    * delete by age
    * Can be vased on version -- S3 supports versioning
  * S3 Transfer Acceleration
    * Speeds up data upload using cloud front end points


### S3 Glacier
  * Archiving of data within S3
  * Need to retain, but don't need to get as fast
  * Configurable Retrieval Time
  * Can put files in directly or via lifecycle rules
  * Two Classes
    * Glacier
      * Minimum storage time of 90 days
      * Retrieval in minutes or hours (different cost)
      * Pay per GB retrieved
      * Storage is 5x cheaper than standard S3
    * Glacier Deep Archive
      * 180 day minimal storage duration
      * Retrieval in hours
      * Pay for retrieval
      * Up to 23x cheaper than standard S3

### Elastic Block Store (EBS)
  * Persistent block storage for EC2
  * Can scale to support petabytes of data & multiple volume types
  * Enables redundancy within AZ
  * Allows for snapshotting
  * Offers Encryption
  * Multiple Volume Types
    * General Purpose SSD
    * Provisioned IOPS SSD
    * Throughput optimized HDD
    * Cold HDD

### Elastic file system (EFS)
  * Fully managed NFS file system
  * Stores over multiple AZs
  * Designed for linux workloads
  * Supports petabyte scale
  * Two storage classes
    * Standard
    * Infrequent Access
  * Use Case Example
    * EC2 instances in two AZs

### Amazon FSx
  * Fully managed windows file system
  * SMB Support
  * NTFS
  * AD Integration
  * SSD for low latency

### Data transfer with Snow Ball
  * Physically move data

| Snow Ball                                          | Snow Mobile                                 |
| -------------------------------------------------- | ------------------------------------------- |
| Petabyte Scale                                     | Exabyte Scale                               |
| Device delivered by AWS, returned by local carrier | Shipping container brought to your location |
| You connect to your network                        | AWS Connects to your network                |
| Loaded into S3                                     | Loaded into S3                              |

## Database Services

### Amazon Relational Database Service (RDS)
  * Managed Service (provisioning, patching, backup/recovery)
  * Supports deployments across multiple AZs
  * Some platforms support read replicas
  * Launch into VPC
  * Two volume types
    * General purpose SSD
    * Provisioned IOPS SSD
  * Supported Platforms
    * MySQL
    * PostgreSQL
    * Oracle
    * MariaDB
    * Amazon Aurora
      * MySQL / PostgreSQL compatible
      * Built for the cloud
  * Amazon Database Migration Service (DMS)
    * One time or continual
    * Supports many commercial and open source DBs


### Amazon Dynamo DB
  * Fully managed
  * No SQL DB
    * Key Value
    * Document DB
  * Extremely low latency
  * Automatic Scaling
  * In memory cache option
  * Can handle more than 10 trillion requests/day. Peak of 20 million reqs/sec
  * Use Cases
    * Scale w/o maintenance
    * Serverless Architecture
    * Need low latency
    * Data model w/o blob storage

### Amazon Elasticache
  * Fully managed in memory data store
  * Memcached
  * Redis
  * Low latency
  * Enable scaling / replicas on demand
  * Handles most use cases
    * DB Cache
    * Session Store

### Amazon Red Shift
  * Scalable Data Warehouse
  * Petabyte Scale
  * High performance disks and column storage
  * Can be encrypted
  * Isolation in VPC
  
## App Integration Services

### Simple Notification Service (SNS)

  * Fully managed pub/sub messaging service
  * Organize info into topics
  * Integrate with other AWS Services
  * Notifications
    * SMS 
    * Email
    * Push
  * If you are not listening when the message is published you will not receive it.

```
                                                 ┌──────────────┐
                                  ┌─────────────▶│    Lambda    │
                                  │              └──────────────┘
                                  │                              
 ┌──────────────┐         ┌──────────────┐       ┌──────────────┐
 │ User Signup  │────────▶│  SNS Topic   │──────▶│  SQS Queue   │
 └──────────────┘         └──────────────┘       └──────────────┘
                                  │                              
                                  │              ┌──────────────┐
                                  └─────────────▶│    Email     │
                                                 └──────────────┘
```

### Simple Queue Service (SQS)

  * Fully managed message queue service
  * Up to 256kb payload
  * Allows messages to be stored up to 14 days
  * Two types of queue
    * Standard - order not guaranteed
    * FIFO - order guaranteed
  * Fan out (send to multiple places at once)
  * Queues help the system be fault tolerent. Service can go down and we don't lose data.

```
                                      ┌───────────┐     ┌─────────────────┐
                                      │ Analytics │     │Analytics Ingest │
                          ┌──────────▶│   Queue   │────▶│Service (lambda) │
                          │           └───────────┘     └─────────────────┘
  ┌───────────┐     ┌───────────┐                                          
  │User Order │────▶│ SNS Topic │                                          
  └───────────┘     └───────────┘                                          
                          │           ┌───────────┐     ┌─────────────────┐
                          │           │Fulfillment│     │Order Fulfillment│
                          └──────────▶│   Queue   │────▶│     Service     │
                                      └───────────┘     └─────────────────┘
```

### AWS Step Functions

  * Orchestration of workflows
  * Fully managed service
  * Serverless Architectures
  * Can support complex workflows and includes error handling
  * Charged per state transition and for other services used
  * Amazon states language
  * Itegrates with many AWS services (compute, messaging, database)

## Management & Governance Services

### AWS CloudTrail

  * Log and monitor interactions across all AWS services
  * Records into S3 bucket
  * Logs in region where the events occur
  * Best Practice: Should be turned on for every AWS account
  * Use Cases
    * Compliance
    * Forensic Analysis
    * Operational Analysis
    * Troubleshooting

### AWS Cloud Watch

  * Metrics, logs, and alarms for infrastructure
  * Monitoring and management service
  * Collects logs (even from your app)
  * Metrics and events from AWS services
  * Alarms based on metrics
  * Dashboards based on metrics

### AWS Config

  * Monitors and records configuration
  * Configuration history for infrastructure
  * Rules you can customize
  * Can work with AWS organizations
  * Remediation steps suggested

### AWS Systems Manager

  * Multiple tools to manage infrastructure
  * Automation for common maintenance actions
  * Secure way to access server using AWS credentials
  * Store app parameters securely for operational use

### AWS Cloud Formation

  * Provision infrastructure based on templates
  * No additional charge
  * YAML or JSON templates
  * Infrastructure as code
  * Manage dependencies between resources
  * Provides drift detection to find changes
  * Allows building infrastructure for prod, test, dev identically

### AWS OpsWorks

  * Managed instances of chef / puppet
  * Configured as code
  * Works in hybrid cloud model
  * Ops works for
    * Chef Automate
    * Puppet Enterprise
  * Ops works stacks

### AWS Organizations & Control Tower

  * Organizations
    * Manage multiple accounts under one master account
    * Consolidated billing
    * Centralized logging & security
  * Control Tower
    * Centralize user access across accounts
    * User management based on templates
    * Guardrails for accounts
    * Dashboards 
