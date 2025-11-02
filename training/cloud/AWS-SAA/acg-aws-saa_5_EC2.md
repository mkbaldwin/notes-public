# EC2 (Elastic Compute Cloud)

## EC2 Overview

  * Essential part of the solutions architect exam.
  * Secure, resizable compute capacity in the cloud (virtual server).
  * Launched in 2006
  * Changed the economics of computing.
  * Provision resources in minutes not months.
  * Pay only for what you use.
  * Four pricing options:
    * On-demand
      * Pay by the hour (or second)
      * Flexible - low cost commitment for unknown amount of time
      * Short-Term - Unpredictable workloads, or known temporary need.
      * Testing the water - Applications being developed or tested for the first time on AWS
    * Reserved
      * Commitment to buy X amount of capacity and pay all up front.
      * Up to 75% off.
      * Predictable Usage - Application usage/need is steady and known
      * Specific Capacity Requirements
      * Pay up Front to get discount
      * Convertable Reserved Instances
        * Up to 54% off the on-demand price
        * Can change to a different instance type with equal or greater value.
      * Scheduled Reserved Instances
        * Match capacity reservation to a predictable recurring schedule
        * Workloads that only need a portion of a day
      * Operate at a regional level (cannot apply reservation to another region).
    * Spot
      * Purchase unused capacity at up to 90% discount
      * Price fluctuates based on demand.
      * Use Cases:
        * Applications that have flexible start and end times.
        * Applications that are cost sensitive.
        * Urgent need for large amounts of additional compute capacity.
      * Uptime is not guaranteed.
    * Dedicated
      * Physical EC2 dedicated for your use.
      * Most expensive option.
      * Why use these:
        * Compliance - Regulations that don't allow multi-tenant virtualization.
        * Licensing - Great for licensing that doesn't support multi-tenancy or cloud deployment.
        * Can be purchased on-demand or reserved.
  * Bootstrap Scripts
    * Script that runs at the time the EC2 instance first boots .
    * Can be used to install / configure service.
    * Increases boot time.
    * 

## IAM Roles

  * An entity you can create in IAM that has specific permissions.
  * Not associated specifically with one person, but can be assumed by anyone that needs it.
  * Roles are temporary
    * No long term credentials
    * Automatically given temporary credentials
  * Roles can be assumed by people or AWS services (e.g. EC2 instance)
  * Permission Policies can be attached to a role to define allowed access.
  * Roles are more secure than an access key and secret key. No credentials to steal since they are not stored on an instance.
  * Preferred option from a security perspective
  * Avoids hard-coding credentials
  * Uses policies to control permissions
  * Role policies can be updated and take immediate effect
  * Can attach and detach roles from running EC2 instances without a restart
  * **Always chose roles over storing credentials**

## Security Groups

  * Computers communicate using ports (using different numbers). 
  * Security Groups are virtual firewalls for EC2 instances
  * By default, everything is blocked.
  * IP Range 0.0.0.0/0 allows all traffic. Likely in production only open to HTTPS traffic on port 443.
  * 

