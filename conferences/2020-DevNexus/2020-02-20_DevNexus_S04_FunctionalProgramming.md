# Session 4: Functional Programming in Groovy, Java, and Kotlin

Kenneth Kousen / @kenkousin / kousenit.com

  * Lambda Expression - Intended to be pure functions
  * Closure - Similar to lambda but can be dependent on scope
  * Kotlin lambdas are technically closures
  * Groovy 
    * Uses closures for lambdas
    * Groovy puts the stream operations (map, etc.) directly onto the collections
    * POGO - Plain old Groovy object
      * `@Canonical` - toString, equals, etc
    * `@Memoized`
      * Automatically generates a cache of values based on the input to pure functions
    * `@TailRecursive`
    * `>>` & `<<` for composing functions
    * `curry` / `rcurry` - Take a closure and replace an argument with a value and return a new closure
  * Kotlin
    * Data Classes
      * `componentN()` functions - used for destructuring
    * `tailrec` keyword
  

