# CodeStock 2016

 * July 15 - 16, 2016
 * Knoxville Convention Center

## Day 1 (6/15/2016)

### Keynote

Cory House (@housecor)

> Why be in the mainstream? You can Google it.

> Everybody gets a COBOL book!

### Session 1: Security Vulnerabilities

Joe Kunk

 * Risk = Event Probability x Business Impact
 * Attacks tend to fall into a small number of categories
 * fireeye.com
 * Bring your own device (BYOD)
   * More Challenges for Security
 * Devices that can impersonate an open access point. Then capture all data then
   relay to the real device. Thus allowing someone to capture all traffic including
   SSL keys.
    * Mitigate with VPN client
 * Ransomware - Encrypt data and then hold the keys for ransom
   * getting much smarter
   * very dangerous
   * These are a business. Demand payment in BitCoin. Even have "customer support"
     to help people pay.
   * 3X more ransomware apps for mobile devices in the past year.
   * Recent offline backup (physical disconnect) are only real protection
 * Most attacks are random and not targeted at anyone specific
   * Throw it out and see who they catch
 * Attack types
   * SQL Injection
     * Most common
     * Easy fix
   * Cross site scripting (XSS)
   * Cross site request forgery (CSRF)

### Session 2: Responsive Frameworks Fine Print

Aaron Ladage (@aladage)

 * It took 3 years from the iPhone release to the advent of responsive
   * new learning curve
   * can't test all sizes
   * how to design for it?
   * performance is important for mobile
 * JQuery Mobile
 * Zurb (Zerb?)
 * Sencha
 * Ionic
 * Bootstrap - 2011
   * Built by twitter for use on internal Tools
 * Frameworks do ... well:
   * make getting started easier
   * rapid prototyping
   * consistent design language / coding style
   * provides a grid for you
 * The Bad:
   * Websites can look alike
     * customize defaults
   * The right tool for the job
     * Lots of stuff included might not be needed
     * Strip out what you don't need
   * Performance is key
     * 250ms slower/faster is the competitive advantage - Microsoft
     * Minify
     * Combine into one file
     * Don't override default styles, recompile from less
   * What happens if you redesign?
     * Bootstrap markup is all tied to visual layout
   * What if the framework changes?
     * Bootstrap has already done this with V3 and with some V4 stuff.
   * Leverage the preprocessor to create symantic markup that extends the Bootstrap classes
     * eg
     ```
       .article {
         @extend :col-xs-12
       }
     ```
   * Makes upgrading / moving away Easier
   * Be Framework Agnostic

### Session 3: Skipped for IOT Workshop

Losant IOT Platform

### Session 4: Take Back Project Sanity the Kanban Journey

David Neal (@reverentgeek)

>Kahn Bahn

Benefits
 * Visualize Work
 * Prioritize
 * Communication
 * Collaboration
 * Expectations

Originated with Toyota in the 1940s. - Decided to get into the car biz.

LEAN (Manufacturing)
 * Continuous Improvement (Kaizen)
 * Respect for people

 * SCRUM/XP - Late 90s
 * Agile Manifesto
 * Lean Software

 Cargo Cult
  * Doing things without understanding the reason behind it
  * Doing things you've observed other people Doing

