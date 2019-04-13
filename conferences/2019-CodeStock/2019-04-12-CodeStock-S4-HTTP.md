# Learning the language of HTTP for better data experience

Chris Woodruff / JetBrains (Developer Advocate .NET) / @cwoodruff

  * The HTTP Protocol
    * HTTP Methods/Verbs
      * GET - Queries the representation of a resource
      * POST - Changes state of a resource
      * PUT - To replace content of an existing resource
      * DELETE - Delete a resource
      * HEAD - Same as GET without a response body
      * PATCH - Apply partial modifications
      * TRACE - Loop-back test
      * OPTIONS - Determne options and/or requirements associated with a resource
      * CONNECT - Establishes a tunnel to server identified by target resource (SSL)
    * HTTP Request
      * Consists of a header and a body
      * Header
        * Contains HTTP Verb
        * Metadata
          * From 
          * User-Agent - Info about the client making the request
          * Accept - Define what type is expected
          * Accept-Encoding - Define what encoding is expected for the return data
          * Content-Length - Size of content being sent
          * Content-Type - Specify the type of content being sent
      * Body
        * Any data that you want to send to the server. Usually empty for GET.
    * HTTP Response 
      * Status Codes
        * 1xx - Information Responses
        * 2xx - Success
        * 3xx - Redirection
        * 4xx - Client Error
        * 5xx - Server Error
      * Header
        * Returns the Status code/text as well as other metadata about the response
      * Body
  * REST
    * REpresentational State Transfer
    * REST is a very generic concept. Lots of different implementation.
    * Constraints
      * Must be client-server architecture
      * Stateless communication (client must hold all state)
      * Caching
      * Uniform Interface
        * Self descriptive messages
        * Hypermedia as the engine of application state
      * Layered System
      * Code on Demand
        * not usually used
    
        
    