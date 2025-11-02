# S3

## Securing S3 Buckets

* All buckets are private by default (can only be used by the owner)
* Bucket Policies
  * Applied at bucket level, and premissions apply to all objects in the bucket
  * Useful for groups of files in a bucket that need the same permissions
  * Policies are written in JSON
  * AWS Provides a Policy Generator Tool
* Bucket Access Control Lists (ACLs)
  * Applied at the object level
  * Allows for granting different permissions to objects within the same bucket
  * Fine grained access control
* Provides access logs to track all requests made to a bucket.
  * Not enabled by default.
  * Logs are written to another S3 bucket.
* All buckets are encrypted by default.
* Encryption Options
  * Encryption in Transit using SSL/TLS (HTTPS)
  * Encryption at Rest (server side encryption)
    * SSE-S3
      * Uses S3 managed encryption keys
      * AES-256
      * Enabled by Default
    * SSE-KMS
      * Uses AWS Key Management Service managed Keys
    * SSE-C
      * Customer-provided keys
  * Encryption at Rest (client side)
    * You encrypt the files yourself before you upload them.
* Cross Origin Resource Sharing (CORS)
  * A way to allow code from one S3 bucket to access resources in another bucket.


## Amazon Athena

* Allows you to run standard SQL queries on data stored in S3
* Serverless service.
* Pay per query / per TB scanned.
* Works directly with data stored on S3.
* Use Cases
  * Very useful for storing log files stored in S3
  * Cost analysis (analyze cost/usage reports)
  * Business reports on data stored in S3
* Using Athena
  * Must create an S3 bucket where Athena Query Results will be stored.
  * You must also create a database.
  * You must then create a table, and tell Athena where to retrieve the data (note this create statement is not entirely standard SQL).
