# Spring Framework 5: Hidden Gems

[Video Link (YouTube)](https://www.youtube.com/watch?v=Oytwjf7Al8c)
Presented at **SpringOne Platform 2017** by **Juergen Hoeller**

  * Spring 4.3 was an early backport release of many features planned for 5.0 release.
  * Logging
    * Convoluted history
    * First class support for:
      * Log4j 2
      * SLF4J
      * JUL
    * Spring-style runtime detection of Log4j 2/SLF4j providers
    * No custom bridges
      * streamlined setup of Log4j 2/Logback
    * Implements its own commons logging bridge
      * spring-jcl
  * Build-time components indexer
    * Classpath scanning at startup can be slow
    * Build time annotation processor to generate index file placed in the jar
      * `META-INF/spring.components`
    * Skips classpath search
    * No code change required
  * Nullability
    * Annotations used to indicate nullable or not nullable across the codebase
    * Better compatibility with Kotlin
    * Nullability validation in IntelliJ IDEA
      * "Constant conditions & exceptions" inspection
  * Data Class Binding
    * Can work better with immutable classes.
    * Works well with Kotlin `data class`
    * Property names matched against constructor parameter names
      * Assume this is a data class if no default constructor
      * Assume it is immutable class populated through its constructor
      * Explicitly property names via `@ConstructorProperties`
      * Inferred from class bytecode (`-parameters` or `-debug` on javac)
  * Programmatic lookup via ObjectProvider
    * Spring 4.3+ can declare an injection point: `@Autowired ObjectProvider<MyBean>`
    * Lookup API with `getObject()` and some other related methods.
    * Allows you to Lazily resolve an object.
    * Request a fresh instance of a prototype scope, etc
  * Refined resource interaction
    * As much as possible was upgraded to NIO.2 API
  * Asynchronous Execution
    * `ListenableFuture` and `CompletableFuture`
    * New Date/Time API can be used with `TaskScheduler`
    * ScheduledTaskHolder` interface for monitoring current tasks
    