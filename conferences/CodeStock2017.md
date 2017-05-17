# CodeStock 2017

## Day 1 (5/5/2017)

### Keynote: The Silver Bullet Syndrome
Hadi Hariri (@hhariri)

> As a developer
> I want to create a framework
> So that I don't have to talk to anyone

> Do you know how to tell if a program is written in F#? They'll tell you so.

### Session 1: Becoming a Social Developer
Jeremy Clark (@JeremyBytes)

Phone = "Magic device" - Creates a "force field" and people won't talk to you.

Introvert - derive energy internally
Extrovert - derive energy externally (from others)

Not related to being shy or outgoing.

Book - Quiet: The power of introverts in a world that can't stop talking. by Susan Cain

Developers love to talk but they don't like to start the conversation.

Fear...
 * of the unknown
 * of rejection
 * of failure

Steps:
  0. Spot a conversation
  1. Join the circle (listening)
  2. Exploratory Comment
  3. Active part of the conversation

Simple and terrifying
 - Hi I'm &lt;insert name>
 - What do you do?
 - What kinds of technology do you use?

You've just given permission to talk to you.

> We want to learn.

Tips
 * Turn off your force field
 * A laptop is an invisibility cloak
 * Help others skip the awkwardness, invite them into the conversation.
 * Buffet Line =
   * Captive Audience
   * Short Term Commitment
   * 3rd thing in common (food)
 * Look for tables with people sitting apart. "Complete the Triangle"
 * You never know who you are going to meet.

### Session 2: Becoming a Geek Leader
John Rouda (@johnrouda)

Simon Sinek - Ted Talk

Motivation
 * Autonomy
 * Mastry
 * Purpose

Types of bosses
 * Ignoring Boss
 * Critical Boss
 * Praising Boss
   * Praising just 10% of successes improves morale/performance significantly

 * Be world class -> Keep current
 * Take Responsibility
 * See the big picture
 * All about relationships
 * No excuses
 * Give the extra 1%
 * Cooperate

Tips for difficult conversations
 * Be authentic/real
 * Be direct
 * Be unapologetic

> Leadership is not overnight

Imposter Syndrome - Normal to feel unqualified

Book: Notes to a software team lead

### Session 3: Becoming a pro at git
Chris Keathley (@chriskeathley) keathley.io

> git is like clown shoes

Git's golden rule => **Don't panic**
 * If you don't panic you can fix 100% of problems.

Git CLI is the most important tool.

On the vi/emacs war...
> I don't know who the winner is, but I know who the loser is and its all of us.

Aliases for common tasks help.

 * diff-so-fancy - Better command line diff utilities
 * hib - Better command line operations for github.

Git Scripts
 * Custom shell scripts that can be run by git.
 * Named: git-something
 * Run as: git something

bisect - Give it a known good commit and a bad commit. Checks out the one in the middle. Then mark as good or bad. Finds the new middle for you.
 * Sounds cool if you have good unit tests.

bisect can take a script to test for the bug

 * Only work swhen your git history is clean
 * Commits should be small, complete
 * Simple branching strategy is best

rebase - Realigns the head of the current branch to the tail of master

git checkout -
 * Take be back to the last thing I was on.

Interactive Stage - Walks you through doing some types of operations

Interactive Rebase - Walks you through reordering/splitting/squashing commits.

reflog - all of the repo history (for some period of time)

speakerdeck.com/keathley

### Session 4: Taking a byte of Java Bytecode
Magnus Stahre (@magnusstahre)

synalize it - binary file viewer

First 4 (magic) bytes -> CA FE BA BE

Followed by minor version (2 byte) major version (2 byte)

All constant values are stored together in a "pool" shared throughout the entire class.

javap - output metadata about a class

asm - tool to manipulate/view Java classes.

## Day 2 (5/6/2017)

### Session 1: Agile Architecture
Steve Green (@stevepgreenkc)

> If its work we try to do less. If its art we try to do more. - Seth Godin

There is a notion tha architecture is beyond programming.

