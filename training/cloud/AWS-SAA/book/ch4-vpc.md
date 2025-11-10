# Virtual Private Cloud (VPC)

* A VPC is a virtual network that can contain EC2 instances as well as other AWS resources
* Every VPC is logically isolated from all other networks 
* Connections to other VPCs, the internet, and your own network can be set up
* VPC Exists only in one region and you can have multiple VPCs in your account

## CIDR Blocks

* CIDR - Classless Inter-Domain Routing
* Each VPC consists of at least one contiguous range of IP addresses defined as a CIDR block.
* Primary CIDR block must be assigned when creating the VPC
* Represented as an IP Prefix
  * /16 to /28
  * The smaller the prefix the larger the number of IP addresses in the range
  * IPv4 supports /0 to /32.
  * You can use any range (RFC 1918) but it is recommended to use one of:
    * 10.0.0.0./8
    * 172.16.0.0/12
    * 192.168.0.0/16
* You can optionally add secondary blocks after creation.
* Must come from one of the selected RFC 1918 range or a publicly routable range.
* You can also let AWS assign an IPv6 CIDR, but you don't get to select the range.

## Subnets

* Allows you to isolate resources from each other. 
* You can carve out smaller blocks out of your VPC CIDR block.
* The first four IP addresses in the subnet are reserved by AWS. If you did a 172.16.100.0/24 subnet the follwing are reserved:
  * 172.160.100.0
  * 172.160.100.1   - Gateway / Router
  * 172.160.100.2   - Amazon Provided DNS server
  * 172.160.100.3.  - Reserved
  * 172.160.100.255 - Broadcast
* Subnets in a single VPC cannot overlap
* Commonly the subnet's prefix length will be larger than the VPC CIDR to allow for IP addresses in other Availability Zones.

## Availability Zones

* Subnets can only exist in one Availibility Zone.
* Resiliency can be achieved by deploying services in multiple availibility zones
  
## Elastic Network Interface

* An elastic network interface (ENI) is a network resource that allows an instance to communicate with other resources
* First ENI instance is called the primary ENI.
* Each instance must have a primary IP address bound to the primary ENI.
* It is possible to add additional ENIs with additional IP addresses in the same or different subnets. 
* Virtual network insterfaces can also be "enhanced networking" that provides higher performance by allowing direct access to the physical host network device.
* Two ways of accessing:
  * Elastic Network Adapter
    * Speeds up to 100Gbps
    * Supported by most instance types
  * Intel 82599 Virtual Function Interface
    * Speeds up to 10Gbps
    * Only some instance types supported
  * Your host OS must include appropriate drivers (Amazon Linux and Ubuntu) hardware virtual machine AMIs have this enabled by default
  
  ## Internet Gateway & Routing

* Give the ability to obtain a public IP address, connect to the internet and receive requests from the internet. 
* To use the internet gateway you must create a default route that points to the internet gateway as a router
* Control of how traffic moves in and out of your VPC is done using routes stored in route tables
* A route termines where traffic can move and consists of a desination IP prefix and a target resource
* Desitination must be in IPv4 or IPv6 CIDR notation
* The local route is the only mandatory route that exists in every route table
* The default route
  * To enable internet access from your instances you must create the default route
    * Destination: 0.0.0.0/0 (ALL IP Addresses)
    * Target: Your internet gateway
  * The router will route based on the most specific route first (closest match)
  
## Security Groups

* Functions as a firewall
* Define inbound and outbound rules 
* Stateful firewall - e.g. if inbound traffic is allowed outbound replies are intelligently allowed out back to the requestor
* Each VPC contains a default security group you cannot delete
* You don't have to use it, but you can modify the rules to your needs
* Attached to each ENI

## Network Access Control Lists (ACLs)

* Functions as a firewall
* Attached to a subnet
* Only one NACL per subnet
* NACL is stateless and does not use connection tracking to automatically allow reply traffic
* Much like firewall rules on traditional switches or routers
* Each NACL has a rule number and rules are applied in order (from smallest to largest) rule number
* You may want to use both NACL and security group rules to prevent someone from accidentally creating a lax security group rule

## AWS Network Firewall

* Scalable firewall that can protect multiple VPCs and subnets
* Can even work across multiple AWS accounts
* Provides web filtering, intrusion detection/prevention, stateless and stateful packet filtering
* Centralized visibility on all traffic

## Public IPs

* Can be routed over the internet
* Required if you want outside traffic to connect to your resource over the internet
* Elastic IP addresses (EIPs)
  * Type of IP assigned to your IP when you request it.
  * You have exclusive use of the IP until you manually release it
  * You must bind it to a speficic ENI
  * Can be moved between ENIs, but only assigned to one at any given time
  * AWS Global Accelerator
    * If you have resources in multiple regions managing EIPs managing routing can be cumbersome
    * Automatically routes traffic to the fastest (often closest) endpoint
  * Network Address Translation (NAT)
    * When you assign a public IP to an ENI the server still has its internal private IP
    * NAT is used to route traffic from the public IP to the private internal one
    * Occurs automatically at the internet gateway
    * Can also be performed by a:
      * NAT gateway
        * Managed by AWS
        * Automatically scales
        * Can reside in only one subnet that must be public
        * Must create default route to direct internet bound traffic to the gateway
        * Doesn't use an ENI so cannot have security group applied
      * NAT instance
        * EC2 instance using a preconfigured Linux-based AMI
        * Doesn't automatically scale
        * Has an ENI so you must apply a security group
        * Can be used as a jump host (bastion) to access services that do not have public IPs
        * Must create default route to direct internet bound traffic to the NAT instance
        * Not easy to create resiliency
      * These are useful when services need to access the internet (e.g. for updates), but do not need to be publicly accessible.
  
## Other Services

* AWS Private Link
  * Uses private carrier lines to establish direct connections from:
    * AWS datacenters
    * AWS edge locations
    * customer locations
  * Reliable, low-latency
* VPC Peering
  * Allows traffic to flow between VPCs
  * Only allows instance to instance communication 
    * Cannot share thins like NAT devices
* Hybrid cloud networking
  * Tools for making the cloud be an extension of your data center
  * AWS Site-to-Site VPN
    * Configure a Virtual Private Gateway inside of AWS
    * Configure your on-premise router
    * One VPN per VPC
  * AWS Transit Gateway
    * Highly available service that allows connecting multiple VPCs on on premise networks
    * Done dia Direct Connect links or VPNs
    * Route tables are used to control how traffic flows between networks
    * Black hole routes can be used to drop any traffic that matches the rule
  * AWS Direct Connect
    * Uses private link to offer private low-latency access to your resources
    * Bypass the internet completely
    * Dedicated
      * Single physical connection terminating at an AWS direct connect location
      * 1Gbps, 10Gbps, or 100Gbps speed
    * Hosted
      * Supports between 50Mbps and 10Gbps
      * Extends the last mile connection from a direct connect location to your data center or office.
    * Direct Connect Gateway
      * Global resource that provides a single connection point to multiple VPCs in a region
* High performance computing
  * Elastic Fabric Adapter
    * Special type of ENA that supports TCP/IP
    * Allows HPC applications to use Libfabric to bypass host OS TCP/IP stack
    * Increased throughput and latency
    * All instances must be in same subnet
  * ParallelCluster
    * Automatically manage your Linux HPC cluster
    * Creates cluster instances and automatically creates a 15GB shared filesystem for them to use (based on EBS)