KanBan
  * Japanese Word
  * Signal Card / Sign Board
  * A way of indicating capacity for more work.
  * A way to visualize Work
  * Work typically flows left to right
    * Backlog | Todo | Doing | Done
  * Doesn't tell you how to do your work. It is a visualization of our work.
  * Our brain can process pictures 60,000x faster than text.
  * Cards usually have lots of info
    * Identifier
    * Assigned Person
    * Flag for blockers
    * Time / Effort Estimates
  * Start with what you use now
    * Can be low tech "sticky notes" or Software
    * Board should match the way you currently do work. Don't change things up front.
  * Include all steps. Don't hide anything.
  * Next focus on flow
    * Where are the bottlenecks?
    * Where is it inefficient?
  * "Focus on the bataan not the runner"
    * Often the process is the problem not the people.
  > A bad system will beat a good person every time.

  * Track timing on each card
    * How long was it blocked?
    * When was it started?
    * When was it completed?
  * This can help to improve the process and track that it is getting better.
  * Limiting your SIP (work in progress)
  * Multitasking is bad
  > What is a highway at 100% utilization? A parking lot.

  * The more work in progress at once the more pain and potential problems delivering product.
  * We can become paralyzed with indecision.
  * Focus on less work. You can get more work done.
  * Place limits on the number of items in a category (e.g. "In Progress") at a time. Limits overworking people.
  * Cross team collaboration to aid in backlogs.
  * Expedite Lane -> High priority items that are the #1 goal. Everyone focuses on getting this done.
  > Pull a number our of my rear end and add 20%

  * Once you are collecting metrics you can experiment with improvements then know what impact they have.
  * leankit.com/learn/kanban
    * Simple steps to start with KanBan
  * Book: Personal Kanban
  * Can you be applied to any process. Not just software.
  * Set List
    * Visualize work
    * Pursue incremental improvements
  * Slides are on slideshare.net

## Day 2 (6/16/2016)

### Session 1: Angular 2 w/Typescript

@JeremyLikness

  * Angular CLI
    * Rapid scaffolding of projects
  * Angular
    * Declarative vs Imperative
    * data-binding
    * Dependency Injection
    * Designed with testinf from the ground up
  * Why Andular 2?
    * Smaller footprint (45k smaller)
    * Improved Performance
    * Server side (nodejs) rendering
      * Angular Universal
    * Great CSS Management
    * TypeScript

### Session 2: Cross platform apps with Electron

David Neal

  * Cross platform desktop apps
  * .NET + Mono + Xamarin
    * Pros:
      * Shared core .NET code
    * Cons:
      * Xamarin Mac != Xamarin Mobile
      * Native UI is hard
      * Deployment
        * Mono is required for OS X
  * Electron
    * Pros:
      * HTML/CSS/JS
        * Familiar tool set
        * Node.js + Chrome
      * No deployment dependencies
        * All required assets bundled with the app
      * No cross browser problems
    * Cons:
      * HTML/CSS/JS :-|
    * Created by GitHub for Atom
      * Previously Atom Shell
      * Existed since 2013
      * 1.0 release May 2016
      * Frequent updates
    * Features
      * Rapid development
      * Can use any front end tech
        * Angular/React/etc
      * Themes - easy to create with css
      * Shared Code / UI with traditional web apps
      * Deployment + "Silent Updates"
      * Extends Node + Chrome to include native UX
        * Notifications
        * Printing
        * etc
    * Why desktop apps?
      * Offline
      * Access to printers, drivers, etc
      * On premises apps
      * Edit/access local files
      * Kiosk
      * App store
      * "It just feels right"
    * Examples
      * Atom
      * Slack
      * Wagon (SQL Editor)
      * Nylas N1 (email client)
      * Speak (Desktop Sharing / Video Conferences)
      * Jibo (robot)
    * Getting started
      * Requires nodejs
        * `npm install electron-prebuilt`
    * Process (main.js NodeJS)
      * Main starting point
    * Renderer (index.js)
      * One or more chrome (stripped down) instance
    * to run: `electron main.js`
    * In HTML script tags or in other JS code you have full nodejs access.
    * Have access to local information
      * user home
      * file system
    * Most ES6 support. Uses the latet chrome engine.
    * Use any front end JS/CSS Tools
    * Chrome Developers Built In
    * Reactor App - In speakers github repo
    * Modules
      * app - Environment info
      * ipc - Communication from renderers
      * dialog - File open / print / etc
      * menu
      * power-monitor
      * etc
    * Renderer Modules
      * ipc, remote, web-frame
      * Chrome instance is not sandboxed
      * Web frame content is sandboxed (safe for external content)
    * other
      * clipboard
      * crash-reporter
    * Recommended Tools
      * electron-debug - enable chrome dev tools in the deployed application
      * electron-reload - auto reload for dev
      * electron-packager - create stand alone app
      * electron-builder - create an installer
      * electron-updater - simplify update process
      * electron-mocha - TDD tool
    * Devtron
      * Chrome deve tools plugin
      * Adds additional electron specific debug tools
      * Helpful Linter
    * Spectron
      * Electron testing framework
    * Bolierplate projects
      * electron-boilerplate
      * electron-react-boilerplate
    * electron-prebuilt-compile
      * Replacement for electron-prebuilt
      * Understands Typescript/CoffeeScript
      * ES6/ES7 (babel)
      * less
      * reactjs
    *  PhotonKit
      * CSS UI Framework
      * Looks very OS X Styles
    * Building for windows
      * Win 7 / Server 2008 +
      * VS 2015 Community
      * Python 2.7
      * NodeJS
      * Git
    * Building for Mac
      * OS X 10.8+
      * XCode 5.1+
      * NodeJS
      * pyobjc (if using python from homebrew)
    * Building for Linux
      * Python 2.7
      * NodeJS
      * clang 3.4+
    * Tips
      * Use css default cursor for all elements
      * `-webkit-user-drag: none`
      * `-webkit-user-drag: text`
      * Keep windows open
    * Local Storage
      * Read/Write JSON file
        * fs-jetpack
      * nedb -> similar to mongodb
      * pouchdb -> couchdb in JS
      * Relational DB
        * seriate (for mysql)
        * Drivers available for major DBs
          * pg
          * mysql
          * oracle
      * awesome-electron (github)
        * Detailed list of resources
      * Pluralsight - electron playbook
      * electron.atom.io


  * 2 hard problems in development
    * Cache invalidation
    * Naming things
    * Off-by-one errors

