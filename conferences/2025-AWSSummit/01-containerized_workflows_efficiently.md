# Running containerized workflows efficiently on AWS.

* Why graviton (arm64)
  * Best price to performance ratio in EC2 for a broad array of workloads
  * Consume about 60% less energy
* Customer example
  * From Samsung...
    * Saw a 15% cost savings
    * Median average saw 5.6% increase, but 90th percentile saw up to 48% latencey improvement
* Can be used with:
  * EC2 (not containers)
  * ECS
  * EKS
  * Lambda
* Building images for Graviton
  * Everything in your stack needs to be compatible with arm64
  * Complexity of migration depends on programming language
    * Java is low effort to migrate
    * Not all interpreted languages are easy. Python or Node can be medium complexity. 
      * You might not be able to get arm versions of some libraries that use natively compiled (C/C++) code
    * No mention of .NET, probably because containerizing even on x86 will be problematic for many peopled
* Porting advisor is a tool that can help analyize for porting issues
* Building images
  * Build on a mative arm platform (Mac Mx series CPUs)
  * Emulated builds using docker buildx on x86_64 using qemu
  * Generally no major difference in the Dockerfile, but difference in how you build
  * All your image layers must be arm compatible
* Fargate is the easiest way to use Graviton with ECS
  * Simply set the parameter for CPU architecture
* You can pin a container to run on Graviton or x86
* EKS fully supports graviton
  * Cluster can contain container instances in multiple architectures
  * All of the usual tools still work
* Spot instances
  * Fargate supports fargate spot instances
    * price is lower when there ie excess capacity
    * can be reclaimed with 2 minute warning notification
    * price could be different depending on demand for a particular architecture
      * containers built for multiple architectures can use whichever is cheaper
    * You can have automatic termination of load balancer connections so users don't get routed to the container being terminated. 
    * You cal also to other things with the event
  * Measuring ontainers
    * AWS Lambda Power Tuning (on github)
      * toolkit (open source) for measuring performance results and comparing between CPU architectures
* Multi-architecture pipelines
  * Thousands of grativon compatible images are already available (nginx, httpd, dbs, etc)
    * Nothing you have to do other than change the image being used
  * Custom image (compiled code)
    * installing software already built for the base OS
  * Can build the image for multiple architectures and publish to the usual container repositories
  * Using buildx for docker is 20x slower than creating the image
  * Better to have two build hosts, one for each platform, then do the manifest creation on one of the nodes.