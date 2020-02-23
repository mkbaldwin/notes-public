# Revisiting Effective Java in 2020

Edson Yanaga, Red Hat - @yanaga

  * Factory Methods
    * e.g. `public static PhoneNumber of(int areaCode, int number)`
    * Can have a different name.
    * Doesn't always have to return a new object, maybe it pulls from a cache.
    * Not always even required to return the same type, maybe you want to return another compatible type based on what the input to the factory.
  * `Objects.equals()` 
  * If you are using an object as a key to a hashmap, make sure it is immutable, or at least has an immutable key to use for hashcode.
  * toString isn't for business values, it should be used to create text for logging/debugging
  * `Formattable` interface that can be implemented to format a string. Called when using `String.format` or `System.out.printf`
  * `Comparator.comparingInt()` - New way of building comparators for making a compareTo method. This is thread safe, so it can be created once (static) for the object.
  * Functional Interfaces
    * Favor strategy over template method pattern
    * `@FunctionalInterface` - Use when you want to make a functional interface for using in a lambda. Will cause code not to compile if you add a second method which would cause problems other places.
  * Method References - 5 types in Java
    * Static: `st(Integer::parseInt)`
    * Bounded: `b(Instant.now()::isAfter()`
    * Unbounded: `ub(String::toLowerCase()`
    * Constructor: `c(TreeMap::new)`
    * Array: `a(int[]::new)`
  
    