# Session 1: Reactive Revolution

Josh Long @starbuxman

  * Bootiful Podcast
  
  * Write software that is aware of the fact that things may be asynchronous
  * Threads are expensive in Java (rely on real OS threads)
  * Reactive programming helps with these things
  * Asynchronous IO has been in the JDK for a long time (nio interfaces introduced in 1.4)
    * Not widely used
    * Painful
  * Asyhchronous/Reactive programming is a major paradigm shift in how we think about writing software. 
  * Spring Framework 5, integrates reactive programming into the framework.
  * "I'm going to use the latest and greatest version, because why not. YOLO."
  * Flux - from project reactor, produces 0 or more things
  * Reactive programming is good for anything that is long lived connections. 
    * e.g. great for websockets, no longer requires a thread for each socket to always be open/running.
  * BlockHound
    * Utility to help you locate code/operations that block threads
    * Throws exceptions when you do something that would block the thread
  * rsocket
    * New protocol for reactive connections
    * Binary format
  