# Reactive for the Impatient

Mary Grygleski / @mgrygles / IBM

  * A gentle introduction to reactive programming
  * Reactive Principles
    * Responsive
    * Resilient
    * Elastic
    * Message Driven
  * Event Driven vs Message Driven
    * Event driven - more like publisher/subscriber
    * Message driven - you know where the message is going to
  * Patterns and terminologies
    * Reactivity - response to some stimulus
    * Events - the stimuli that trigger a reaction
    * Design Patterns
      * Observer
      * Composite
      * Iterator
  * Failures are treated as another type of event
  * Marble diagrams
    * Visually describe how things work in a reactive system
    * https://rxmarbles.com
  * How are microservices related to reactive programming/systems
    * Reactive programming can be used inside a microservice
    * Reactive systems used between the microservices
  * RxJava
    * Java implementation of the ReactiveX standard
    * Popular with Android developers
    * Java 6+ support
    * Partial reactive stream support
  * Spring Reactor
    * Java 8+
    * Fully supports reactive streams
  * Akka
    * From Lightbend (partnership with IBM)
    * Actor Model (from Erlang - 1980s - Actor Programming model)
    * Event Driven
    * Lightweight
    * Supervisor capability
      * Resiliency / Recoverability
    * Requires a bit more setup, but the framework is more sophisticated
    * Started off in Scala
  * Vert.x
    * Interoperates with other frameworks and tools (RxJava, Spring Reactor, etc.)
    * Verticles -> Components being deployed and executed by the Vert.x instances
    * Vert.x Event Bus -> Knows how to route the message
  * Takeaways
    * Overloaded term
    * Not for the faint of heart
    * Not the same as "functional reactive programming" or "reactive systems"
    * Still not fully ready on database systems