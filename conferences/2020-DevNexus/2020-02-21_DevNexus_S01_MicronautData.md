# Ahead of Time Data access with Micronaut

Todd Sharp

  * Does compile-time rather than runtime processing
  * Import dependencies and add annotation processor in Gradle
  * Uses JPA annotations, or Micronaut's own annotations for defining entities, etc.
  * Repositories can be interfaces, or abstract classes.
    * Include baked in default CRUD operations
    * Abstract classes let you get down to writing native SQL
    * In JDBC mode  it doesn't have any concept of session/dirty checking
    * Custom queries in Micronaut data are inspired by GORM (which was inspired by Rails)
      * find<X>By<Y>OrderBy<Z>
      * This is similar to Spring data JPA
      * You can also do projections to only load specific fields
      * Things other than find:
        * countBy
        * existBy
        * updateBy
        * deleteBy
      * You can also do a simplified find syntax by doing things like `findBook(String title)`. This is less flexible.
      * Can create Projections using DTOs (POJO).
        * Annotate DTO with `@Introspected`
        * Use the new DTO as return type
    * Soft delete using `@Where`
    * Explicit queries using JPA-QL
    * Join Queries
    * Pagination
      * Change repository to a `PageableRepository`
      * Queries expect a Pageable that takes offset, max (much like Spring Data JPA)
  * GraalVM / Native Images
    * Graal has multiple parts
      * A different just in time compiler that changes how your code runs
      * AOT compiled native image
    * Can do custom type definitions.
    * Can also do column transformations when loading / saving data in and out of the entity