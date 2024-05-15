# Route 53

  * DNS 101
    * Domain Name System - convert domain names to IPv4 or IPv6 address
    * SOA Record
      * Start of Authority Record
      * Name of server supplying data for the zone
      * Administrator of the zone
      * Version of the data file
      * Default TTL for resource records
    * NS Record
      * Name Server Record
      * Used by TLD servers to direct traffic to the content DNS server containing authoratative DNS records.
    * A Record
      * Address records
      * Translate name to IP address
    * TTL - Length that a DNS record is cached on a server or client (in seconds)
    * CName
      * Canonical Name
      * Resolve one name to another
    * Alias
      * Used to map resource records in your hosted zone to ELB, S3, etc.
      * Similar CNAME, but can be used for naked domain names
    * Routing Policies
      * Simple Routing
        * One record with multiple IP addresses.
        * All values returned to user in random order.
      * Weighted Routing
        * Allows you to split traffic based on assigned weights.
        * Health Checks
          * Define on individual records
          * If a record fails it is removed until it is healthy again
          * Can notify of failures via SNS
      * Latency-based Routing
        * Routing based on latency to give the user the route with the lowest latency.
      * Failover Routing
        * Used to create an active/passive setup
        * Monitors the health of the primary endpoint, if failure then uses the alternate site
      * Geolocation Routing
        * Lets you define where to route traffic based on the location of the user (i.e. where the DNS query comes from)
      * Geoproximity Routing
        * Traffic Flow Only
        * Allows Route 53 route traffic based on location of users and resources.
        * Bias increases or decrease the size of the geographic regions
      * Multivalue Answer Policy
        * Lets you configure multiple values (IP addresses)
        * Also lets you check the health of each resource so Route 53 only returns healthy records
        * The same as simple routing, but with health checks
    * Exam Tips
      * Elastic Load Balancers do not have pre-defined IPv4 addresses, you resolve them with DNS names
      * Understand difference in CNAME and ALIAS
      * 