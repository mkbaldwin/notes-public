# Building webapps with Vue.js and Nuxt.js

Raymond Camden

  * What is Nuxt?
    * A framework that adds a lot of "sugar" to building applicaions with Vue.js
  * Installs a command line utility for creating a Nuxt app
    * Asks you a bunch of questions about what you want your app to be
  * Pages and Routes
  * Layouts
    * Cannot do nested layouts
    * Might use components as an alternative to nested layouts.
  * Components -> Work the same way as in Vue.js
  * Async
      * Promises
        * `asyncData` -> Must return a promise 
        * Axios (works great with Nuxt, but not required) 
      * Async/Await syntax can be used as well
  * Dynamic routes
    * Defined by a page or folder beginning with an underscore
    * Dynamic part (ID) can be required or optional
    * Route params can be validated with custom logic
    * By default not supported out of the box for static output (per docs)
      * Presenter says the docs are wrong, he tried and it did work (since it is still an SPA)
  * Vuex
    * Provides a store for holding state/data in your app.
  
  