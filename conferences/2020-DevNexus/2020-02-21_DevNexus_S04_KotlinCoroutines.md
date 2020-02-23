# Structured Introduction to Kotlin Coroutines

Roman Elizarov, JetBrains - @relizarov

  * Coroutines are an old concept
  * First introducted in Simula'67
    * CLU 1975
    * Erlang 1986
    * Go 2009
    * C# 2012 - async/await (first Mainstream language)
  * Today most of the code we write is just waiting on something else
  * Asynchronous programming
    * Don't block the thread while waiting and doing nothing.
    * How do we wait without blocking?
      * Green threads/coroutines/fibers
      * When the code gets blocked waiting, move the call stack to the side and then let the thread do other work.
      * Erlang uses this approach.
      * Java 1.0 was originally based on green threads.
        * Moving around the call stack was complex
        * There wasn't a need a the time for the feature
        * Java 1.2 introduced real/native threads
        * Project Loom is bringing back runtime support for this again.
      * Callback/Event Listners
      * Futures/Promises/Reactive
      * async/await
      * Most ways require special ways to write the code
  * Kotlin Coroutines
    * Allows you to write your code as usual (like magic)
    * Suspended functions, mark a function with the `suspend` keyword.
    * How does it work?
      * When the compiler sees the `suspend` keyword it creates Java that takes a `Continuation` parameter. Essentially adds a callback.
    * Integration with existing asynchronous frameworks
    * Ability to suspend execution is one of Kotlin function's super powers
    * Coroutine builders
      * The most basic is `GlobalScope.launch`
        * Returns immediately, and the work happens in a background thread pool
        * Can tell a coroutine to run on a speficic dispatcher. Can be used to say it must be run on the man thread.
      * Builders for creating CompletableFutures (`GlobalScope.future`), etc.
      * The best analogy is that Kotlin Coroutines are lightweight threads
        * There is way more to coroutines than this
    * Cancellation
      * Probably every application needs, but nobody gets right.
    * Structured Concurrency
      * A way of writing your code so it doesn't "leak" and leave behind work that doesn't need to be done anymore.
      * `coroutineScope` - Can be used to wrap calls to await and cancells all operations if one fails.
    * Coroutines enforce structure
      * The coroutine builders are all extensions on CoroutineScope. 
      * Forces all of the async code to be in a scope.
      * Types serve as documentation
      * Types are enforced
      * Scope must be explicitly provided
    * GlobalScope, what is it?
      * Extension of CoroutineScope
      * Serves as the main scope for the application
      * If you launch a coroutine within a coroutine then the nested call gets a different scope than the GlobalScope
    * Allows you to write very safe, leak free, code.
    * Can create a separate thread pool for more computationally intensive (CPU bound) tasks. A coroutine executor can be created from a normal executor in Java. Then it can be passed when creating the coroutine.
      * Helps with scalability.
      * Keeps big CPU tasks from holding up other things.
    * The catch... Thread Switching
      * Shared thread pool out of the box (default dispatchers)
      * If needed automatically creates more threads that aren't blocked.
    * `runBlocking` waits for completion of children
    * Coroutines and data streams
      * Channel
        * send()/receive()
        * Create a producer (`produce {}`)
      * Flows
        * Safer way to do asynchronous data streams
        * `flow { for(...) { emit() }}`
        * Flow is "cold" it doesn't run until it is collected.
        
        
      
      