# Monitoring

AWS provides monitoring tools that can be used to track your AWS environment.

* Tracking Performance
* Detecting Application Problems
* Detecting Security Problems
* Event Logging
* Managing Resources

## CloudTrail

* Keeps a log of all read/write operations against your AWS resources.
* Audit logging
* **Event** - Record of an action taken by a principal (user or role) against an AWS resource.
* Logs both API and non-API actions.
* Management Events
  * Operations against AWS resources (control plane operations)
  * Write-Only Event - Operation that modifies or might modify a resource.
  * Read-Only Event - Operation that can't make changes.
* Data Events
  * Tracks operations on S3 object and lambda function executions.
  * High volume operations
* Event History
  * Logs 90 days of management events by default
  * Separate event history for each region
* Trails
  * Allow you to configure custom retention and or event types to be logged.
  * You can choose to log management events, data events, or both.
* Log File Integrity Validation
  * Can be enabled to ensure that log files are not modified once written.
  * Every log file delivered to S3 is cryptographically hashed.
  * Hourly a digest file is created containing the hashes of all files written in the past hour.


## CloudWatch

### CloudWatch Metrics

* Keeps track of numeric performance metrics from AWS resources as well as other non-AWS services.
* AWS resources automatically send metrics to cloud watch.
  * Examples:
    * EC2 instance CPU usage
    * EBS volume IOPS
    * S3 bucket sizes
  * Metrics are organized into namespaces (a container for metrics)
  * AWS services store in a namespace named in the format: "AWS/servicename"
  * A metric contains a time-ordered set of data points
  * Basic Monitoring
    * Sends metrics to CloudWatch every 5 minutes
    * Supported by most services
  * Detailed Monitoring
    * Supported by some services
    * Sends metrics to CloudWatch once per minute
  * Cloud watch timestamp resolution is configurable. 
    * Some services uses 5 minute resolution by default.
    * Can be adjusted for some metrics to be up to one-second resolution.
    * Resolutions under one minute are considered high-resolution.
  * Metrics cannot be deleted, but expire automatically.
    * High-resolution metrics are retained for 3 hours at which point they are aggregated to 1-minute resolution.
    * After 15 days 1-minute resolution data points are aggregated to 5-minute resolution.
    * After 63 days data points are aggregated to 1-hour resolution.
    * These 1-hour data points are kept for 15 months then deleted.
  * CloudWatch provides tools to graph and analyze data.

### CloudWatch Logs

* Allows you to collect logs from AWS and non-AWS resources and store them.
* Logs are then searchable and can be used to extract custom metrics.
* Log Events - Records of activity recorded by an application.
* Log Stream - Stores log events from the same source.
* Log Groups - A set of related log streams used for organization.
* Metric Filters - Used to extract data from log streams to create CloudWatch Metrics.
* Cloud Watch Agent - command-line utility used to collect logs from EC2 instances and on-premises servers running Linux or Windows.

### CloudWatch Alarms

*  Monitors a single metric and performs an action based on a change in value
*  Can do things like send an email alert, reboot an instance, or execute auto scaling actions.
*  Threshold
   *  The value the data point must meet or cross to indicate a problem.
   *  Static Threshold - Fixed value comparison
   *  Anomaly Detection - Determine if a value fall outside a range of values called a band. Band size is based on a specified number of standard deviations.
   *  Metric Math Expression - More complex formula for evaluation
*  Alarm States
   * ALARM - Data points have crossed a threshold for a period of time
   * OK - Data points have not crossed a threshold
   * INSUFFICIENT_DATA - Enough data points have not been collected to evaluate.
 * Actions
   * Specify what to do when an alarm threshold is met.
   * Notification - Uses SNS to publish an event to a "topic" that can be monitored by various subscribers. 
   * Auto Scaling Action - If you are using auto scaling you can trigger an increase or decrease in the number of instances.
   * EC2 Action - Stop, terminate, reboot an instance.

### Event Bridge

* Monitors for and takes an action based on specific events or on a schedule.
* This is different from CloudWatch Alarms in that it takes action based on an event and not metric values.
* Can take immediate action.
* Event Buses
  * Every AWS account has an event bus for AWS services
  * You can create custom event busses to receive events for your applications.
* Rules / Targets
  * A rule defines an action to take in response to an event.
  * A target is a resource that takes an action based on a rule.
  * Rules can also be invoked on a schedule (e.g. to take hourly snapshots of an instance).

## AWS Config

* Tracks how your AWS resources are configured and how they change over time.
* Can be used to view the configuration at some time in the past.
* Used for the following:
  * Security - Can notify anytime a resource is changed.
  * Easy Audit Reports - Can provide a report of how your resources were configured at a given time.
  * Troubleshooting - Analyze for changes around the time a problem started.
  * Change Management - Analyze how a change to one resource could impact another. 
* Configuration Recorder - discovers and monitors how resources are configured.
* Configuration Item - Represents a resource being monitored.
* Configuration History - Log of changes to a configuration item. Creates a configuration history file every 6-hours in which a change occurs.
* Configuration Snapshots - Log of all configuration from a given point in time. Kind of like a snapshot of configuration being monitored.