# DNS and Routing

## DNS

* Responsible for translating human readable domain names into IP addresses. 
* A nameserver is responsible for performing this translation.
* If a query isn't satified by your local nameserver it will be pointed to other name servers specified in the computers configuration.
* Domain Name Components
  * Top-level Domain (TLD) - Values like .com, .net, .edu
  * Second-level Domain (SLD) - First part to the left of the TLD (e.g. amazon from amazon.com)
  * Subdomain - Additional name added to the left of the SLD
* Fully Qualified Domain Name (FQDN) - contains a full DNS path for a domain

### Zones

* A dns zone (or hosted zone) defines a DNS domain.
* A zone file is a text file describing the way resources in the zone should be mapped.
* Resource records inside a zone file consist of the follwing fields:
  * Name - Domain or subdomain being defined
  * TTL - Time to live before record expires
  * Record Class - Namespece for the record (usually IN for Internet)
  * Record Type - The record type being defined (e.g. A, CNAME)

#### Record Types

* There are currently around 40 DNS record types, but only the most common ones are offered by Route 53.
  
| Record Type | Function |
|-------------|----------|
| A | Map a hostname to an IPv4 address. |
| CNAME | Canonical name - define a hostname as an alias for another. |
| MX | Mail Exchange - used to define mail transfer servers. |
| AAAA | Map a hostname to an IPv6 address. |
| TXT | Human or machine readable text. |
| PTR | Pointer - poiints to another location within the domain space. |
| SRV | Record for service location. |
| SPF | Sender Policy Framework - Email validation protocol (nolonger widely used) |
| NAPTR | Name authority pointer |
| CAA | Certificate Authority Authorization - Establishes a Certificate Authority authorized to issue certificates for a domain. |
| NS | Identify the name server to use for the zone. |
| SOA | Start of authority - define authoratitive metadata for a zone. |

* Route 53 also provides alias records that allow you to route traffic to an AWS resource (e.g. load balancer).

## Route 53

* AWS' hosted service for DNS.
* Provides
  * Domain registration
  * DNS management
  * Availibility monitoring
  * Traffic management policies
* Domain Registration - Can be used as an alternative to other registrars.
* DNS Management
  * Core feature of Route 53.
  * Allows you to configure your zones through the AWS console or CLI.
  * Can host public or private zones. A private zone is only accessible within your AWS VPC.
* Availability Monitoring
  * Route 53 can be configured to monitor the availability of your resources and route to an alternative resource if the health checks are failing.
* Routing policies
  * Can be used to route traffic to different resources
  * Weighted Routing - Route to resoures based on a ratio you set. 
  * Latency-based Routing - Route to resources in different AWS regions based on the one with the lowest latency.
  * Failover Routing - Identify a resource as the primary and if the primary is unavailable route to a defined secondary resource.
  * Geolocation Routing - Route traffic to the closest available region for the client making the request. Sometimes geolocation can fail and you must define a default.
  * Multivalue Answer Routing - 
  * Traffic Flow - Tool to help visualize complex combinations of routing policies.
  
# AWS CloudFront

* A global content delivery network (CDN)
* Network of physical edge location placed physically close to end users.
* Route 53 can be used to send users to CloudFront for appropriate routing.
* Allowed CloudFront origins
  * Amazon S3 Bucket
  * AWS MediaPackage channel endpoint
  * AWS MediaStore container endpoint
  * Application Load Balancer
  * Lambda Function URL
  * Custom origin (e.g. on-premise HTTP server)
* 