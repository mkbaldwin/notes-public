# Compute

## EC2

 * AMIs - Amazon Machine Images
    * Amazon Quick Start AMIs - Amazon maintained AMIs for common OS choices (Linux, Windows, etc.). Up-to-date and officially supported.
    * AWS Marketplace AMI - Third-party images that are official releases from vendors.
    * Community AMI - Maintained by indepdendent vendors / organizations.
    * Private AMI - Images you create and maintain for your organization.
    * Note: Some AMIs may have additional fees for licensing.
 * Instance Types 
    * General Purpose - Balance of compute, memory, and network resources
    * Compute Optimized - Optimized for high-end web servers or machine learning.
    * Memory Optimized - Intensive data analysis and caching. Can have as much as 3.9TB of RAM.
    * Accelerated Computing - Include access to GPU resources (such as those from NVDIA) and are used for demanding high-performance workloads where GPU acceleration is needed.
    * Storage Optimized - For heavily data intensive applications. Can deliver fast read/writes and low latency access to storage. 
    * Some instance types are burstable (e.g T2) this means you can accumulate credits as you run that allow you to temporarily use more resources when needed.
    * Available instance types change freuently as AWS leverages new technologies.
 * Tenancy
    * Shared Instance - This is the default option and is a VM that shares physical resources with other AWS customers.
    * Dedicated Instance - Instance runs on dedicated physical hardware. This can be useful for certain regulatory or licensing situations. These instances cost more than shared instances. 
 * Placement Groups
    * AWS by default tries to spread your instances across their infrastructure. This is good for most cases, but you can use placement groups to control this behavior if needed.
    * Cluster Groups - Launches instances in a single availability zone and attempts to start them physically close to each other for lower latency.
    * Spread Groups - Launches instances across distinct hardware racks and availability zones. This is done to reduce risk of failure.
    * Partition Groups - Lets you define "partitions" to keep some instances close to either other but physically separate from instances in other paritions. 
 * Resource Tags
    * Key-value pairs you can assign to resources to add additional metadata. This is useful as you have a larger number of resources (that may be dynamic) in AWS.
    