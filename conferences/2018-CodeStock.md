# CodeStock 2018

 * April 20 - 21, 2018
 * Knoxville Convention Center

## Day 1 (04/20/2018)

### Keynote: Paige Bailey (@DynamicWebPaige)

Magenta - AI music/art

### Session 1: CSS Can you? !== Should You?

Alice Brosey (@ambroseya)

> For every project there is a fine line between the role of CSS and JavaScript

* CSS Negatives
  * "Different" to debug
  * Mistake cascades through app
* JS Negatives
  * May have overly complex dependencies
  * One bug can break the entire app
  * May lead to too little separation of concerns
* CSS Positives
  * Fewer Dependencies
  * Better Performance??
  * "separate the clothes from the body"
  * No DOM manipulation
* JavaScript Positives
  * Debugging - easier??
  * Easier to test
  * Performance - maybe depending on framework
* Most people use big JS frameworks out of habit
* Giana Blantin (sp?) -> Does lots of CSS stuff 
* CSS Everyone Needs
  * Calculations
    * calc()
    * IE 10+
  * Flexbox
    * Polyfill needed for IE 10
  * CSS Grid Layout
    * Flexbox + CSS Grid pair well
  * Viewport Units (vh, vw, vmin, vmax)
    * vh, vw - Always based on screen size
  * Media Queries
    * scale based on width / height of screen size
  * Selectors and pseudoselectors (pre CSS3)
    * not, required, etc aren't well known/used
  * Animation (mostly back to IE 10)
  * Filter
    * grayscale, hue-rotate, blur, etc

alicebrosey.com

### Session 2: Write Cleaner JavaScript Today

Tyler Jennings (@jenningstcj)

* Cognitive load
  * How much can be kept in your mind at one time
* ES 6 new constructs
* use `let` & `const` over `var`
* map
  * `array.map({x => x*2})`
* ternary
* String templates ${myvar}
* Arrow Functions
  * Can write single line expressions
  * `const doSomething = () => statement;`
  * declarations aren't "hoisted" to the top of the file
  * `() => console.log("~") || someExpression`
  * `() => ({x: 'x'})`
    * Arrow function returning JSON
* Destructuring
  * `...` "rest" operator pulls remaining object properties from another object
  * can do destructuring with arrays
  * shorthand properties
* Spread Operator
  * `console.log(...[1,2,3])` = 1 2 3
* Proposed pipe operator (`|>`) 
  * Not valid today, how to simulate?
  * Custom function
```javascript
Take("xyz")
  .map(func)
  .map(func2)
  .result();
```

### Session 3: Ex Nihlo ... Why it's ok to throw code away.

(Paraphrased title from memory)

Rob Scott

* Sunk cost fallacy - keeping it because "we've already invested in it"
* Principles
  * Domain Driven
  * Simple - don't anticipate complexity
  * Loosley Coupled
  * Robust
  
### Session 4 - Going Fast: The art of delivering quality software quickly

Josh Carroll @jwcarroll

> We are too focused too much on small problems not the whole system

* Value Stream - concept to cash
  * How long does it take from idea to production
* Thinking differently
* Why release in batches?
  * inefficiencies
  * state transitions that are difficult
  * avoiding pain
* How do we get to production faster without breaking it?
* If something is hard, do it more often
> No feature survives contact with the user
* Solutions
  * Rapid prototyping
    * Paper drawing, mockup, etc
  * Minimum viable feature
    * Smallest piece of the feature that can provide value to the users
  * Alpha/Beta testing
  * Planning problems
    * over engineering
    * analysis paralysis
* Reasons
  * Psychological, infrastructure, institutional
  * engineers love challenges
  * rigid infrastructure
  * culture of blame
* Solutions
  * Planning on-demand (Close to the request)
  * Long term themes
  * Stack rank backlog
  * Bias toward action (experiment and ship products)
* Coding problems
  * Long lived feature branches
  * Infrequent checkins
  * Always "almost done"
* Reasons
  * Merging is difficult
  * Features are too big
  * Ego driven development
* Solutions
  * Tasks <= 1 day
  * Top tasks are always up for grabs
  * Pair Programming / Code Reviews
  * Feature Toggles
    * Allow shipping partial features
  * Branch by abstraction 
* Devs should own outcomes not features
* No backlog cherry picking
* Automate code style/linting
* Poor Quality 
  * No quality standards
  * unrealistic deadlines/pressure
  * poor coaching/mentoring
  * "Not created here"
    * "creating a custom solution when something already exists"
* Foster a culture of research
* Educate devs to the cost of their time
* "Cult of reuse"
  * All projects reference common/core
  * Unnecessary layers of abstraction
* Myth of code reuse
  * creates brittle architecture
  * Monolithic
  * increases cognitive load
  * increases development time
* Rewrite solutions often
  * frees you from tech lockin
  * repitition makes you efficient
  * creates deep domain knowledge
* Treat common libraries like 3rd party (strict packaging)
* build quality in
* everyone owns quality
* devs write tests/specs
* automate testing / quality checks
* automate everything
  * CI to validate checkins
  * automated tests
  * automate configuration & setup
* Deployment problems
  * Scheduled deployments
  * Arbitrary time boundaries
  * Requires a team
  * Botched deployments
> Every checkin should be ready to be deployed to production or a staging environment
* User acceptance problems
  * delayed feedback
  * Don't know how feature will actually be used
* Solutions
  * constant user feedback
  * live alpha/beta testing
  * proactive monitoring
    * identify problems before users complain
* know your real process
  * find places to identify waste
  * automate everything else

## Day 2 (04/21/2018)

### Session 1: ...