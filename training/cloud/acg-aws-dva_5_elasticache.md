# Elasticache

* In-memory cache (key-value store)
* Improces DB performance
* Great for read heavy workloads
* Session Data Storage
* Memacached
  * Basic object caching
  * No persistence, single AZ, no failover
  * Good for basic caching
* Redis
  * More sophisticated solution
  * Can store complex data types
  * Has persistence, multi AZ, and failover capabilities.
* Elasticache is useful for read heavy DB with infrequently changed data
* Can't help with write workloads
* Not helpful for OLAP queries
* MemoryDB for Redis
  * Massively scalable in memory DB (1gb to >100tb)
  * Highly available (multi AZ)
  * Can be used as a primary database
  * Transaction log for recovery and durability
  * Supports > 60 million requests per second
  * Workloads that need high performance redis compatible database