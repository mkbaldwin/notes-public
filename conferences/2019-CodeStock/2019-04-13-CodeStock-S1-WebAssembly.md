# WebAssembly: The Browser _is_ Your OS

Jeremy Likness / Microsoft / @jeremylikness

  * Predecessors
    * asm.js
      * A strict subset of JavaScript that can be used as a low level target for compilers
      * Tool exists to convert LLVM bytecode to JS (emscripten)
  * Web Assembly (1.0 - 2017)
    * WASM is a binary format
    * Supported by the major (new) browsers
  * Blazor
    * Bridge between C# and WASM
    * Experimental
    * Project Type in Visual Studio (if you turn on experimental runtimes)
    * Interoperability between .NET libraries and JS       
    * Debugging isn't great right now
      * Lots of console out put
      * Still early, will be addressed in future releases.
      