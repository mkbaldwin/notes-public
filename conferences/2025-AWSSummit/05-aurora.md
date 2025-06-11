# Amazon Aurora

* Aurora read only nodes
  * Can have up to 15
  * Can be a mix of architectures and serverless
* Can grow up to 128TB, and automatically managed
* If R/W node goes down CNAME is updated to the new node
* JDBC and other wrappers are available that helps manage fail-overs. 
* Local write forwarding
* Global databases
  * Allows global cluster / failover between multiple regions
  * Replication is fairly fast across regions because they copy blocks
  * Initial replication might take a while depending on the size of the DB
  * Can also do local write forwarding
  * Global database/global endpoint
    * There are URIs for each region
    * Global endpoint points to either
    * Can do planned switchovers
* Storage internals
  * Storage deamon that takes log entries (from queue) and commits to "hot log"
    * Queue is not durable.
    * At this point it is written to disk and can be guaranteed
  * Update queue reads the hot log and then writes into the data blocks
  * Alsows continuously backing things up to S3 for point in time recovery / snapshots
  * IO Optimized
    * Storage deamon will bactch IO for heavy workloads (grouping small commits into one operation)
    * Incoming queue is now a durable queue
    * Some customers see up to 40% cost savings with using IO OPtimized
    * Pay Compute and Storage
      * Slightly higher compute cost
    * If you have a high IO app it might save money
  * Standard IO
    * Pay compute, storage, and IO
* PostgresSQL updates
  * Support for Postgres 16
  * r7i & r8g support
  * pgvector extension for Generative AI
  * Postgres seems to be the most used, most people moving from Oracle go to PG
  * Survey of the room showed most people using PG
* Aurora Serverless
  * Automatically scales in place
    * Resources (CPU/Mem) are added in under a second
    * Billed by hour
  * Default memory allocation 75% for buffer and 25% for heap
  * Buffer pool scales with capacity
  * Automatically scaled down through a combination of least frequently used (LFU) and least recently used (LRU) algorithms
  * Now supports scale to zero
    * After timeout of 5 minutes resources are scaled down to zero
    * Buffer also goes to zero
    * There is a brief performance impact for the first connection to and spin things up again 
* Can use an HTTP data API
* Optimized reads
  * Normally if you run out of memory you have to spill to disk
  * New NVMe storage category for this storage
  * db.r6gd
  * db.r6id
* Manageability - Patching
  * Zero downtime patching
    * Take a pause point in the service and hold the connections
    * Save session state
    * Do upgrade
    * Then restore session state and connection
    * Minor patch takes a few seconds [an example was shown of only 3 seconds]
  *  Blue / Green Deployments
     *  Blue - Prod
     *  Green - Testing / Staging
     *  Managed blue/green deploymments
     *  Creates an identical cluster (with green in the cluster name) then upgrades the DB version
     *  Good for major / minor updates
     *  Schema changes
     *  Other maintenance
     *  Data is automatically replicated
     *  Cluster will be available an you can initiate a switchover
     *  Stop point to allow transactions to finish on blue before switching to green
     *  Cluster names are changed 
     *  You can delete the old cluster when ready
*  zero-ETL Integration
   *  Works with Redshift
   *  Move data between Aurora and Redshift 
   *  5-10 sec replication lag
   *  Can run analytics on redshift while ingesting data
   *  CDC - Change Data Capture
   *  