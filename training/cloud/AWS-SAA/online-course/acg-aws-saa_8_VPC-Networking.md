# VPCs & Networking

  * Virtual data center in the cloud
  * Virtual private cloud is a logically isolated part of AWS for your infrastructure.
  * **Internet Gateway** - Connection to public internet
  * **Virtual Private Gateway** - Connection to your corporate network
  * Network ACLs are stateless
  * Security Groups are stateful
  * Default VPC
    * Can immediately deploy instances
    * All subnets have route to internet
  * VPC Peering
    * Connect one VPC to another with direct network route
    * Instances behave as if they are on the same network
    * Can peer within same or different AWS account
    * Peering is not transitive... if A and B are peered and B and C are peered A is still not allowed to talk to B.
  * Subnets cannot be across multiple AZs
  * ACLs - Allow / Deny rules for inbound and outbound
  * Availability zone names are randomized between accounts. So, 1-a may not be the same physical data center 
    when comparing two accounts
  * Direct Connect
    * Dedicated connection between AWS and your network
    * Directly connect your data center to AWS
    * Useful for high throughput workloads as well as security / stability
  * Global Accelerator
    * Accelerators improve availability and performance
    * Includes two IPs, can bring your own
    * Traffic enters one location and then goes over Amazon network
    * Components:
      * Accelerator - Directs traffic to optimal endpoints
      * Static IPs
      * DNS Name
      * Network Zone
      * Listener - Processes inbound connections (TCP/UDP)
      * Endpoint Group - One or more endpoints in a region
      * Endpoint - AWS Service (e.g. EC2, ALB, ect.)
  * VPC Endpoint
    * Interface endpoint - network interface with a private IP that serves as an entrypoint for traffic destined to a supported services
    * Traverse AWS network not internet
    * Gateway Endpoint
      * Certain services supported (S3, DynamoDB, etc)
      * Keeps traffic from your App to AWS service inside AWS network instead of using the public endpoints
    * By default, services such as S3 route out to the public internet from inside your VPC
  * AWS Private Link
    * Opening services between VPCs
      * Open VPC to internet (more to manage, security considerations)
      * VPC Peering
        * Manage many relationships
        * Whole network is accessible
      * Private link
        * Open services between VPCs
        * Best way to expose service VPC
        * Utilizes a network load balancer (on the service VPC) and elastic network interface (on the customer VPC)
  * AWS Transit Gateway
    * Allows transitive peering between 1000s of VPCs
    * Hub and spoke model
    * Regional basis, but can span regions
    * Can use across multiple AWS accounts
    * Use route tables to limit traffic
    * Supports IP multicast
  * AWS VPN (?)
    * Single point to connect VPN infrastructure
    * Hub and Spoke
  * AWS NEtwork Costs
    * Free traffic into VPC
    * App server to DB server (private IP in AZ/VPC) is free
      * Cost $0.01/GB (may vary) between regions / AZs
      * Twice as expensive if public IP over internet
    * Cost $0.02/GB between regions
    * Always use private IPs over public to save costs
    * No network cost for EC2 instances within AWS VPC
