# Taming scary production code that nobody wants to touch

Mike Clement / blog.softwareontheside.com

  * What is Legacy Code?
    * Many opinions
      * A slang term for difficult-to-change code that we don't understand.
      * Legacy code is when people turn over faster than the code.
      * Code without tests is bad code.
    * Legacy code is scary production code that nobody wants to touch.
  * Risk
    * To mitigate risk... three questions:
      * What changes do we have to make?
      * How do we know we've done them correctly?
      * Does everything else work the way it previously worked?
  * Is it more important for the software system to work or is it more important for the software system to be easy to change?
  * How do we keep software "soft"?
  * Legacy code dilema
    * I can't change the code without tests in place
    * I can't put in tests without changing the code
  * Low risk refactoring
    * Refactoring -> Changing the structure of code without changing the variable
    * Code refactoring as CRUD
      * Create: Introduce/Extract
      * Read: performed by human no refactoring needed
      * Update:
      * Delete:
    * Use your tools. IDEs can help a lot with refactoring.
  * Preserving existing behavior is a big challenge
    * Strategies that don't work:
      * "Edit and pray"
        * Not the situation you want to be in.
      * "Working with care"
    * Better approach: "Cover and modify"
      * Cover with tests
      * Then modify
      * Characterization Test
        * Characterization: A description of the features
        * A means to protect existing behavior against unintended changes
          * Protecting behavior also includes bugs
          * Describes the actual behavior of the system
    * Approval Tests framework
      * Versions for multiple platforms
      * Compares output from your code with a known state
  * Seams
    * A seam is a place where you can alter or observe behavior in your program without editing in that place. 
  * Code coverage is necessarry but not sufficient to ensure your tests are good
  