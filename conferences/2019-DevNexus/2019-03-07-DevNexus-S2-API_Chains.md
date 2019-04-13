# APIs, Chains, and Graphs

Michael Stowe / @mikegstowe

  * Why we build APIs
  * undisturbedrest.com
  * Web APIs
    * Act as an interface
    * Usually over HTTP
    * Let different systems communicate without being tightly coupled
  * Many kinds of APIs (SOAP, REST, GraphQL)
  * History
    * XML RPC
      * Early API
      * Tightly Coupled
    * SOAP
      * Special Libraries
      * Bloated Request/Response
    * JSON RPC
      * Tightly Coupled
      * Need Extensive Docs
    * REST
      * Created before JSON
    * GraphQL
      * Used by Facebook/Github/etc
      * Tightly coupled to our models/relationships
      * No versioning of APIs
      * Same problems as rest
  * REST
    * Clear separation of client/server
    * Stateless
    * Client / Server can evolve separately
    * Cacheable
    * Uniform Interface
  * Hypermedia
    * Media with links
    * 1945 - Vannevar Bush
    * 1987 - Hypercard
    * Hypermedia is a requirement for rest
      * HATEOAS - Helps server & client evolve separately
      * Hypermedia is the engine for application state
  * GraphQL
    * Query language to request the info that you want
    * Powerful query capabilities (all in one call)
    * Client needs to understand business rules
    * Not standard for versioning
  * Hypermedia is designed to describe state
  * GraphQL is designed to query model
  * CHAINS
    * Rest API multiple Request Chaining - RAMRC
    * Logic based on standard logical operators
    * Series of calls based on result of previous call
    * Lets you specify what date you want returned
    * JSON format
    * SDKs for multiple languages
    