# Introduction to Security and Architecture on AWS

## AWS Architecture Core Concepts

  * Acceptable use policy
    * No unsolicited mass emails
    * No viruses, malware, harmful content
    * Penetration tests allowed for specific services
  * Least privilege access
    * Only grant the minimum permissions to user accounts that are required to do the job they need to do
  * Shared responsibility model
    * Shared responsibility for security & compliance between AWS and AWS user
    * AWS responsible for running core systems and cloud platform
    * Customer responsible for what's running on the cloud

| AWS Responsible for              | Customer Responsible for                              |
| -------------------------------- | ----------------------------------------------------- |
| AWS Employee training / access   | Individual access to cloud resources                  |
| Global data centers and network  | Data security and encryption (in transit and at rest) |
| Physical hardware                | OS / Network / Firewall config                        |
| Infrastructure config management | All code deployed                                     |
| Patching cloud infrastructure    | Patching guest OS / apps                              |

### AWS Well Architected Framework

* Collection of best practices
* 5 core pillars
  * Operational Excellence
  * Security
  * Reliability
  * Performance Efficiency
  * Cost Optimization

### High-availability & Fault Tolerance

  * Everything fails all the time - CTO Amazon
  * Reliability on AWS
    * Fault tolerance
      * Being able to handle failure of app components
    * High Availability
      * Keep entire solution even if problems occur
      * Powered by most AWS services out of the box
    * Solutions on EC2 must be deployed to be fault-tolerant
    * Should leverage more than one AZ
    * Some services can help
      * SQS (Simple Queue Service)
      * Route 53

### Compliance

  * Common Standards
    * PCI-DSS
    * Credit Card
    * HIPPA
    * SOC1, SOC2, SOC3
    * FedRAMP
    * ISO27018 - PII Related
  * Services
    * AWS Config
      * Conformance pack
    * AWS Artifact
    * AWS Guard Duty

## Identities & User Management

### AWS IAM

  * Free Service
  * Service controlling access to AWS services
  * Authentication and authorization management
  * Supports identity federation (SAML)
  * IAM Identities
    * Users  - Individual access to resources
    * Groups - Manage permissions for multiple users
    * Role   - Allow user or service to assume permission for task. Can be used to allow your app to use AWS resources
  * Policies
    * Define permissions for AWS identity / principal
    * Defines services & permissions
    * Custom or AWS managed
  * Best Practices
    * Least Privilege
    * Multi-Factor Authentication
  * MFA Options
    * Virtual (authenticator app)
    * U2F Security Key
    * Hardware Token (gemalto)

### Amazon Cognito

  * Service that enables you to handle authentication / authorization for your app
  * Fully managed user directory service
  * UI components for many platforms
  * Advanced security controls
  * Enables controlled access to AWS resources
    * e.g. allowing end user to have access to private files in S3 bucket
  * Works with Social & Enterprise IDPs
    * Google
    * Facebook
    * AD
    * SAML

## Data Architecture on AWS

### Integrating On-Premise Data

#### AWS Storage Gateway

  * VM or hardware appliance on your network
  * Works with S3 & EBS
  * Three types
    * Tape Gateway
      * Enables tape backup process to store on cloud in virtual tapes
      * Virtual tape library
    * Volume Gateway
      * Local iSCSI volumes that are stored in cloud
    * File Gateway
      * Store file in S3 and keep local copy on your network

#### AWS Data Sync

  * Agent deployed as VM or your network
  * Works with S3, EFS, FSx
  * Greatly improved transfer speed

### Processing Data

#### AWS Glue

  * Managed extract, transform, and load (ETL) service
  * Supports RDS, DynamoDB, RedShift, S3
  * Serverless model

#### Amazon EMR

  * Elastic map reduce 
  * Supports popular open source tools
  * Operates in clustered environment w/o additional configuration
  * Many big data use cases
  * Frameworks included
    * Apache Spark
    * Apache Flink
    * Apache Hive
    * Apache HBase
    * Apache Hudi
    * Presto

#### AWS Data Pipeline

  * AWS Data Pipeline
    * Managed ETL Service
    * Supports: S3, EMR, RedShift, RDS, DynamoDB
    * Data Workflows
    * Can work w/on-prem data source

### Analyzing Data

#### Amazon Athena

  * Fully Managed
  * Query large scale data in S3
  * Write in standard SQL
  * Charged based on data scanned per query

#### Amazon Quick Sight

  * Fully managed business intelligence service
  * Dynamic data dashboards
  * Per user or per session pricing model
  * Multiple versions

#### Amazon Cloud Search

  * Fully managed search service
  * Per hour / instance charge
  * Enables developers to build search into your app

### Integrating AI & Machine Learning

#### Amazon Rekognition

  * Computer vision - image/video
  * Identify objects in images
  * Identify actions in video
  * Facial Analysis
  * Custom labels for your business objects

#### Amazon Translate

  * 54 Languages supported
  * Language identification  and translation
  * Realtime or batch

#### Amazon Transcribe

  * Speech recognition
  * Special version for medical
  * 31 languages

