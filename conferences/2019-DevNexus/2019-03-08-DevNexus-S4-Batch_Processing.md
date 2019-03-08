# Batch Processing in 2019

  * Spring Cloud Data Flow
    * Job state stored in job repository
    * Tasks that can be run
    * Jobs
      * Integrates with the platform scheduler that you are running on
  * Spring Batch
    * Sample app is a standard Spring boot application
    * `@EnableTask` -> Bootstrap the Spring Cloud integration
    * `@EnableBatchProcessing` -> Setup the Spring batch tools
    * Job instances can only be run once for each set of parameters
    * Reader -> Returns a single item for each invocation
    * Processor -> Processes data passed to it
    * Writer -> Takes a list of items to write
    * Jobs consist of a series of steps