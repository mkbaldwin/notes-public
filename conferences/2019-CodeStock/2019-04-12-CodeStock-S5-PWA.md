# Progressive Web Apps Across All Frameworks

Mike Hartington / @mhartington / Ionic

  * What are PWAs?
    * Best of web meets native
    * PWA is just marketing words
  * Angular
    * Framework for Mobile/Desktop
    * Decorators, Dependency Injection
      * Lookup angular Decorators... apparently similar to Python's
    * Code Splitting in Angular is driven by 'router'
      * Uses NgModules
      * "Magic String" reference
```javascript
{
  path: 'browse',
  loadChildren: './page/something.module#ClassInModule
}
```
    * Lazy Loading in Angular
    * Service Workers
      * `@angular/pwa` needed
      * Easy way to create workers
      * Turns off caching in dev, only enable for prod
  * React
    * Code Splitting
      * React.lazy / Suspense
    * Service Workers
      * Base worker created, but not enabled
      * Kind of "automatic"
      * Uses `workbox-webpack-plugin`
      * Uses a cache-first strategy
      * Can't easily customize
  * Vue.js
    * Middle ground approach to frameworks
    * Code splitting
      * Core feature of vue-router
      * Standard dybamic imports
      * Included by default when you create a project with routing
    * Service Workers
      * Option available in the CLI
      * Vue docs are readme.md, real docs are from workbox
      * Config are not provided by default
  * No framework is a silver bullet

github.com/mhartington/pwa-across-frameworks
      