## Disaster Recovery on AWS

  * Backup & Restore
    * Backup data into S3
    * In a DR event, spin up an entire new environment
    * Longest recovery time
    * Cheapest Cost
  * Pilot Light
    * Key components are kept running in cloud
    * Reduce time over backup & restore
    * Increased Cost
    * Must be maintained
  * Warm Standby 
    * Scaled down version always running
    * Can run on less capable infrastructure
    * Even more cost
  * Multi-site
    * Full environment running all the time
    * Most expensive
    * Near seamless recovery process
  * Choosing an approach
    * Recovery time objective -> Time it takes to get fully back up and running
    * Recovery point objective -> Amount of data loss in terms of time that is acceptable. 

## Architecting on EC2

  * Auto-scaling groups
    * Launch template defines instance config
    * min/max/desired number of instances
    * performs health checks
      * You can customize these
    * Works in one or more AZ within a region
    * On-demand or spot instances

```                                                                                                 
                                  EC2 Auto                                                          
                                Scaling Group                                                       
                                      │                                                             
                                      │                                                             
┌─────────────────────────────────────┼─────────────────────────────────────────┐                   
│ us-east-1                           │                                         │                   
│                                     │                                         │                   
│ ┌───────────────────────────────────┼──────────────────────────────────────┐  │                   
│ │  VPC                              │                                      │  │                   
│ │                                   │                                      │  │                   
│ │   ┌─────────────────────────┐     │        ┌─────────────────────────┐   │  │                   
│ │   │  AZ1                    │     ▼        │  AZ2                    │   │  │                   
│ │   │ ┌───────────────────────┴──────────────┴─────────────────┐       │   │  │                   
│ │   │ │     ┌───┐                                    ┌───┐     │       │   │  │                   
│ │   │ │     │   │                                    │   │     │       │   │  │                   
│ │   │ │     └───┘                                    └───┘     │       │   │  │                   
│ │   │ └───────▲───────────────┬──────────────┬─────────▲───────┘       │   │  │                   
│ │   │         │               │              │         │               │   │  │                   
│ │   │ ┌───────┼───────────────┴──────────────┴─────────┼───────┐       │   │  │                   
│ │   │ │       │                   ┌───┐                │       │       │   │  │       Application 
│ │   │ │       └───────────────────│   │────────────────┘       │ ◀─────┼───┼──┼──────Load Balancer
│ │   │ │                           └─▲─┘                        │       │   │  │                   
│ │   │ └───────────────────────┬─────┼────────┬─────────────────┘       │   │  │                   
│ │   │                         │     │        │                         │   │  │                   
│ │   │                         │     │        │                         │   │  │                   
│ │   │                         │     │        │                         │   │  │                   
│ │   │                         │     │        │                         │   │  │                   
│ │   └─────────────────────────┘     │        └─────────────────────────┘   │  │                   
│ │                                 ┌─┴─┐                                    │  │                   
│ └─────────────────────────────────┤   ├────────────────────────────────────┘  │                   
│                         ┌────────▶└─▲─┘                                       │                   
└─────────────────────────┼───────────┼─────────────────────────────────────────┘                   
                          │           │                                                             
        Internet          │           │                                                             
         Gateway ─────────┘           │                                                             
                                 US Traffic                                                         
```       

  * AWS Secrets Manager
    * Securely manage passwords, certs, etc.
    * Works natively with RDS, DocumentDB, RedShift
      * Can automatically rotate credentials
    * Fine-grained access control
  * Controlling access
    * Security Groups
      * Firewall for EC2 instance 
      * Works at instance level
      * VPC has default security group
      * Outbound traffic allowed by default
  * Network ACL
    * Works at subnet level
    * Default VPC allows all inbound/outbound
    * Custom ACL by default denies all traffic
  * AWS VPN
    * Creates encrypted site-to-site VPN tunnel
    * Client VPN
  * AWS Shield
    * DDoS Protection
    * Ongoing Detection & Prevention
    * Two service levels
  * Amazon Macie
    * Machine learning to analyze data stored in S3
    * Enables dashboard / alerts about data access
  * Amazon Inspector
    * Scanning of EC2 instances
    * Charged per instance per scan
    * Host assessment & network reachability inspection
  * Deploying Predefined Solutions
    * AWS Service Catalog
    * Organizational Service Catalog
  * AWS Market Place
    * Catalog of third-party solutions
    * AMIs, cloud formation, etc.
    * May have extra charge on top of AWS resources
  * Developer Tools
    * AWS Code Commit
      * Managed GIT repositories on AWS
      * Alternative to GitHub
      * Integrates with IAM
    * AWS Code Build
      * Managed service for deploying your custom apps
      * Deploy to EC2, far gate, lambda, on-prem
    * AWS Code Pipeline
      * Fully managed continuous delivery pipeline
      * Automate Build, Deploy, Test
    * AWS Code Star
      * Workflow tool to automate the use of other developer services
      * Only charged for other services used

## The Certification Exam

  * Cloud Concepts - 26%
  * Technology (AWS Services/Infrastructure) - 33%
  * Security - 25%
  * Billing / Pricing - 16%