# Amazon RDS

* Relational database service
* Generally used for online transaction processing (OLTP) workloads
* Engines:
  * MySQL/MariaDB
  * MS SQL
  * Oracle
  * PostgreSQL
  * Amazon Aurora (PostgreSQL/MySQL compatibile)
* Get databases up and running in minutes
* Online transaction processing (OLTP)
  * Processes transactions in real time
  * e.g. orders, payments, banking
  * lots of small transactions in real time
* Online Analytics Processing (OLAP)
  * Compiler queries to analyze historical data
  * Using large amounts of data & complex queries
* RDS is not good for OLAP
* Multi AZ
  * Exact copy of DB in another AZ
  * Primary/Standby DB instances
  * Data is replicated
  * Automated failover to secondary DB
  * PostgreSQL, MariaDB/MySQL, MS SQL, Oracle
  * For disaster recovery only
* Read Replica
  * Read only copy of your primary data
  * Useful for reporting, etc.
  * Can be located in same AZ, different AZ, or different region
  * Used to scale read performance
  * Automate backups must be enabled
  * Multiple read replicas (up to 5) are supported
* DB Snapshot
  * Manually initiated
  * Snapshot of storage volume
  * Manual and have no retention perid
  * Restore to a known state
  * Good before significant maintenance / changes
* Automated Backup
  * Enabled by default
  * Runs during backup window
  * Transaction logs used to reply transactions
  * Retention period of 1 - 35 days
  * Point-in-time recovery to any point in the retention period
  * Full daily backup + transaction logs throughout the day
  * Can restore to any point in time from the retention policy
  * Stored in S3
  * Free storage equal to the size of your DB
* Restoring backups / snapshots always creates a new RDS instance with a new DNS endpoint
* Encryption at rest
  * Can be enabled ONLY at the creation of the RDS instance
  * Fully ingegrated with KMS
  * Encrypts all DB storage including: backups, snapchots, and logs
  * Snapshot + restore can be used to encrypt DB
* RDS Proxy
  * Application points to RDS proxy instead of DB
  * Pools and shares database connections to assist with performance and scalability
  * Serverless and autoscaling
  * Particularly useful for serverless
  * Preserves application conenctions during failover (application isn't aware of failover happening).
  * Can run over multiple AZs
  * Up to 66% faster failover times