Architecture is no longer a prerequisite
 * Speed to Market -> Pressure to deliver fast
 * Advanced Tooling -> Tools make doing the right thing easy
 * Lower Barriers -> Focused on delivery
 * Continuous Delivery -> Easy to change / deploy software

**Agile Misnomers**

Working Software > Documentation - Business people read as "no documentation"

Agile team roles do not include architect. Everyone is responsible for architecture.

Business wants features not architecture.

External Quality
 * Good UX
 * Few Defects

Internal Quality
 * Good Design

The business things external quality is the only important thing.

"The Design Stamina Hypothesis" - Martin Fowler

Bad architecture builds quietly over time unitl it becomes unmanagable.

"Query of Despair" - Daily WTF

Indicators of good design
 * Delivery
 * Change - Can we handle change?
 * Complexity - Cam we handle complex challenges?

Requirements - What should be built?
Architecture - How should it be built?

All developers are architects because they decide the how on many things.

Scrum roles don't include a business analyst.

 * Code is our blueprint
 * Compiling is our construction

Coding is like building a house? **WRONG**
 * All developers are not interchangable.
 * Dangerous for business to think this way.

What is the role of a software developer?

We don't just tell the compuer what to do. We tell other developers what we want the computer to do. **Clean code matters.**

**Building software is like writing a book**
 * Outline
 * Write (rough draft)
 * Revise
 * Review (get feedback from others)
 * Release

Coding is an art form.

Architecture is the stuff that's hard to change. - Martin Fowler
 * The stuff we need to get right

>Great developers remove architecture

Good developers remove things that are hard to change.

Good design allows us to defer complex decisions.

Design is driven by use cases.

Diagrams are still important.
 * but they get out of date easily
 * Generating diagrams helps

Emergent Design - start small and emerge the design as you go