### Session 3: Lightning Talks

#### Talk: ???

  * 70% - 80% of custom software projects are abandoned, late, or overbudget
  * Challenges
    * Users like the status quo
    * Differences in Expectations
    * Over/Under Engineered Software

#### Talk: Hand drawn slides for presentations

David Neal

  * Tools
    * IPad Pro with Pencil
    * Regular iPad and stylus
  * Visual information is important in passing on information
  * Telling stories with pictures is the most effective way to do so
  * You can express the exact message you want. Unique.
  * Start with Why
    * Why to use something is more important than examples
  * Show & Tell - Dan Roam

### Session 4: Building Secure Apps from the Ground Up

Jared Smith (@JaredTheCoder)

  * informationisbeautiful.net
  * Compromise is inevitable
    * We all make mistakes
    * Non public unknown bugs
    * probably won't know you've been breached for a long time
  * Security Domains
    * Web
    * Networks
    * Mobile
    * Vehicle
    * IoT
    * Embedded
  * Security through obscurity - False Security
  * Security by default (by design)
    * Think about how you could be attacked
      * Think like a hacker
    * Design from the ground up with security in mind
    * Have a security team
      * Even if one person
    * Never Do:
      * Missing authentication on checkout
      * No hard coded password / credentials to version control
      * Sending sensitive data without end-to-end encryption
    * Attacking is a process
      * Reconnaissance
      * Develop vulnerability hypothesis
      * Test vulnerability hypothesis
      * Develop exploit
      * Profit?

### Session 5: Eloquent Code

  * SOLID
  * Single responsibility principle
    * each class should do one thing
  * Interface segregation principle
    * No client should be forced to...
  * Dependency Inversion
    * Rely on interfaces not concrete implementations
  * Write code to be read by humans
  * Write more declarative code
  * Don't make me execute code
    * I'm a bad computer
  * Don't copy code -> Think
  * Use informative names
    * Naming is hard. Don't get stuck.
