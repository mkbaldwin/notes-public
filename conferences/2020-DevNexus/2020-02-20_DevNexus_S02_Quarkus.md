# Session 2: Quarkus - Becoming Supersonic

Roberto Cortez, RedHat - @radcortez
Justin Lee, RedHat - @evanchooly 

  * Opinionated framework for writing Java microservices
  * Why Quarkus?
    * Startup & Memory Overhead
    * Developer Joy
      * Zero config
      * Live reload
      * Streamlined code for common use cases
      * Flexible for the other cases
      * Easy native executable generaton (GraalVM)
    * Memory Usage (example REST application)
      * Traditional Stack - 100MB+
      * Quarkus + OpenJDK - ~70MB+ (JVM Mode)
      * Quarkus + GraalVM - ~12MB (Native Mode)
    * Startup Times
    * Unifies Imperative & Reactive
      * Can have both types of endpoints in the same application
    * Uses best of breed frameworks
  * How does it work?
    * Moved as much as possible to the build phase.
    * Minimal dependencies
    * Dead code elimination
    * Various optimization levels (benefit both GraalVM and HotSpot)
    * Little use of reflection
  * DevMode watches for file changes and rebuilds automatically (very fast rebuild)
  * Native Image (GraalVM)
    * No classpath, or libraries at runtime. All resolved at compile time. 
    * Native build is not as fast (compile) as JVM, but runtime is faster.
    * Some things are not supported in GraalVM
      * Dynamic Class Loading, InvokeDynamic, Method handles
      * JVM Interfaces (JMX, etc)
    * Some things have caveats in their usage
  * GraalVM
    * Best for the fast startup
      * Serverless
      * Short lived processes
    * JVM can give better throughput for long running processes
      * JVM does dynamic optimization as the JVM runs and figures out ways to run the app optimally.
    * Libraries might or might not work in native mode
  * Panache
    * Quarkus adds support for Active Record style to Entities/Hibernate 
  * Dev mode
    * Support live reloading
    * No server restart
    * Watches code files for changes and automatically recompiles
    