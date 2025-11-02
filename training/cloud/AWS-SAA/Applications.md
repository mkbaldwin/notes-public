# Applications

  * SQS
    * One of the first, if not the first, AWS service
    * Comes up frequently in the Solutions Architect exam
    * Message Queue system
    * Use to decouple components of ann application so that they may run independently. 
    * Decouple is an indicator on the exam that the answer is SQS
    * Messages can have up to 256k of text in any format.
      * Can go larger, but data will be stored in S3
    * Queue acts as a buffer between component producing data vs component consuming data
      * Producer-consumer pattern
    * Queue Types:
      * Standard Queue
        * nearly unlimited transactions per second
        * Guarantees that a transaction is delivered at least once
        * Ordering of messaging is not guaranteed, message could be received twice. Normally are delivered in the order received.
        * Must be able to handle out of order messages and duplicate message in application.
      * FIFO Queue
        * first-in-first-out delivery
        * exactly-once processing
        * Limited to 300 transactions per session
        * Support message groups that allow multiple ordered groups per queue.
      * SQS is pull based not pushed
      * Visibility Timeout - amount of time that a message is invisible in the queue after a reader picks up the message.
        If the job isn't processed before the visibility timeout expires then the message becomes available again.
        * Maximum timeout is 12hrs.
      * Guarantees messages will be processed at least once.
      * Long polling is an option. Doesn't return a response until a message arrices in the queue or a long poll times out.
        * A cost is incurred every time the queue is polled... so this is a good option.
  * Simple Workflow Service (SWF)
    * Service that makes it easy to coordinate work across distributed application components.
    * Tasks represent invocations of various processing steps in an application.
    * Actors
      * Workflow starters - application that can initiate a workflow
      * Deciders - Control the flow of activity tasks
      * Activity workers - carry out the activity tasks
  * SWF vs SQS
    * SQS has a retention period up to 14 days
    * SWF workflows can last upto 1 year
    * SWF is a task oriented API, SQS is message oriented
    * SWF ensures a task is assigned only once, SQS you must handle duplicated messages.
    * SWF keeps track of all tasks and events in an application, SQS you must implement your own tracking
  * Simple Notification Service (SNS)
    * Service that helps make it easy to set up, operate, and send notification from the cloud
    * Push notification to Apple, Google, Windows, and Amazon Devices
    * SMS Test Lineages, Email, SQS
    * Topic - Allows you to group multiple recipients. Recipients can dynamically subscribe for identical copies of the same notification.
    * Messages are redundantly stores across availability zones
    * Benefits
      * Push based delivery (no polling)
      * Simple API
      * Multiple delivery options
      * Inexpensive
      * Web based console for management
  * SNS vs SQS
    * Messaging systems
    * SNS push, SQS pull (poll)
  * Elastic Transcoder
    * Media transcoder in the cloud
    * Convert media files from their original source format into different formats
    * Presets for popular output formats
    * Based on the minutes and resolution
    * How it is used at ACG
      * Video stored in S3
      * Lambda function triggered, sends the video to elastic transcoder
      * Elastic transcoder stores result in S3
  * API Gateway
    * Fully managed service to publish and maintain APIs at scale
    * Acts as a "front door" for access to backend services
    * Commonly used with lambda, but can work with other services
    * What can it do?
      * Expose HTTPs endpoints as a RESTful API
      * Serverless-ly connect to lambda and dynamodb
      * Send API endpoints to different target
      * Track and control usage by API key
      * Throttle requests to prevent attacks
      * Connects to cloudwatch for monitoring
      * Maintain multiple API versions
    * How to configure?
      * Define an API (container)
      * Define resources (URI Paths)
      * For each resource:
        * Select HTTP Methods
        * Set security
        * Choose target
        * Request and response transformations
    * Deploy to a stage
    * Can use custom domain
    * Supports AWS Certificate Manager
    * API Caching can be enabled
      * Cache endpoint response to reduce number calls
      * Cache for specified TTL (seconds)
    * Same-origin policy - permits scripts contained in a first page to access data in a second page as long as they have the
      same origin (domain name). Done to help prevent XSS attacks.
      * CORS - Cross origin resource sharing - allows the same-origin policy to be relaxed
        * Allows restricted resources to be pulled from another domain
        * Server indicates which domains are approved
  * Kinesis 101
    * Streaming data - data that is generated continuously. Records that are generated simultaneously and small sizes.
      * e.g. Purchases, Stock Prices, Sensor data, etc.
    * A platform where you can send streaming data on AWS.
      * Easy to load and analyze data
    * Three types (need to know for exam)
      * Kinesis Streams
        * A place to store streaming data. 
        * Default of 24hr retention, but can be up to 7 days.
        * Shards are used to separate different types of data.
          * 5 transactions/second read / 2MB/sec
          * 1000 transactions/second write / 1MB/sec
      * Kinesis Firehose
        * No data persistence 
        * You must do something right away with the data
      * Kinesis Analytics
        * Analyze data from Streams or Firehose as it comes in
  * Web Identity Federation and Cognito
    * Gives users access to AWS resources after they have authenticated with a web based identity provider like Amazon, Google, or Facebook
    * Use to sign-up and sign-in to your apps.
    * Acts as a broker between your application and web ID providers
    * Sync user data for multiple devices
    * Recommended for all mobile applications
    * Temporary credentials that map to an IAM role
    * No need to embed or store AWS credentials on device
    * User Pool - user directories used to manage sign-up and sign-in 
    * Successful authentication creates a JSON Web Token (JWT)
    * Identity Pool - provides temporary AWS credentials for services like S3 or DynamoDB
  * Event Processing Patterns
    *  Event Driven Architecture
      * Publish/Subscribe Messaging
      * Decoupled systems responding to events
      * SNS Topic - All subscribers receive a copy of the message sent by the publisher
      * Dead-Letter Queue (DLQ)
        * SNS - Topic for messages that fail to deliver
        * SQS - Queue where messages are sent when maxReceiveCount is exceeded
        * Lambda - Results from failed async invocations are sent to SQS or SNS
    * Fan out pattern
      * Process needs to send messages to multiple recipients
    * S3 Event Notifications
      * Can be sent to SQS, SNS, or Lambda
      * Events
        * Object Created
        * Object Removed
        * Object Restored
        * RRS Object Lost
        * Replication