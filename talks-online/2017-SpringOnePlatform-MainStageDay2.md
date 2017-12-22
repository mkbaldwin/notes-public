# Spring One Platform 2017 - Main Stage Day 2

## Chip Childers - CTO, Cloud Foundary Foundation

* Value of a platform 
  * freedom to create
* Value of open source
  * "Positive sum game"
  * Sharing is extremely hard
    * How do I avoid having my innovations or contributions used against me?
    * All about trust
    
*Was interrupted during this talk and missed some. Need to go back and watch recorded version.*

## Niki Allen - Boeing

* One 787 Dreamliner will generate about 1TB of data during a single flight.

## Juergen Hoeller

```
  JDK9     JDK10     JDK11
    |        |         |
---------------------------->
    |        |         |
Sept '17   Mar'18   Sept 18
```

* New JDK iteration twice a year
  * New language features
  * Raise bytecode level with each
* JDK 10
  * Adds type inference
* Tools and framework must evolve to handle new JDK releases frequently
* New LTS release every 3 years (JDK 11 is next LTS)
* Spring Framework 5
  * Minimum Java 8
  * Support for Java 9+
* Most people will embrace JDK 11 in production
* Industry Collaboration
  * JetBrains (Kotlin)
  * Reactive Streams (Project Reactor)
    * Related to RxJava
  * EE4j
    * Evolving from specifications originally part of Java EE
    * Being managed by Eclipse Foundation
    * End of traditional Java EE
    * Still being established
* Spring core roadmap
  * 5.1 Q2 2018 (May/June)
  * 5.2 Late 2018/Early 2019
  * Backlogs are in their JIRA
  
## Lt. Col Enrique Oti- DIUX

* Group looking to find products for the military
* Modernizing the air operations center
  * Plans operations in the middle east
  * Partnered with Pivotal Labs
* Agile works even for military

## Kim Bannerman / Meghan Kjelland - Google

* PKS on premise or on Google Cloud Platform (GKE)
  * Both Kubernetes tools
* PKS users have access to the entire GCP product catalog
* Pivotal & Google have a shared vision
  * Make you move faster and help you win
  
## Mark Fisher - Pivotal

* RIFF
  * Event driven functions on Kubernetes
  * Riff is for functions
  * A service for executing functions in response to events
  * workload is a container running on Kubernetes
  
*Was interrupted during this talk and missed some. Need to go back and watch recorded version.*

## Cornelia Davis - Pivotal

* Distributed systems are hard
* Leader election
  * Identical processes that require coordination
  * Quorum - More than half the votes
* Paxos
  * Consensus protocol
  * Only one value ever chosen
  * Actors (Proposers, Acceptors, Learners)
  * Used by cassandra DB
* CAP Theorem
  * Partition Tolerence, Consistency, Availability
  * Can only have two of these at most
  * AP or CP are the only ones most distributed systems can be
  
## John Schnider - Spring Metrics Product Lead

* Formerly of Netflix
* Spring Metrics
  * Better monitoring of your application
* Most orgs monitor system performance
* What is the amount of time a user waited?
* New Project "Micrometer"
  * micrometer.io
  * instrumentation facade
  * Focused on helping get the right information
  
*Was interrupted during this talk and missed some. Need to go back and watch recorded version.*
