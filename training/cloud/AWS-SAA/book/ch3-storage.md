# Storage

## S3

* Organize files into buckets
* Default allows 100 buckets per account
* Name is globally unique
* S3 objects do not have a folder structure, but you can use prefixes or delimiters to mimic a hierarchical structure. S3 understands / as a delimeter and translates it to an appropriate delimiter. The UI will show the folder structure.
* A single object can be as large as 1TB.
* Individual uploads can be no larger than 5GB. Multipart upload recommended for large objects.
* **Transfer acceleration** - Optional feature that routes uploads through a nearby edge location 
* Encryption
    * Should always be enabled unless information is intended to be public.
    * Can be done with client-side encryption on your own or server-side encryption using keys in AWS.
    * Server-Side Encryption with S3-Managed Keys (SSE-S3) - AWS uses its own enterprise standard keys.
    * Server-Side Encryption with AWS KMS-Managed Keys (SSE-KMS) - Uses same protections as SSE-S3 but adss use of envelope key and full audit trail of key usage. Optionally can import your own KMS keys.
    * Server-Side Encryption with Customer-Provided Keys (SSE-C) - Uses customer provided keys.
* Logging
    * Tracking S3 events is disabled by default.
    * When enabling logging you specify the source bucket (to be monitored) and a target bucket (where to put logs).
    * Logs include:
        * IP Address of requestor
        * Bucket Name
        * Action
        * Timestamp
        * Response Status
* Durability
    * Data in most S3 classes is automatically mirrored across 3 availability zones.
    * 99.999999999% durability - i.e., if you store 10,000,000 objects, you can expect to lose one object every 10,000 years.  
* Availability
    * S3 Standard - 99.99%
    * S3 Standard-IA - 99.9%
    * S3 One Zone-IA - 99.5%
    * S3 Intelligent-Tiering - 99.9%
* Data stored in S3 is eventually consistent across all three availability zones. Changes may not be reflected across all three immeidately. Delay is typically under 2 seconds.
* By default saving an object to the same name overwrites the original content. Versioning can allow tracking changes to files.
* Life Cycle Management
    * In addition to S3 Intelligent-Tiering, you can specify custom lifecycle rules for buckets.
* Accessing S3 Objects
    * Buckets/objects are available by default to everything in your account, but not other accounts or visitors. 
    * Permissions can be managed using access control list (ACL) rules, S3 bucket policies, and IAM policies.
    * AWS recommends using S3 bucket policies or IAM policies over ACL rules. 
    * Presigned URLs can be generated to allow temporary access to an object. The URL can be made valid only for a specific period of time.
    * Static Website Hosting - S3 can be used to store HTML files for an entire static website. 
* S3 Glacier
    * Encrypted by default
    * Objects are given machine generated IDs instead of human-readable names. 
    * In Glaicier, the term archive refers to a file that is uploaded. The term vault is used instead of bucket.
    * Classes:
        * Instant - Immediate availability of data.
        * Flexible - Longer time to retrieve data.
        * Deep Archive - Takes 12hrs to retrieve data.
* Cost of S3 is determined by the storage amount and class. Additionally, you are paying for data transfer.

## Other Storage Services

* Elastic File System (EFS)
    * Scalable storage for Linux systems.
    * Network File System (NFS) mounts.
* Amazon FSx
    * Four flavors:
        * FSx for Lustre - Open source distributed file system.
        * FSx for Windows File Server - File shares for Windows servers (SMB).
        * FSx for OpenZFS
        * FSx for NetApp ONTAP
* AWS Storage Gateway
    * Provides software gateway devices with multiple connectivity options. 
    * Local devices can connect as if it is a physical device (e.g. tape drive)
    * Data is stored in EBS or S3.
* AWS Snow Family - Physical devices for moving large quantities of data
* AWS Data Sync
    * Quickly and securely move data from your data center into AWS.
    * Transfer up to 10Gbps if your connection supports that speed.
