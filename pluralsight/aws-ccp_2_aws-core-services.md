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
    * Superior fault tolerence than DNS resolution
  * Use Cases
    * Non HTTP protocol (UDP, VOIP, MQQT)
    * Need for static IP
    * Instant failover

## File Storage Services

## Database Services