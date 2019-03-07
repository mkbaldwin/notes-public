# Go Java Go

Andres Almiray / @aalmiray / andresalmiray.com / Java Champion

  * Purpose: Showcase the Go programming language from a Java Perspective.
  * Java - been around for 23 years
  * Go - been around for 9 years
  * gobyexample.com
  * github.com/cdarwin/go-koans
  * Go does not have operator overloading
  * Differences from Java
    * Visibility
      * Java has 4 (technically 5) visibility modifiers
      * In go there is a case convention in Go
        * Symbols starting with uppercase are public
        * Symbols starting with lower case are private
    * Type inference
      * Two ways to define variables
        * var strings = []string{"a", "b"}
        * strings := []string{"a", "b"}
    * Collections
      * Slices and Maps built into the language
      * Slices - Kind of like lists/arrays
      * Maps
        * mapofvalues := make(map([string]int))
        * mapofvalues["foo" = 1
        * map[string]int{"foo":1}
      * Arrays 
        * Look like slices but their length is part of the type
          * Much like arrays in other languages
    * Functions
      * Defined using `func` keyword
```Go
fun foo(n int) int {
  return n
}
```
      * Functions can return multiple values
```Go
fun foo() (String, int) {
  return "ok", 1
}
```
      * Functions can passed like variables (similar to lambda expressions), but in Go it is not considered a good practice.
      * Functions can be associated with types
    * There are no classes in Go
    * There is struct
```Go
type Person struct {
  name string
  age int
}
```
      * No need to define constructors
      * `p1 := Person{"Duke", 23}`
      * `p2 := Person{name: "Someone", age: 1}`
    * The Go compiler will fail on statements that are not used (unused imports, variables)
    * Go is always formatted the same way
      * All the go tools will run the gofmt tool
      * Forces a single style
  * Unique features to Go
    * Interfaces
      * Implemented automatically as long as the type matches all methods
      * The `interface{}` type is roughly equivilent to `Object`
      * You never explicitly implement the interface
    * Go does not have exceptions like Jav
      * Uses the multiple return types to "throw" errors
      * First value would be the actual return value
      * Last value would be the error status
        * Leave it up to the programmer to check, or ignore.
    * Type cloning / aliasing
      * `type foo int` (cloning)
        * All the characteristics of int apply to foo
        * Cannot pass a foo to a function that takes an int
      * `type bar = int` (alias)
        * bar and int become identical
        * bar can be passed to function taking int
    * Can also compile go code to assembly
  
         
    
    
  