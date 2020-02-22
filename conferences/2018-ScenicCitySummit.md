# Scenic City Summit 2018

 * August 17, 2018
 * Chattanooga Convention Center

## Day 1 (08/17/2018)

### Keynote: Patterns Exposed - Designing for the cloud

Michael Solberg / RedHat / Chief Architect South East

 * Trunk based development
 * istio -> Service Mesh
 * Getting to cloud ready (walk before you run)
  * Start with SDLC
  * Infrastructure is oriented to self-service
  * Automatic deployments & configuration
  * Deployment pipeline (CI/CD)
  * Deployment strategies (canary, blue-green)
  * Finally, rearchitecting apps
    * Containers
    * Microservices
    * etc
 
### Session 1: An Introduction to Object Capabilities or why Global Variables Suck

Emily Estes

* A capability - an authority to do something
* Without globals "dependency injection" is default (via parameters/constructors)
* Where do dependencies come from?
  * IoC Container 
  * App Startup
* Common idea: Trusted Core
* Rules
  1. all instance variables must be private
  2. no static (mutable) state
  3. no mutable state accessible across thread boundaries
* Linters like Joe-E (Java - old and not maintained anymore)
* Concepts outside of application
  * Containers
  * SE Linux
* Actor Model -> a model of distributed computing
  * Actor is a process
  * Each has a mailbox
  * Actors can send messages to mailboxes they have references to
* How can we use it?
  * Erlang (elixir, go, etc) provide it
  * Akka
  * Similar to calling a method
  * Smalltalk calls it sending a message to an object (Objective-C does as well)
  * Primary difference -> Actors send asynchronously
* What are forgeable references?
  * String containing path / url
  * Process ID in Linux
  * Pointer in C/C++
* Unforgeable references
  * File handle from OS
  * Object References (Java, C#, JS)
  * Erlang Process ID
* Capabilities in web services
  * OAuth Tokens
  * CSRF Tokens
  
### Session 2: React + MobX - Simple, scalable state management

[Andrew Steele](andrewthecreator.com) (@andrew565)

* React is a library not a framework
  * Primarily focused on the view
  * Built in state management is kind of 'clunky' and not enough
* MobX is an alternative state management framework
  * Alternative to redux
* Anything that can be derived from the application state should be
* Based off the observer pattern
* Process:
  * Define Model
  * Inject into view
  * Change the model
  * Auto updates view
* Observable State
  * @observer (ES7)
  * observer() (older)
* Computed Values
  * @computed
  * Derives values based on state
  * Recomputed automatically when state changes
* Actions 
  * @action
  * Changes state and triggers the observer functions and reactions
* Reactions
* realworld.io -> Comparison between different frontend tools
* MobX
  * Easy to learn
  * Less boilerplate
  * Full support for object-oriented or functional style
  * Nested data is easy
* Where does it suffer?
  * Too much freedom
  * Harder to debug
  * There might be a better option than redux or mobx (even with react)
  
### Session 3: Progressive Web Apps 101

Frances Coronel (@fvcproductions)
  * Front-end engineer @slack
  
* PWA - coined by two google engineers
* Bring the power of mobile apps to the web
* PWA Checklist
  * Fast - Quick to load
  * Integrated - Mimic native app experiences
  * Reliable - Offline first experiences
  * Engaging - Web Push Notifications
* 70% of people in emerging markets consider app size before downloading
* ~53% of people have access to internet worldwide
* Write once, deploy everywhere
* Most major companies are creating PWAs
* Downsides
  * No central hub
    * Must go directly to website.
    * no store for PWAs
  * Browser Support is mixed
  * PWAs on iOS are mote limited than on Android
* Lighthouse - open source tool to audit various website metrics
* Gatsby - static site generator buit on top of react

### Session 4: (Lunch Session) SKIPPED

### Session 5: Deep learning with Python

Douglas Starnes (@poweredbyaltnet)

* Artificial Intelligence
  * Mimic human behavior
* Machine learning
  * Throw a bunch of data at it and let the machine figure it out
* Deep learning
  * Subset of machine learning
* Neural Networks
  * Loosely based (inspired) by how the brain might possibly work
  * Node - value to be worked with (neuron)
* Deep neural network 
  * Has more than two layers
* Rows -> Observations
* Columns -> Features
* feature vector / indepdendent variables
* target / dependent variables
  * What we want to predict
* during training we don't care if our predictions are correct, but how close to correct they are
* Data set is split into training & test data set
* Tensor Flow
  * Pythong library for machine learning
  * Created by google
* MNIST -> handwritten numbers data set
* Keras
  * Also from Google
  * Higher level way to define networks
* Convolutional neural networks
  * Networks decide the important features to use
  
### Session 6: .NET Core Ubuntu

Jamie Phillips (@phillipsj73)

* .NET Core
  * Microsoft's new implementation
  * Cross platform support
    * One binary will run on linux, windows, mac
* Snaps
  * Containerized software
  * works on many distros
  * Using lxd
  * Highly isolated (explicit with permissions)
  * data is separate from app
* Dependencies are packages. Only need to install the Snap
* Snap is just YAML
  * Metadata
  * App
  * Parts > Plugins for building app
* 'snapcraft' is used to build snaps (snapcraft.io)

### Session 7: Javascript Testing

(Kyle Welch)[krwelch.com] (@kylewelch)

* Test is how it is meant to be used
* Focus on the critical path
  * Starting point
* Write tests for bugs you fix
* Jest -> JavaScript testing library by Facebook
* How
  * Arrange data you want to use
  * Act (ing) on a thing
  * Assert the value you expect
* Measure 
  * Jest can tell you code coverage for your apps
  
### Closing Keynote: The practice of being goalless

Reid Evans

* What is a goal?
  * Something you want to achieve
* A practice is what you do
* Outliers - the story of success
  * Malcom Gladwell
* Deliverate Practice
  * Focus on tasks outside your current competence and comfort 
> Experts are always made not born