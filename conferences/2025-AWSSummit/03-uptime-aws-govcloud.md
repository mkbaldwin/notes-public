# Architect to Maximize uptime and resiliency in AWS GovCloud

 * What is resilience from Amazon's perspective?
   * Ability to resist or recover from disruptions
   * Reliability - the ability of a wokload to perform its function
   * Reslilience - ability to recover from issues
   * high availability != disaster recovery
     * disaster recovery targets rare, but high-impact failures
     * high availability deals with more routine issues
 * Recovery point objective (RPO)
   * How far back can we go and recover data
   * How much data can you afford to recreate or lose?
 * Recovery time objective (RTO)
   * How quickly must you recover?
 * Strategies
   * Backup and restore
     * RTO: Hours
     * Cost: $
   * Pilot light
     * RTO: 10s of minutes
     * Cost: $$
     * Services idle
     * Data live
     * Provision additional resources and scale when event occurs
   * Warm standby
     * RTO: Minutes
     * Cost: $$$
     * Business critical
     * Always running, but smaller
   * Multi-site active/active
     * RTO: Real time
     * Cost: $$$$
     * Mission critical 
     * Near zero data loss
 * How do you architect for resilience?
 * What services should I use?


Left session early