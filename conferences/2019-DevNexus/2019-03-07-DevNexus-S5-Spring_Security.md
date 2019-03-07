# Spring Security 5.1

Rob Winch / @rob_winch

Live demo of some microservices and setting up Spring Security

  * Example application with spring security 5.1 and oauth2
  * Using [Keycloak](https://www.keycloak.org/about.html) as the sample IdP for OAuth
  * OAUTH scopes
    * Kind of like roles?
  * `@AuthenticationPrincipal` annotation lets you provide expressions to access values in your principal object.
    * Good idea to create a custom annotation (RUNTIME retention) and apply the authentication principal to that annotation. That way you don't have as much spring security stuff mixed into your code.
  * Method Security
    * `@EnableReactiveMethodSecurity`
    * `@PostAuthorize("returnObject?.to == principal?.claims['user_id']")` annotation applied to the repository paths
      * Only allows the requested message to be returned if the "to" contained the user's id. Can be used to prevent access based on the data being returned.
  * Spring security has support for Mock MVC for unit testing as well as spring web test client.
  