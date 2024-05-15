# AWS Developer Associate: Misc Services

## Route 53

* Amazon's DNS service
* Allows mapping domain name to EC2 instances, load balancers, and S3 buckets

## AWS CLI

* Must run `aws configure` one time before use.
* This will require creation of an IAM user.
* S3 operations
  * `aws s3 ls` - List buckets
  * `aws s3 mb s3://mybucket` - Create bucket
  * `aws s3 cp localfile s2://mybucket` Copy file to bucket
  * `aws s3 ls s3://mybucket` - List files in bucket

IAM roles are a secure way to grant privileges to AWS entities to perform functions.

## Systems Manager: Parameter Store

* Helps avoid hard coding parameters in code
* Standard tier supports up to 10,000 parameters up to 4k with no charge.
* Advanced tier supports > 10,000 params up to 8k for additional Cost

## AWS Secrets Manager

* Protect and store secrets for DB connections, API Keys, etc.
* DB secrets for RDS can be automated including username, password, port, url, db name, etc.
* Supports automatic rotation of secrets using a lambda function
  
## CloudFront

* AWS' content delivery network.
* Utilizes AWS Edge Locations (200+ locations).
* Used to improve performance of a website.
* Integrated with other AWS services (e.g. S3, EC2, ELB, and Route 53).
* Objects are cached for a specific time to live (TTL)
  * Default TTL is 1 day
  * You can clear an object from the cache manually, but there is a charge.
* Used to support S3 Transfer Acceleration.
* Can also cache resources for services running in your own data center.
* Origin Access Identity - A special user that can access files in an S3 bucket and serve them to users.
* CloudFront Allowed Methods
  * Specify which HTTP methods that the distribution supports.
  * `GET, HEAD` - Read Only
  * `GET, HEAD, OPTIONS` - Read Only
  * `GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE` - Read/Write
  * Consider what users need to do on your website to determine the correct selection.

| Method  | Type  | Description                                                                      |
|---------|-------|----------------------------------------------------------------------------------|
| GET     | Read  | Retrieve Data                                                                    |
| HEAD    | Read  | Inspect resource headers. Similar to GET, but doesn't include the response body. |
| PUT     | Write | Send data to create a new resource, or replace an existing resource. Idempotent. |
| PATCH   | Write | Partially modify a resource.                                                     |
| POST    | Write | Insert data; used to create or update a resource. Not idempotent.                |
| DELETE  | Write | Remove data.                                                                     |
| OPTIONS | Read  | Used to find out which HTTP methods are supported by the URL.                    |
