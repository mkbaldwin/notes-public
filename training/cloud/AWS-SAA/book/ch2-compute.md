# Compute

## EC2

 * AMIs - Amazon Machine Images
    * Amazon Quick Start AMIs - Amazon maintained AMIs for common OS choices (Linux, Windows, etc.). Up-to-date and officially supported.
    * AWS Marketplace AMI - Third-party images that are official releases from vendors.
    * Community AMI - Maintained by independent vendors / organizations.
    * Private AMI - Images you create and maintain for your organization.
    * Note: Some AMIs may have additional fees for licensing.
 * Instance Types 
    * General Purpose - Balance of compute, memory, and network resources
    * Compute Optimized - Optimized for high-end web servers or machine learning.
    * Memory Optimized - Intensive data analysis and caching. Can have as much as 3.9TB of RAM.
    * Accelerated Computing - Include access to GPU resources (such as those from NVDIA) and is used for demanding high-performance workloads where GPU acceleration is needed.
    * Storage Optimized - For heavily data intensive applications. Can deliver fast read/writes and low latency access to storage. 
    * Some instance types are burstable (e.g T2) this means you can accumulate credits as you run that allow you to temporarily use more resources when needed.
    * Available instance types change frequently as AWS leverages new technologies.
 * Tenancy
    * Shared Instance - This is the default option and is a VM that shares physical resources with other AWS customers.
    * Dedicated Instance - Instance runs on dedicated physical hardware. This can be useful for certain regulatory or licensing situations. These instances cost more than shared instances. 
 * Placement Groups
    * AWS by default tries to spread your instances across their infrastructure. This is good for most cases, but you can use placement groups to control this behavior if needed.
    * Cluster Groups - Launches instances in a single availability zone and attempts to start them physically close to each other for lower latency.
    * Spread Groups - Launches instances across distinct hardware racks and availability zones. This is done to reduce the risk of failure.
    * Partition Groups - Lets you define "partitions" to keep some instances close to either other but physically separate from instances in other partitions. 
 * Resource Tags
    * Key-value pairs you can assign to resources to add additional metadata. This is useful as you have a larger number of resources (that may be dynamic) in AWS.
 * Storage
   * EBS Provisioned IOPS
      * For high IO applications
   * EBS General Purpose SSD
      * Useful for most workloads.
   * HDD Volumes
      * Slower access speeds
      * Cheaper prices
   * All EBS volumes can be copied by creating snapshots that can be used to create other volumes
   * Can be encrypted
   * Instance Store Volumes
      * Ephemeral storage that resets when the instance is shutdown.
      * Availability depends on the instance type selected.
 * Networking
   * All instances get at least once private IP address 
   * Private Address Ranges
      | Class | CIDR Block | Address Range |
      | ----- | ---------- | ------------- | 
      | Class A | 10.0.0.0/8 | 10.0.0.0 to 10.255.255.255 | 
      | Class B | 172.16.0.0/12 | 172.16.0.0 to 172.31.255.255 | 
      | Class C | 192.168.0.0/16 | 192.168.0.0 to 192.168.255.255 |
   * Additional public or private addresses can be added.

### Instance Security

 * Security Groups
   * A security group works like a firewall and by default blocks all incoming traffic and allows all outgoing traffic.
   * Traffic is checked for source/destination address, port, and the protocol configured.
 * IAM Roles
   * Allows for controlling access to resources, like EC2 instances. 
   * Give resources or users access to use your instance.
   * Give your EC2 instance permission to use other resources (e.g., RDS DB).
 * NAT Devices
   * Provide access to the internet without the EC2 being accessible from the internet. 
   * NAT Instance
   * NAT Gateway - Managed Service that doesn't require you to maintain an instance. 

### Auto Scaling

 * Launch configurations define the parameters needed for launching an EC2 instance
 * Launch templates are similar to launch configurations, but are more flexible and can be used to launch one-off instances.
 * Auto scaling groups
   * A set of EC2 instances managed by auto scaling
   * Group can be configured to use a load balancer to direct traffic to the instances in the group.
   * Health checks can be defined to monitor the application instance to determine if it is still usable.
   * Scaling Policies
      * Minimum - ensure the number of healthy instances never goes below a specific value.
      * Maximum - ensures the number of healthy instances never goes above a specific value.
      * Desired Capacity - Optional setting that must be between the minimum and maximum values that is a desired capacity. Otherwise, the auto scaling group starts with the minimum size.

TODO: Take notes on the more advanced scaling policies

### AWS Systems Manager

TODO

## Elastic Container Service (ECS)

 * Quickly launch clusters of hundreds or thousands of containers.
 * Define the container images, environment resources, and configuration your application needs.
 * Amazon ECS Anywhere - extends ECS to your own on-premise hardware using the same APIs. 

## Elastic Kubernetes Service (EKS)

* Fully managed kubernetes (k8s) container orchestration service.

## Other container services

  * Elastic Container Registry (ECR) - managed docker container registry for storing container images