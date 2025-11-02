# Angular Routing - Ch 5: Route Parameters
   
   * Used to pass small amounts of data (IDs, etc)
   * URL has placeholders for parameters `/item/:id` the `:id` is a placeholder
   * Route parameters can be obtained from ActivatedRoute service
       * `this.route.snapshot.paramMap` -> snapshot of when activated
       * `this.route.paramMap.subscribe()` -> observable that gets updated when the route changes
   * Normally do not place asynchronous code in the constructor, instead place it into the `onInit` function hook - `OnInit` interface.
   * Optional Route Parameters
       * Easier to pass optional or complex information and is not used for path matching. These are not specified in the route configuration.
       * Specified in the router link as a set of key/value pairs (e.g. like json object) `[routerLink]="['/url', {key: val}]`
       * Optional params must come after required params
       * Read from paramMap just like required parameters.
   * Query Parameters
       * Looks like classic query params in URL
       * Work across multiple routes unlike route parameters
       * Not in the route configuration
       * Passed separately
       * `[routerLink]="/url" [queryParams]="{key:val}"`
       * `router.navigate(['/url', { queryParams: {key:val}}]);`
       * Have to watch for key name collisions
       * By default they are reset on navigation. queryParamsHandling preserve allows keeping them
       * Read using:
       * `this.route.snapshot.queryParamMap`
       * `this.route.queryParamMap`