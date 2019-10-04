# Session 1: Event-Driven Architecture for Microservices

Francis Solomon

  * Asycntronous Interaction
    * Not all transactions need to be synchronous
    * Eventual consistency
      * How eventual is eventual?
    * In an asynchronous model if a service goes down...
      * other pieces stay running
      * It just looks like it is running slow
    * Some kind of event bus (ActiveMQ, cloud products, etc.)
    * What does an event look like?
      * Document message style
        * Larger content
        * multi puropse
        * push model
    * Publish / Subscribe Model
      * Foundation of the event driven architecture
      * Anyone interested in the events can listen to the topic
      * One publisher and potentially many subscribers
    * Event bus vs data bus
      * Event Bus
        * e.g. RabbitMQ
        * Publish message to a topic
        * Each consumer has its own queue
        * New consumers can only read messages that come through after they subscribe
        * Once a message is read it is removed
      * Data Bus
        * e.g. Kafka, Apache Spark
        * Publish a message to a topic
        * Topic has all of the messages published to it
          * May have retention policies
        * Each conumer has a pointer into the list of messages in the topic
          * When a message is read the pointer is updated, but the message remains
          * You only have one queue everyone
          * New consumers can read old messages too
    * Compensating for failure (with a data bus)
      * With a data bus a client can reset is pointer into a topic
        * An event bus would lose the message (potentially)
      * Events can be replayed
        * Idempotence is critical
        * Can't rely on database sequence generation for IDs
        * Publisher of the message should generate the ID (GUID is common)
  * Summary
    * Coupling between microservices is bad (e.g. lots of REST calls)
    * Allowing asynchronous calls and eventual consistency helps
      * Different way of thinking about the problem