# Kotlin Jumpstart Part 1

Venkat Subramaniam / Josh Long

  * Talk about Kotlin and how you can use Kotlin with Spring.
    * Will intermix Kotlin and Spring
  * Why should we care about a language like Kotlin?
    * Very fluent
    * Highly concise
    * Seems to have got a lot of things right
    * Venkat: When I talk to programmers about Kotlin they don't tell me that they like Kotlin. They tell me they Love Kotlin.
    * Venkat: If you take all of the languages you love and put them in a blender the smoothie that comes out is Kotlin.
    * Compiles down to many forms.
      * JVM
      * JS
      * Native
    * You only need to do what you want to do, and leave out the rest.
      * Less ceremony to get things done
      * .kts files -> Run kotlin as a script
        > kotlinc-jvm -script sample.kts
    * Kotlin is a polygot language
  * Walking through creating an application for Android
    * Josh: "I didn't choose C++ because I like myself and the people that read my code"
  * Kotlin Native
    * Using CLion (JetBrains IDE of choice for making native apps)
    * Created a CSV parser starter project from CLion
    * Very different experience
    * No longer have the JVM libraries
    * Directly use native/posix libraries
    * Josh: "I like to think of Kotlin as a better C or Go"
    * Apparently the Kotlin native compiler is slow
  * Kotlin can compile down to webassembly as well.
  * Kotlin wants us to think about the fact that the name of a variable is more important than the type.
  * Classes in Kotlin are final by default
    * Problem for any framework that uses proxies (e.g. Spring Framework)
    * There is a plugin to open classes automatically.
      * Smart enough to know which classes have spring annotations that require it to be extensible.
  * Objects are singletons
    * Keyword `object` to make them
  * Data Classes
    * Take away the ceremony involved in creating "POJOs"
    * No need to worry about `equals`, `hashcode` and `toString`
      * Venkat: "The only reason you would want to write all those is if you are getting paid by lines of code you write. You just want to get your work done and go home"
  * Extension Functions
    * Add functionality to existing classes without extension
    * Open for extension, closed for modification
    > fun String.shout() = toUpperCase()
    * When translated to the JVM bytecode these are static methods that receive the target object as a parameter.
    * Can still use these in Java, but they are accessed as static methods
  * Nullable Types
    * "Creating null, the million dollar mistake"
    * Kotlin requires you to specify nullability on variables
    * `?.` Null Save Operator
    * `something?.param ?: default value` Can be combined with the elvis operator.
     
    
    
  