# Scenic City Summit 2016

 * August 12, 2016
 * University of Tennessee at Chattanooga

Keynote 1 by Cory House (same presentation as at CodeStock 2016).

## Session 1: A developers journey from OO to functional

Reid Evans (@ReidNEvans)

SOLID Principals -> "uncle bob"

15 - 50 errors per 1000 lines of code - Industry Average

"If you have a class with two methods and one of them is a constructor you have a function" - @JackDied

What is functional programming?

 * Totality -> Every value we give to a function returns another value
 * Determinism -> Same result for a specific value every time
 
 Every function can be replaced with any other function that has the same signature.
 
 "Happy Path" -> Estimate you give of how long the task will take
 
 How to choose a functional language
  * Clojure
  * F#
  * Elm
  * Haskell
  * Erlang
  * Scala
  * Your current language
  
Anecdotal Results Switching
 * 5 months development
 * 3582 LOC
 * 2 bugs not caught at compile time

> Just because your unit tests pass doesn't mean your code is correct.

##Session 2: Designing for People

Jessica Ivins (@jessicaivins)
 * UX Designer
 
 
 * Useful - needed
 * Usable - understandable
 * Desirable - wanted & enjoyable
 
 
 * Must understand what the user needs
 * Find out the need before doing any design or development
 * Ask what they need
 * Ask what they struggle with
 * Asking what they want isn't always useful. We don't get good info back.
 * Books
   * Just Enough Research - Erika Hall
 * Reduce barriers to entry
 * Desirable
   * Make your product delightful (depending on context)
 * Designing for emotion
   * Don't get carried away - i.e. Clippy

## Session 3: ???

_Either I didn't take any notes during this session or mis-numbered my hand written notes._

## Session 4: 12 Keys to Scalable JavaScript

Cory House

1. JS Belongs in a JS File
2. JS Code Should be Static
   * Don't generate JS dynamically in server code
   * Javascript Configuration Object Pattern
3. JS Should Be Minified
4. JS Should Be Linted
   * ESLint _(recommended)_
   * JSHint
   * JSLint
5. JS Should Have Automated Tests
   * Hardest Part -> Choosing How
   * Options
     * Mocha _(speaker's recommendation)_
     * Expext library
     * Cheerio
     * JSDOM
     * Karma
   * Tests should run when you hit save
   * "The Peltzman Effect" -> When you add more safety people take more risks.   
6. JS Should Be Encapsulated
   * Avoid Globals
   * CommonJS
   * ES Modules
   * IIFE
   * AMD
   * Revealing Module
   * _Recommended to use CommonJS or ES6 Modules_
7. Dependencies should be explicit (using imports)
8. Transpile
   * Typescript
   * Elm
9. JS Should have automated build
   * Gulp
   * Grunt
   * NPM Scripts
     * Why NPM Scripts?
       * No extra layer of abstraction
       * No plugin dependence
       * Simpler Debugging
10. Use Libraries
11. JS Should Separate Concerns
    * UI
    * Data Access
    * Presentation
    > For some reason when we move to JavaScript we lose our minds
    * Context: People forget separation of concerns/structure. Everyhing gets smashed together.
12. You need a starter kit
    * Book: The Checklist Manifesto - Atol Gawande
    * Starter Kit = Automated Checklist
    * react-slingshot - His starter kit

bitnative.com/handouts

## Session 5: A Functional Workflow to Rule Them All

Reid Evans (reidevans.tech)

* 1 Data Type + 2 Functions
* Functional Programming - Programming with functions
* Determinism - for the same value you always get the same result
* Higher order functions - functions that take or return functions
* One Type F#
  ```F#
    type Either<'Left, 'Right> =
        | Left of 'Left
        | Right of 'Right
  ```
* C#
  ```C#
    class Either<Left, Right> {
        readonly Right
                 Left
                 bool
    ...
  ```
* These concepts apply regardless of the language
* Two types of functions
  * Functions that don't know about our type
  * Functions that know about our type
* Putting it all together
  * Map/Bind -> Helper functions that adapt between
  * tinyurl.com/bindthem -> Slides
* Railway Oriented Programming
* "Either" types return either an error code (Left) or the resulting value (Right). Subsequent method calls (or the caller)
  must handle the Either to process further
* reidev275 (GitHub) - Library "Either"

##Keynote 2: Harder & Better - Modern Dev Practices

Jessica Kerr (@jessitron)

* Pokemon Go is like development
  * "You can't catch them all"
* Lots of technologies
* As a team we can get all the knowledge we need to be successful
* Sociotechnical system
  * Team + Its Code
  
> I don't want rockstars on my team, I want my team to be rocking it.


