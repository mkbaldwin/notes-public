# S3

* Simple Storage Service
* Highly scalable object storage
* Large part of the SAA exam
* What is S3?
  * Safe place to store your files.
  * Object based storage.
    * Not suitable for OS/Database which would need block storage.
  * Spread across multiple devices/facilities.
  * Can be from 0 bytes to 5 TB
  * Stored in buckets (like a folder)
* S3 is a universal namespace (bucket names must be globally unique)
* Each bucket gets its own web address
* HTTP 200 code if file upload was successful
* Objects consist of
  * Key - name of the object
  * Value - data bytes
  * Version ID - used for versioning
  * Metadata - data about the data being stored
  * Subresources
    * Access Control Lists
    * Torrents
  * Data Consistency Model
    * Read after write consistency for PUTS of new objects
      * New data can be read immediately
    * Eventual consistency for overwrite PUTS and DELETES
      * Immediately reading after the update you could still get the old version for a brief period of time.
      * Slight amount of time for changes to propagate
  * Reliability
    * Guaranteed 99.9% availability, but built for 99.99%.
    * Guaranteed 99.999999999% durability (11x9s)
  * Features
    * Tiered Storage Available
      * S3 Standard
      * S3 Infrequent Access - Not needed as often, but immediately available. Lower cost.
      * S3 One Zone IA - Similar to S3 IA, but  less resilient
      * S3 Intelligent Tiering - Automatically move data to the most cost-effective tier,
      * S3 Glacier - Archiving uses - retrieval in minutes to hours
      * S3 Glacier Deep Archive - 6-12 hour retrieval time
    * Lifecycle Management
    * Versioning
      * Stores a version of an object even if you delete an object
      * Once enabled cannot be disabled (can only be suspended)
        * Suspend stops new version tracking, but keeps old versions that already exist.
      * Integrates with Lifecycle rules
      * Includes MFA Delete capability
      * New versions are private by default, you must explicitly make versions public.
      * Deleting a file doesn't remove the versions, it adds a delete marker and keeps previous versions.
    * Encryption
    * MFA Delete
    * Secure using ACLs and bucket policies
  * Billing for S3
    * Storage Space
    * Requests
    * Storage Management Pricing
    * Data Transfer Pricing
    * Transfer Acceleration
      * Uses Cloud Front to accelerate upload/download from S3.
    * Cross Region Replication
      * Allows automatic replication of data from one region to another
  * Security
    * All buckets are private by default
    * Access can be controlled through:
      * Access Control Lists
      * Bucket Policies
    * Encryption in Transit
      * SSL/TLS
    * Encryption at Rest
      * Client-side - You encrypt the data before uploading to S3
      * Server-side
        * S3 Managed Keys - SSE-S3
        * AWS Key management service - SSE-KMS
        * Customer Provided Keys - SSE-C
      * Encryption can be enabled for individual object or for entire bucket.