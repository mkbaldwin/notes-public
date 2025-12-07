# Database Services

## Relational Databases
  * OLTP - Online Transaction Processing
    * Frequent read/write
  * OLAP - Online Analytic Processing
    * Less frequent but complex queries

### Amazon Relational Database Service (RDS)

* Fully managed database service built on top of EC2
* Multiple database engines supported:
  * MySQL
  * MariaDB
  * Oracle
  * PostgreSQL
  * Amazon Aurora
  * Microsoft SQL Server
* Licensing Considerations
  * License included
    * MariaDB, MySQL, and PostgreSQL use open source licenses
    * Microsoft SQL Server - All editions include a license
    * Oracle DB Standard Edition Two (SE2) - Includes a license
  * Bring your own license
    * Oracle Enterprise Edition (EE) and SE2 allow you to bring your own license.
* Option groups allow you to specify configuration options for a database type and apply to multiple instances.
* When launching an instance you must select an instance class to decide how much compute, memory, and network bandwidth you need. 
  * Standard - Good for most needs
  * Memory Optimized - Good for heavier performance needs. Have larger amounts of memory.
  * Burstable Performance - Good for development, test, and any other non-production databases. 
* Storage
  * Need to understand the amount of storage and performance needed
  * IOPS (pg 151)
    * Input/Output operations per second
    * Measure of read / write operations performed
    * You are allocated a specific amount of IOPS and this cannot be exceeded, this can limit your performance.
    * Computing IOPS can be complex.
      * e.g. MariaDB has a page size of 16KB. One page will count as a single operation. If you need to read 102,400KB every second then you will use 6,400 IOPS
    * Storage types have different IOPS limits
* Scale Vertically (or scale up) - Add additional resources to existing instance
* Scale Horizontally (or scale out) - Add additional database instances (read replicas)
  * Can have uup to 5 read replicas
  * RDS will load balance connections tot hem
  * Analytic tools that need a read-only connection can point to them
* High Availability
  * Done with a multi-AZ deployment.
  * Primary instance in one AZ doing read/write, standby instance in another AZ
  * If the primary instance has an outage system automatically fails over to the standby (usually within two minutes)
  * All instances must reside in same region
  * MariaDB and MySQL allow you to define multi-region fail-over
  * Amazon Aurora
    * Single Master - Primary read/write instance with multiple replicas
    * Multi-Master
      * All instances can write to the database
      * No fail-over when there is a failure because all instances can continue writing to the cluster
      * Continuous availability 
  * Backup and Recovery
    * Can take EBS volume snapshots of your instances that are stored in S3
    * Snapshotting can be automated to happen daily during a 30min backup window.
    * Snapshots are kept for a limited amount of time then deleted (default 7 days, but can be 1 to 35 days)
  * AWS is responsible for maintenace such as patching and you can specify a 30 minute maintenance window when this will happen.
  * Major upgrades need to be manually applied. 
  * RDS Proxy
    * Proxies connections to your DB
    * Useful for applications that open/close connections lots of connections frequently
    * Useful for failover where the application won't lose all connections
  
### Amazon Redshift

* Managed data warehouse / columnar database
* Good for OLAP 
* Cluster consists of one or more compute notes
* Dense compute nodes can store up to 326TB of data on fast SSDs
* Dense storage nodes can store up to 2PB of data on magnetic hard disks
* If you have multiple nodes then you will have a leader node to communicate among the nodes.
* Redshift Spectrum
  * Allows you to query data files stored in S3 without having to import the data

### Database Migration Service (DMS)

* Automatically copy existing DB and its schema into another database
* Supports many different database types.

## Nonrelational (NoSQL) Databases

* Designed to consistently handle tens of thousands of transactions per second.
* Optimized for unstructured data
* Schemaless
* Each record requires a primary key attribute that must be unique
* Queries
  * Optimized for querying based on primary key
  * Queries against other attributes are slower
* DB Types
  * DynamoDB
    * Handles thousands of read/write operations per second
    * Speed achieved by partitioning data
    * Each partition is 10GB and backed by SSDs in multiple Availability Zones
    * When you create a table, you specify the primary key and data type
      * Partition Key - (hash key) contains a single value
      * Composite Key - Combination of two values
      * Can also be a combination of a partition key and a sort/range key.
    * Hot partition - partition seeing high read/write operations
    * Data Types
      * Scalar - contain only one type of value
        * string - store up to 400KB of UTF-8 text
        * number - store positive or negative numbers up to 38 significant digits
        * binary - store up to 100KB of binary data in base-64 format
        * boolean
        * null - for unknown or undefined value
      * Set - Unorderedd list of scalar values
      * Document - Hold different types of data thart is not scalar or set, can be nested up to 32 levels deep.
      * list - Ordered list of data of any type
    * Modes
      * On-demand - automatically scales to accomodate the workload 
      * Provisioned 
          * you specify the number of read/writes your application requires - provisioned throughput
          * Read capacity units (RCU)
          * Write Capacity Unitys (WCU)
        * Auto scaling can be used to specify minimum and maximumn RCUs and WCUs
  