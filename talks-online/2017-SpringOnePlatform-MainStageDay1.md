# Spring One Platform 2017 - Main Stage Day 1

## Announcements

* IBM Open Liberty in Spring Boot 2
* Spring Tools 4
  * IDE Agnostic
* Pivotal Cloud Foundary
  * Windows Server 2016/.NET Workloads
  * Small Footprint PAS (6vms vs 20vms)
  * "BOSH"?
  * Health Watch Dashboard
  * Installation/upgrade pipelines for PCF Infrastructure
  * Support for Azure
  * Dell EMC - Pivotal Ready System
  * Pivotal Container System (PKS)
    * Kubernetes for PCF
    * VMware + Google ...
  * Building a unified platform experience
  * VMware NSX coming to PCF
  * PCF 2.0
  * Riff - Pivotal's open source functions as a service platform
  
## Erich Gamma - Microsoft

* 2011 -> Eclipse everything is a plugin
* Visual Studio Code
  * Partway between IDE and Editor
* Spring / Java plugins available for VS Code (and Atom)

## Phil Webb - Spring Boot Lead

* Spring is not just a DI framework
* Spring is an integration framework that helps you integrate different technologies in a way that feels natural.
  It does that through dependency injection.

> Software maintenance is not keep it working like before, it's keep it being useful in a changing world. - Jessica Kerr

* Statistics from Spring Initializer (last 12 months)
  * View Technologies
    1. Thymeleaf - By far the most popular ~75%
    2. Freemarker
    3. Groovy Templates
    4. Mustache
  * NoSQL/Databases
    1. JPA - Relational databases / ORM by far most popular
    2. Mongo
    3. Redis
  * Spring boot isn't a microservices framework. Its a general purpose framework.
* "You ain't gonna need it" movement
* Some new choices
  * Kotlin
    * Interest has been growing
    * Support in Spring Boot 2
  * Reactive
    * WebFlux (alternatives to Spring MVC)
      * Non-blocking
      * Netty Support
    * Web Client
      * Alternative to rest client
    * Can use some parts even on Spring MVC stack

## Ranji - Scotiabank

* Cloud development platform built on PCF

## Stephane Nicoll / Madhura Bhave 

* Live Coding Demo
* Project reactor gives functionality similar to Java 8 streams but without needing to worry about threads.
* Important to use a reactive data repository
  * e.g. spring-boot-starter-data-mongodb-reactive
* Web Flux 
  * Coexists with Spring MVC
  * Defaults to Netty
  * Also can use Tomcat/Jetty
    * Sticks to only non blocking portions of servlet api 3.1
* Regular spring mvc can use reactive web client/data store
  * Still uses blocking IO for web layer
  * Different concurrency model
  * Some benefits of non-blocking IO
* New features in spring boot actuator

## Simon Wardley

* strategy-madlibs.herokuapp.com
* medium.com/wardleymaps

## John Heveran - Liberty Mutual

* Liberty Mutual - Technology Manifesto