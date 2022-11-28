# Fundamental Cloud Concepts for AWS

## Understanding Cloud Computing

  * Traditional Data Centers
    * Forecasting demand is difficult.
    * Large investment
    * Slow to deploy
    * Expensive to Maintain
    * Own all security burden
  * Cloud benefits
    * Capital expense (up front) traded for variable monthly expense
    * Benefit from economies of scale
    * Stop guessing capacity
    * Increased speed & agility
    * No data center to maintain
    * Go global in minutes
  * Elasticity - Ability to acquire resources when needed & release automatically
  * Reliability - A solution's ability to provide its functionality when needed
  * Agility
    * Lowers the cost  of trying new things
    * Less time maintaining infrastructure
    * Access to emerging technologies
  * Types of Cloud Computing
    * Cloud Computing - on demand delivery of compute power / resources
    * Cloud Computing Models
```
Max Control                                  Min Maintenance
       |----------------------|---------------------|
     (IaaS)                 (PaaS)                (SaaS)
Infrastructure as         Platform as           Software as 
    a service              a service             a service
```
  * Deployment Models
    * Public Cloud - AWS, GCP, Azure
    * Private Cloud - Cloud like features in a private data center
    * Hybrid - Using both public/private cloud together

## AWS Global Infrastructure

  * AWS Regions
    * Specific geographic location
    * Cluster of data centers working together
    * Currently, 22 regions, 5 more announced
    * 4 public regions in the US
    * 2 GovCloud regions
  * Availability Zone (AZ)
    * One or more data centers
    * Each region has multiple AZs
    * Redundant power / networking
    * 69 AZs
  * Highly available apps have no single point of failure
  * Region and zone naming
  * AZ Name:
```
Region Name
/-------\
us-east-2a
-- ---- ||
|  |    |\ AZ
|  |    \ Region #
|  \ Subarea
\ Area
```
  * AWS Edge Locations
    * Used as part of a global CDN
    * Only apply to CloudFront [CDN] and Route 53 [DNS]
    * 200 Global Locations

## Understanding Cloud Economics

  * Traditional approach has very large capital (up-front) expense, plus operational costs. Upgrades 
    to capacity have additional capital expense and operational costs.
  * Cloud has no capital expense, only operational expense that scales with your demand / usage (pay as you go).
  * Traditional data center has the potential for unused capacity or unmet demand.
  * AWS Cost Explorer
    * UI for exploring your AWS costs.
    * Breakdowns by: Service, Cost Tag
    * Provides predictions for the next three months of cost based on your previous usage
    * Recommendations for cost optimization
    * API available
  * AWS Budgets
    * Plan and track usage across your AWS services
  * AWS TCO Calculator
    * Enables determination of costs for leveaging cloud infrastructure
  * AWS Simple Monthly Calculator
    * Calculate costs of running specific AWS infrastructure
  * AWS Resource Tags
    * Metadata we attach to specific resources
    * Name / Optional Value
    * Use cases include department, environment, or project
  * AWS Organizations
    * Allows for managing multiple accounts under a single master account
    * Provides consolidated billing for accounts with clean separation of costs between organizations
    * Centralize logging and security standards

## Supporting AWS Infrastructure

  * Support plans differ based on communication method, response time, cost, type of guidance offered
  * Plans
    * Basic Support
      * Provided to all customers.
      * Trusted Advisor (7 checks)
      * 24x7 Access to customer service, documentation, forums, etc.
      * Does not include implementation support
      * Personal Health Dashboard
    * Developer Support
      * Targeted at invividual developers
      * Includes all from Basic
      * Business hours email access to support
      * Tied to one primary contact
      * Starts at $29/mo, tied to AWS resource usage.
      * General Guidance - 24 business hour response time
      * System Impaired - 12 business hour response time
    * Business Support
      * Includes all from developer level
      * Full set of trusted advisor checks
      * 24/7 phone, email, and chat access to support engineers
      * Unlimited contacts (not limited to one person opening tickets)
      * 3rd party software support
      * Starts at $100/mo, tied to AWS resource usage.
      * General Guidance - 24 hour response time
      * System Impaired - 12 hour response time
      * Production System Impaired - 4 hour response time
      * Production System Down  - 1 hour response time
    * Enterprise Support
      * Includes all from business level
      * Dedicated technical account manager
      * Concierge support team
      * Starts at $15,000/mo
      * General Guidance - 24 hour response time
      * System Impaired - 12 hour response time
      * Production System Impaired - 4 hour response time
      * Production System Down  - 1 hour response time
      * Business-Critical System Down - 15 minute response time
  * Assistance for cloud workflows
    * AWS Quick Starts
    * AWS Partner Network Consulting Partners
    * AWS Professional Services
