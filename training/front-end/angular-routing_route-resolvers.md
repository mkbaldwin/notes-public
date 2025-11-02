# Angular Routing - Ch 6: Route Resolvers

  * Route parameters are good for simple data
  * Component isn't activated until the data is received
  * Route resolver is created as a service that implements `Resolver<MyObject>`. Provides a resolve method.
  * Resolver will receive a snapshot of the activated route and router state.
  * Can return an observable, promise, or just the data.
  * Retrieve ID or other parameters from the route and call a service to get the needed data.
  * Can return an observable directly from the service and the resolver handles the subscription, and waits for it to complete before continuing on to the component being rendered
  * Error Handling
    * Check required parameters
    * Options
      * return false which cancels nav and leaves user on the original page
      * return null which leaves things to the resolved route to handle
      * Navigate to Error Page
    * No built in method for passing errors to the prior or activated route
    * Ways to send error info:
      * Use a service
      * Optional param on route
      * Custom error handler
      * Define resolved data to include error information
        * e.g. Product class with data
```typescript
interface ProductResolved {
    product: Product;
    error?: any; //Optional error message
}
```
   * Resolver can return ProductResolved instead of product.
   * Need to handle error from service as well
```typescript
productService.getProduct().pipe(
    map(product => {product: product}),
    catchError(err => { return of({product.null, error:err})})
)
```
  * On route config: `resolve: { product: ProductResolver}`
  * Reading Resolved Data
    * `this.route.snapshot.data['product']`
    * All components share same returned object instance
    * `ngOnInit` is not executed again if you stay on the same page - observables address this
    * `this.route.data.subscribe(data => { data['resolvedData']})`