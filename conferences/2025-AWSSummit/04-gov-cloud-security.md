# Elevate AWS GovCloud with new security and naming capabilities

## Amazon Route 53

* Fast
* Cost effective
* Secure
* Highly available
* Region independent 
* Public vs private DNS
  * public hosted zones
    * Route to internet facing resources
    * Global routing policies
    * DNSSEC
    * Won't reside in GovCloud, but instead is in a commercial account
  * private hosted zones
    * internal domain resolution
 * Challenges with the public DNS being in a commerical account
   * Number or public routes
   * Complexity
   * Compliance
   * Central control and visibility
 * New feature: Public hosted zone capability inside of GovCloud. 
   * All of the usual Route 53 DNS features are available. 
   * Benefits
     * Streamlines compliance controls
 * What problems does DNSSEC solve?
   * Compliance
   * You want to authenticate DNS when connecting to web services
   * You want your clients to authenticate DNS connecting to your services
   * NOT for privacy or encyption
   * Route 53 makes this easy
     * Signing is automatic
     * Key management is automatic

# DDoS Protection

* AWS Shield Standard Mitigations
  * Baked into the AWS infrastructure and enabled automatically.
  * Stops traffic pretending to be AWS traffic and keeping it from getting into the AWS network
  * Rate limiting for DDoS signatures
  * Route 50 packet suspicion management
    * requests are filtered into buckets based on suspicion score 
    * Requests will be services but priority will be given to less suspicious items
  * Abuse isolation 
    * Attacks coming from inside AWS infrastructure
    * Customer server has been compromised 
    * Automatically isolate access to/from those resources (other than ssh access in)
  * Botnet disruption
    * If shield detects a bot it will isolate the system to keep the bot from talking home or to other services.
    * The shield team can then track down the command and control server and shut it down if on AWS or block.
  * Proxy-based L7 DDoS attacks
    * Deployed honeypots that look like proxy servers
    * Try to catch the source of attacks and work with the ISPs and hosting proviers to take them down
*  AWS WAF migrations
   *  Provides Layer 7 protection
   *  Add on product
   *  You inline this with other services being used. e.g.:
      *  Elastic Load Balancer
      *  API Gateway
      *  Cognito
      *  Verified Access
   *  Only adds single digit millisecond additional latency
   *  WAF does require user configuration. 
   *  Provides web ACLs
   *  AWS does provide managed rules (you only have the option to enable or disable).
   *  Only one rule in GovCloud that has an additional cost. 
   *  Options for response to a rule:
      *  Allow
      *  Block
      *  Count
      *  Captcha
      *  Challenge
   *  Rate based rules - rate limiting with thresholds. 
   *  Geo blocking (block an entire country e.g. Russia, NK)
   * Option to label the request and then use that label in another rule. 


*Thought: How does this compare to what Akamai Provides?*