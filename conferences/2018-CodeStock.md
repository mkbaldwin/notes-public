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

### Session 1: Machine learning 101 with Python and Scikit-learn

Jared Smith

* You can teach computers to do tasks for which they can create models
* Neural networks date back to 1943
* GANs
  * Generative Adverserial Networks
  * Two models train each other
* Categories of ML
  * Supervised Learning
    * uses labeled data
  * Unsupervised learning
    * no labels
  * Semi-supervised learning
    * Mix of supervised and unsupervised
  * Reinforcement Learning
    * Optimize Learning
  * Deep Learning
* Supervised Learning
  * Data with labels + similar data -> similar data with labels
  * Classification
  * Regression
* Unsupervised Learning
  * ML(data w/o labels) -> unlabeled groupings of data
  * clustering
* Semisupervised
  * ML(large data w/labels, small data w/o labels) -> better unlabeled groupings of data
* ML Workflow
  1. Gather Data
  2. Preprocessing
      * Clean Data
      * Format Data
      * Transform Data (if needed)
  3. Feature Engineering (if supervised)
  4. Train the model
  5. Test/validate
* Data in scikit-learn
  * work with data via numpy library
  * just using matrices
* Estimators
  * Things that can build and fit data
  * can be classifiers, regressors, etc
* Predictors
  * called to get new labels for unlabeled data
  * or fitting unlabeled data
* Transformers
  * cleanup/preprocess data
  * Extract features from data
  * Reduce number of dimensions
* Alternatives
  * Tensor flow
  * NLTK
  * Keras
  * Caffe (C++)
  * OpenCV (C++)
* Anaconda Installer
  * Scientific installer for python
* Jupyter lab
* Jupyter Notebooks

### Session 2: DSLs for fun and profit

Daniel Oliver (@a_software_dev)

* DSLs
  * Only express a business domain
* Building a language
  * Grammar
  * AST (Abstract Syntax Tree)
  * Lexer
  * Parser
  * Interpreter
* Grammar
  * Bakus-Naur Form (BNF)
    * EBNF
* Abstract Syntax Tree
  * Data structure a language is represented by
  * All languages are fancy data structures
  * Convenient to validate and transform a language by
* Lexer & Parser
  * "Lexical Analysis" analyze and assign meaning
  * recursive descent parser
  * base words and symbols are called a lexeme (or token)
  * Parsers aren't' huge complicated things
  * RDP - Recursive descent processor
    * Each lexeme from the lexer is processed one at a time
* Interpreter
  * Do something
    * Read language
    * Generate AST
    * Validate/Transform AST
    * Output/Perform Result

### Session 3: The developers guide to learning effectively

Arthur Doler (@arthurdoler)

* Experience vs education
* How do we change our "theory of action"
  * Slight improvement through doing
* Single loop learning
  * we have a theory of action
    * Do an action
    * get results
  * Loop through this
* Double loop learning
  * When we let our results change our theory of action (in double loop style)
* be able to describe your theories
* What is a skill?
  * A measure of your ability to behave in a particular way
* Types of knowledge
  * Explicit 
    * Easy to be articulated
  * Tacit
    * Only gained through experience
    * Not easily articulated
  * Implicit
    * Between the others
    * Can be articulated but its hard
* Keep learning loops short (distance between cause/affect)
* Keep an open mind and explore
  * be surprised ... it helps you remember
* Seek guided learning
  * find a mentor
  * listen to other people
* "Mylenation"
  * Makes nerves go faster
  * The more you use a nerve the more it happens
  * Helpe you learn faster
* Brain has "two systems"
  * Unsonscious fast learning
  * Conscious logical processing
* "burn your comfort zone"
* Chase effort and discomfort
  * Know what mental effor feels like for you
  * Context switch for a quick reset
* Destroy your fear of loss or change
* "Ask why?"
* Use as many parts of the brain as possible when learning
  * write down
  * draw
  * fidget/move
  * varied kinds of input
* Lessons can be learned anywhere
* teach others
  * talking about or teaching a topic helps you learn better
* blog
* give a talk
* have to be good at know how to learn AND what we should learn

### Session 4: Serverless - Bootstrap globally in minutes for pennies

Andy Cowell

* Serverless can be
  * a philosophy
  * general technology
  * a company making a product 
    * not talking about this one
* Philosophy
  * buy don't build
  * use the cloud
  * keep things small - microservice
  * build and use apis
  * event driven programming
* The Technology
  * Functions as a Service "FaaS"
    * Subset of PaaS
  * Pay only for what you use
* Talk is about AWS lambda
* Can do FaaS on Kubernetes (OpenFaaS)
* Not a silver bullet
* Not for...
  * heavyweight services
  * long-ruinning jobs
  * high performance
* can have multiple functions, tell AWS which one to call
* Two paramters
  * Event - our input
  * Context - info about the runtime environment
* Return value is sent to the caller
* Limitations to AWS Lambda
  * 5 minutes runtime maximum
  * 3GB RAM maximum
  * No state preservations between incovations
  * Cold start penalty - initial startup cost
* Advantages
  * No environment to manage
  * Automatic scale out
  * Cheap
    * Amount of time running * memory used to determine cost
  * Low cold start penalty for languages like python
  * Get started quickly
* Supported Languages
  * JavaScript/Node
  * Java 8
  * Python
  * C#
  * Go
* Port activated on command
* Container handled for you
* Code downloaded from S3
* Serverless websites
  * S3 bucket used to host website static content
  * github.com/vt102/s3-static-site
* AWS Chalice
  

