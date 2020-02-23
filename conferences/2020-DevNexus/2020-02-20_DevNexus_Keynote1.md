# DevNexus 2020 - Day 1

February 20, 2020 - Atlanta, GA

## Opening

  * 2400 attedees, biggest DevNexus ever
  * 25 years of Java
  * Duke!

## Keynote 1: Dueling Banjos

  * Ray Tsang, Google Cloud - @saturnism 
  * Burr Sutter, Red Hat - @burrsutter


  * Google created Kubernetes in 2014
  * RedHat created Open Shift in 2015 (based on Kubernetes)
  * Redhat is a primary contributer to the Java support in VS Code
  * Quarkus / OpenShift (Burr)
    * Java microservice framework
    * Quarkus has support for GraalVM
    * Build small optimized binary executable containing everthing needed to run the app, but not the unneeded things.
    * Super fast startup (great for containers)
    * Plugin for Quarkus (maven/gradle) to automatically build your kubernetes/docker files for you.
    * Knative
      * Looks for activity, and dynamically scales the infrastructure based on load
      * Can be based on HTTP traffic, messages, etc.
      * Automatically scales up/down based on demand
  * Spring Boot / GCP (Ray)
    * "Friends don't let friends write docker files"
    * Google Jib Plugin
      * Creates your docker files for you
    * Istio - Service Mesh
      * Can automatically instrument the application to know latency, connections, etc.
    * Kiali 
      * Provides visibility into how traffic is flowing in the cluster
      * Manage and controll traffic flow
    