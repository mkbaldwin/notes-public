# Data Ingest & Transformation

## AWS Lake Formation

* Allows you to create a data lake from all of your data.
* Supports AWS and on-premise sources.
* Utilizes AWS Glue to perform extract, transform, and load (ETL) operations.
  * Glue is based on Apache Spark
* Ingestion
  * The process of collecting data from various sources and pulling it into your data lake.
  * Can import from many AWS services (e.g., S3, RDS, CloudFront, CloudTrail, etc.)
  * Can import from any database with JDBC support.
* Transformation
  * The process of preparing data including formatting, combining, deduplication, etc.
* Analytics
  * Querying, visualizing, or performing statistical analysis to uncover meaningful patterns in data.

## AWS Transfer Family

* Lets you move data in and out of S3 or EFS using:
  * File Transfer Protocol (FTP)
  * SSH File Transfer Protocol (SFTP)
  * File Transfer Protocol over SSL (FTPS)

## Kinesis

* Services to collect, process, and store streaming data.
* Kinesis Video Streams
  * Designed to ingest and index almost unlimited amounts of streaming video data
  * Sources like: webcams, security cameras, phones.
  * Uses a producer-consumer model.
  * Producer - The data source producing the video and sending to Kinesis.
  * Consumer - Any application that reads the video stream.
* Kinesis Data Streams
  * Data pipeline that can reliably aggregate, buffer, and store data from producers until consumers are ready to process it.
  * Examples:
    * Application Logs
    * Stock Trades
    * Financial Applications
  * Amazon Kinesis Agent - Java-based application that can run on Linux servers to stream application logs.
  * Kinesis Producer Library (KPL) - can be used to have your application send directly to Kinesis.
  * Stores data in a record along with a partition key and sequence number.
  * Sequence number is used instead of a timestamp since the data may not be time-dependant, but order is important.
* Kinesis Data Firehose
  * Can ingest streaming data and transform it before sending to the destination. 
  * Can also send a copy of untransformed data to S3 for safekeeping.
* Kinesis Data Streams and Data Firehose are similar services. 
  * Firehose is tightly integrated with AWS and third-party services and is often better when working with these tools.
  * Data Streams is better for working with your custom application.