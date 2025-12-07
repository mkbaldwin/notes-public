# Implementing Zero Trust in GovCloud

*Notes are a bit incomplete because this was a "chalk talk" with whiteboarding diagrams and such.*

 * What is zero trust?
   * A security model focused on providing security controls that are not dependent on the network.
   * This is not a product, but a set of patterns. Varies depending on the use-case.
 * Stay grounded with the approach
   * Avoid binary choices
   * Work backward from your use cases to understand how to add zero trust
   * Not one size fits all
 * Key AWS Services
   * AWS Verified Access
     * Provide secure access to corporate applications without a VPN
     * Browser extension (can check if device is managed or not, security status of device)
     * HTTP, but also supports other stuff like RDP, databases, ssh, etc.
     * Non HTTP runs as an agent on the machine
   * AWS Verified Permissions
     * Scalable permissions management and fine grained authorization for your application
     * Permission rules engine
   * AWS App Stream
     * Virtualized application in the cloud (not indeneded to be full desktop)
   * AWS Workspaces
     * VDI
 * Use cases for AWS GovCloud
   * User
   * Network
   * App
     * 
   * Database
     * S3, RDS, etc.
     * S3
       * Can do tag based access controls
       * Limited number of tags per session (50)
       * S3 Interface Endpoint
         * Let's you write really granular policies
         * Driven by AWS PrivateLink
 
 
 * AWS Systems Manager
   * No inbound connections required into your EC2.
   * Agent on instance (built into all AWS provided AMIs) polls the systems manager to see if it needs a connection. 
   * Can logs all the buckets