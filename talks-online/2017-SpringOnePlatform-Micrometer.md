# Observability with Micrometer Metrics

[Video Link (YouTube)](https://youtu.be/HIUoeLYWo7o)
Presented at **SpringOne Platform 2017** by **Jon Schneider**

* Think SLF4j but for metrics
* micrometer.io
* slack.micrometer.io
* Not dependent on Spring (can be used with other frameworks)
* Spring Boot 2
  * Autoconfigured by Actuator spring boot actuator
    * By default configures an in-memory metrics store
    * You pick the backing data store you want to use
      * Prometheus
      * Atlas
      * JMX
      * many others...
  * Has replaced their previous iteration of metrics
  * For Boot 1.x you need a bridge library.
  * Metrics are autoconfigured for many types of features.
* Micrometer uses Dropwizard
* CompositeMeterRegistry
  * Combine multiple registry types into one
* Registry
  * Abstraction of where metrics can be sent
* Counter
  * Used to keep track of events.
  * Tags - divide data into "slices"
  * Really good for counting things that increase over time
  * Examples of how to create a counter:
```java
//                              name,         tags
Counter ping = registry.counter("my.counter", "ping");
Counter pong = Counter.builder("my.counter").tag("pong").register(registry);
```
* Gauge
  * Good at monitoring things that have an upper bound (e.g. speedometer)
  * Must provide an object that you are monitoring.
  * You tell the gauge how to get the desired value from the object.
  * Examples of how to create a gauge:
```java
//Object to monitor
AtomicInteger n = new AtomicInteger(0);

//             name,       tags,        obj to monitor, how to update
registry.gauge("my.gauge", emptyList(), n,              n2->n2.get());
```
* Timer
  * 
  * Examples of how to create a timer:
```java
Timer timer = Timer.builder("timer")
                   .publishPercentileHistogram()
                   .register(registry);
```
  * You really need to plot the max value for request timing. 
  * Can record the time it takes to complete some task easily:
```java
  Metrics.timer("my.timer").record(() -> {
    /* Do Something */
  });
```
* FunctionCounter
  * Useful for instrumenting things with existing metrics.
  * Examples of how to create a FunctionCounter:
```java
//Object to monitor
AtomicInteger n = new AtomicInteger(0);

FunctionCounter.builder("fcounter", n, n2 -> n2.get()).register(registry);
```