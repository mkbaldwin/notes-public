# Serverless Computing

* Allows you to run your application code in the cloud without worrying about servers.
* AWS Handles:
  * Capacity Provisioning
  * Patching
  * Scaling
  * High Availability
* Eliminates overhead of managing servers.
* Extremely scalable.
* Never pay for over provisioning.
* Event driven, only charged when code is executed.
* Examples of AWS Serverless Technologies
  * Lambda - run code as functions
  * SQS - Simple Queue Service
  * SNS - Simple Notification Service
  * API Gateway - Create, publish, and secure APIs.
  * DynamoDB - Fully Managed NoSQL DB
  * S3 - Object storage / web hosting

## Lambda

* Takes care of everything needed to run your code including the runtime environment.
* Supports: Java, Go, PowerShell, Node.js, C#, Python, and Ruby.
* Costs
  * Based on the number of request, duration, and amount of memory used.
  * Requests
    * First 1 million requests per month are free.
    * $0.20 per 1 million additional requests in a month.
  * Duration
    * Charged in 1ms increments
    * Price is based on memory allocated.
  * Memory
    * Charged per GB-second
    * $0.00001667/GB-second
    * The first 400,000 GB-seconds per month are free
* Event driven architecture
  * Automatically triggered from other AWS services or called directly from a web application
  * Triggered by S3 events (e.g. change to S3 bucket)
  * Triggered by user request from API Gateway
  * Asynchronous - no response is expected or required
  * Loosely Coupled
  * Single-Purpose Functions
* Versioning
  * When you create a function there is only one version
  * Tagged as `$LATEST` which represents the latest version
  * Can create different versions of the code and assign aliases to access them.
    * Useful for separating prod, test, dev, etc.
    * Alias is referenced in the arn for the function
  * If the ARN does not include a version then it is 'unqualified' and refers to the latest version.
* Limits
  * Maximum number of functions that can be run across all functions in a region per account
  * Default of 1,000
  * TooManyRequestsException - HTTP 429
  * Can open a ticket with AWS Support to request the limit be increased.
  * *Reserved Concurrency* - Guaranteed a set number of executions will always be available for your critical fuctions. This also acts as a limit.
* Private VPC Access
  * Can grant Lambda access to a private VPC
  * Add `AWSLambdaVPCAccessExecutionRole` to the execution policy for your function.
  * Must configure private subnet ID and security group

## API Gateway

* Service that allows you to deploy, maintain, and monitor APIs
* Supports RESTful APIs as well as Websocket APIs
* Provides a single end point for clients and route to different services inside AWS
* Supports multiple versions of your API
* Serverless service
* Supports throttling request rates

## Step Functions

* Provides a visual interface for serverless applications
* Manage the logic of your application (orchestration)
* Automatically log the state of each step for debugging
* 

## Miscellaneous Services

* **EventBridge** - helps you handle events and route them to application components.