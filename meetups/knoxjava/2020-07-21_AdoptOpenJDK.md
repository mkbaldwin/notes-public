# KnoxJava - AdoptOpenJDK

  * Hendrik Ebbers
    * @hendrikEbbers
    * github.com/hendrikebbers
  * George Adams
    * @gadams_
    * github.com/gadams

  * Moving to the eclipse foundation
  * Everything is done in the public and OpenSource
  * api.adoptopenjdk.net
    * Useful for automating downloading a version of a JDK
  * Large farm of servers to build and test various OpenJDK builds.
    * Many different platforms
    * SPARC ... ebay machine
  * Build and test environment in the cloud
    * Docker containers
    * Many builds/tests in parallel
    * Not all platforms work in docker (macOS, other things like Solaris)
  * Roadmap projects
    * Website redesign
    * jlink.online
      * website to build version of JDK with only the modules you need/want
      * uses the adoptopenjdk API
  * adoptopenjdk.net/slack
  * github.com/adoptopenjdk
  * One of the things that needs to happen moving to eclipse is getting a license for the Oracle TCK (octla?).
    * Once that happens all of the binaries will be tested and have to pass the TCK tests/compatibility. 
    * Not currently running the TCK, but confident in the test suite they already have.
  * Some stuff is happening on an ARM64 OpenJDK for Mac.
    * Not sure how long it will take to have a version.
    * JDK folks at Apple are currently working on some things.
    * Some features currently in OpenJDK depend on OpenGL.
      * OpenGL has been deprecated in macOS for a while, may be removed in ARM release.
      * Some work in OpenJDK to move to using Apple's own (metal?) APIs. 
    * OpenJDK was mentioned by Apple in a WWDC session.
  
  
