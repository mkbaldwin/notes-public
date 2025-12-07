# HA Architecture

* Elastic Load Balancer
  * Balance load across multiple web/application servers
  * Application Load Balancer
    * Http/https traffic
    * Layer 7 / application aware
    * Intelligent - Advanced routing rules
  * Network Load Balancer
    * TCP (layer 4) connection level balancing
    * Millions of request per second at low latency
    * Use for extreme performance
  * Classic Load Balancer
    * Legacy Service
    * Http/https or TCP
    * Not application aware
  * X-Forwarded-For header is added by the proxy to the HTTP request to identify the end user's public IP
  * Sticky Session - bind a user's session to a specific EC2 instance. Supported only on classic load balancer.
  * Cross Zone Load Balancing - allows a load balancer to balance across instances in multiple AZs. Not enabled by default.
  * Path based routing - Look at the URL to determine where to route traffic. Uses path patterns.
  * Auto Scaling (important for exam)
    * Groups - collection of web / app / db servers
    * Configuration Template - Default template for instances to be launches
    * Scaling options
      * define how and when to scale. Based on conditions or schedule
      * Options:
        * Maintain current instance levels at all times 
          * Terminate and relaunch instance if health check fails
        * Scale manually
          * specify change in minimum or desired capacity
        * Scale based on schedule
          * scale up or down at specific date/time
        * Scale on demand
          * scaling policy based on defined parameters to determine if the app should scale up
        * Predictive Scaling
          * Can help maintain performance and availability 
          * Predict based on previous history
  * HA Architecture
    * Everything fails
    * Plan for failure
    * Use multiple AZs and regions where possible
    * Scaling out vs Scaling up
    * Always consider cost implications
    * Not all S3 storage classes are HA