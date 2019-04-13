# Micronaut

Graeme Rocher

  * Complete framework for any type of application
    * Anything with a `main`
    * Even Android
  * No runtime proxying
    * All dynamic class loading removed in 1.1
  * Why Micronaut? Why now?
    * Low memory
    * Fast startup
  * Java's problems
    * Greatly exaggerated
  * Most existing tools are based around runtime proxying, reflection, etc
  * GraalVM
    * New universal virtual machine (ORACLE)
    * native-imate tool
    * Work well with Micronaut
    * Still experimental and evolving fast
  * Micronaut supports multiple JVM languages
    * Java
    * Kotlin
    * Groovy
    * Scala (coming)
  * `@MicronautTest` -> Supports junit/spock
  * BeanIntrospection
    * A reflection free handle for bean instantiation
    * Access to the bean properties
    * Access to annotations on properties of a bean (if they are on the field itself or a getter method).
    * Not using runtime reflection
    * `@Introspected`
  * Micronaut creates "synthetic" classes automatically during compile that are used to support some of its features.
  * `AnnotationMetadata`
    * AOT computed type information
  * Dependency Injection
    * `@Singleton`
    * Favor contstructor injection by default
    * Completely done at compile time
    * No type erasure
    * No dynamic class loading
  * `BeanDefinition`
    * Contains annotation metadata and generic type information
    * Use `@Factory` for beans you cannot annotate
    * Compatible with the `javax.Inject` spec.
  * `@ConfigurationProperties`
    * Type Safe Configuration
  * `@Requires`
    * Used for conditional beans
  * `@Executable`
    * ExecutableMethodProcessor
    * Will invoke your processor anytime the executable annotation is encountered
    * Can be triggered at different times
    * Useful for integration with other tools
  * AOP
    * Compile time AOP
    * `MethodInterceptor`
    * Around advice
    * Introduction advice
      * How Micronaut HTTP client works
  * Micronaut does not modify the bytecode of your classes 
    * unlike things like Lombok
    * Can still be used with Lombok (lombok annotation processor needs to come first)
    * Micronaut analyzes your classes, and creates separate bytecode
  * Micronaut for Spring
    * build configurations that work with Micronaut and Spring
    * Using this with Grails already
      * Classes are processed by Micronaut before being loaded by Spring at runtime.
  * Declarative HTTP client library
  * Sacrifices compilation speed for runtime speed (and more)
  * Solves problems common to many frameworks
  
      
    
  