Horizontal slicing
 * Specialists build each piece (they only know their part)
 * Integration at the end
 * Slow feedback loop with the business
 * No possibility to experiment (can't evolve to new technology)

Vertical Slices
 * Broken down by features
 * Each slice can meet the definition of done
 * Faster feedback loop
 * Easier to evolve
 * Easier to estimate
 * Scrum meetings work better

> Estimation is the hardest thing we do.

Guiding principals
 * Think big
 * Act small
 * Fail Fast
 * Learn Rapidly

Build an "architectural runway"
 * Dedicated backlog for architecture
 * Helps communicate design vision

Roles of an Architect
 * Must be involved in the solution
   * Must be in the code
   * Avoid the "Ivory Tower"

The structure of the team dictates the deam building it.
 * Accountability -> Those making technical decisions have to live with them
 * Collaboration -> Encourages everyone to engage in architectural thinking.

"Architecture is social" we have to talk about it.

Architects are the guides.

Stay in the trenches. Take the theoretical to the practical.

Mob Code Reviews
 * Everyone gets together to discuss the code
 * Something you are:
   * Proud of
   * Ashamed of
 * Talk about why you did that and about solutions.
 * Everyone has reviewed the code first
 * Avoid mundane stuff
 * Encourage an atmosphere to celebrate code

Is it easy to do the right thing?

"Don't starve opportunities and feed problems"
 * Most experienced get the hard problems
 * New stuff gets left to the less experienced.
 * This is bad

 1. Make sure architectural thinking happens
 2. Make change the new norm
 3. work to master simplicity

### Session 2: Introduction to forensic analysis
Jared Smith (@jaredthecoder)

>Security Incidents are Inveitable

Computer Forensics
 * User behavioral analysis
 * Network analysis
 * Memory forensics

 * IOC - Indicators of Compromise
 * Examining memory for anomolies
 * Capturing logs can miss key insights
 * Manual inspections are often needed.

Tools
 * Autopsy
 * Sleuth Kit
 * Rekall - Analyze memory images
 * GRR - Automation tool for Rekall
 * Volatility - Volatile memory extraction utility framework.

Volatility will be used for this talk
 * Takes dumps from many OSes
 * Extracts system state

Process
 * Pre infected memory sample (baseline)
 * Post infected memory sample
 * Analysis

Strings utility - dump human readable strings from binary file

virustotal.com

### Session 3: Examples of Microservice Architectures
Barry Stahl (@bstahl)

Build microservices at the level you want to deploy independently.

Build at the level you ened to scale independently.

User correlation IDs to track requests across services.

Pay close attention to failure management.

12factor.net - Must read for microservices.

### Session 4: JavaScript Level Up
Lee Brandt (@leebrandt)

IIFE - Immediately Invoked Function Expression

Prototypical Inheritance
 * Instances link back to the parent prototype
 * If a method doesn't exist on the object it calls the next one up the protype chain
 * Shadowing - A child using the same method name of the parent hides it from being accessed
   * No 'super' to access items in the prototype
 * Prototyped Delegation

This discussion is about the ES5 way of doing modules
 * AMD Modules (require.js)
 * Common JS
   * FirstModule.js
     * module.exports = ...
   * OtherFile.js
     * require('./FirstModule');

Anonymous Functions (i.e. functions without a name) are a bad practice. Makes debugging harder.

Asynchronicity
 * Callbacks
   * Callback Hell - Chained callbacks can be hard to manage
 * Promises
   * ES6 includes this
   * q library in Angular
   * others?

>If an error occurs in a catch I don't know what you are going to do... write better code.

Quirks
 * 'this' keyword refers to the context where the functionwas called from

Kyle Simpson - Books about JS

Javascript is compiled just-in-time. Two Phases:
 * Compile
   * In global scopr find all vars and set aside memory
 * Execute
   * Values are assigned to the allocated
   * If a variable isn't defined global scope creates it for you
     * Bad
     * Use strict prevents this

Functions are 'hoisted' to the global scope and therefore can be called before it is declared. Unless you assign the function to a variable.

Revealing module pattern - allows for simulating private variables.

Name Spacing
 * Prevent global scope bleed
 * Prevent name collisions
 * Create a JS object and hang everything off of it.

Tips
 * Always 'use strict'
   * On by default in ES6
 * Use === instead of ==
 * Pick a module pattern and use it
 * Use namespacing for libraries

=== vs ==
  * `==` Performs type coercion automatically `1 == '1'` returns true
  * `===` Doesn't perform coercion (returns truthy or falsy)

truthy/falsy - 0, undefined are falsy

### Session 5: The war is over and JavaScript has won: living under the JS regime
Matt Honeycutt (@matthoneycutt)

ES6
 * 'let' keyword
   * Prevents hoisting of variables
   * Scoped even in nested functions (more like you would expect)
 * 'const'
   * Cannot be reassigned
 * Arrow functions r => () {}
   * Inside 'this' actually refers to the declaring class not the caller like normal callback functions.
   * Now have template strings. 'something ${x}'

Promises API helps structure code. No more nested callbacks.

'async' keyword

```
async function X() {
  let result = await doStuff();
}
```

Calling X returns a promise. The promise then receives the returned value.

Classes are now supported.

```
class X extends A {  //Real inheritance
  constructor(name) {  //Constructor
    super(); //Call parent constructor
  }
}
```

This is mostly syntactic sugar. Underneath the implementation is similar to before.

Generators (need to read more on this)

```
* getSomething() {
  while(true) {
    yield something();
  }
}
```

The star tells us a function is a generator.

Yield returns a value from the generator.

lodash library
 * adds a bunch of useful functions similar to the Java Streams API
 * Modern JavaScript has some of this but not quite as good yet.

> A lof of what's wrong with JavaScript is when it tries to be helpful and make your code work when it shouldn't.

Still need a transpiler to use much of the new ES6 stuff (babel can do this).

aurelia - Front end framework
 * aurelia has a commandline tool to walk you through a project setup process.
 * Generated classes will use modern js classes/etc or typescript depending on the selection
 * VSCode debugger works automatically with this framework
   * Wonder how to det this up for other things or if Intellij/Webstorm can do this too.

Black belt techniques
 * Javascript quirks
   * Learn to ignore
   * Learn to deal with it
