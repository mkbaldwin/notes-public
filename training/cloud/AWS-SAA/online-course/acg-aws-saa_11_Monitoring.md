# Monitoring

  * Cloud Watch
    * Monitoring and observability platform
    * System Metrics
      * Supported by default (out of the box)
    * Application Metrics
      * Customized Information
      * Cloud Watch Agent
    * Alarms
      * Alert when something goes wrong
    * Custom metrics require cloud watch agent on host and permissions to access cloud watch from your compute resource.

|              Feature |  Default  |  Custom  |
|---------------------:|:---------:|:--------:|
|      CPU Utilization |     X     |          |
|   Network Throughput |     X     |          |
|       EC2 Memory Use |           |    X     |
| EBS Storage Capacity |           |    X     |