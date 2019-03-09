# Getting Started with Service Workers

Jennifer Bland

  * What is a service worker?
    * A script that run in the background on the website.
  * What can they do?
    * Display an offline page
    * Store content in a cache
    * Push notifications
    * Background sync
  * Aside from IE 11 support is pretty good. 
  * Service worker can act as a proxy
    * Will intercept your code's requests to the server
    * Can use as a cache
      * Request will come in and the worker can check the cache. 
      * When not found in the cache reach out to a service on the network.
      * New response will then be cached      
  * WorkS on HTTPS only, or localhost
  * Has controlled scopes
  * Runs in the background in a separate thread
  * Only one service worker is active at a time
  * Service worker stays active until all tabs with your application are closed
  * How do we register a service worker?
    * `navigator.serviceWorker.register('my-script.js')`
      * Need to wrap in checks for browser support and error handling
  * You can place static data into the cache when the service worker loads


  
  
