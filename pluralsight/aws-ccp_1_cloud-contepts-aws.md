# Fundamental Cloud Concepts for AWS

## Understanding Cloud Computing

  * Traditional Data Centers
    * Forecasting demand is difficult.
    * Large investment
    * Slow to deploy
    * Expensive to Maintain
    * Own all security burden
  * Cloud benefits
    * Capotal expense (up front) traded for variable monthly expense
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
    * Private Cloud - Cloud likfe features in a private data center
    * Hybrid - Using both public/private cloud together

## AWS Global Infrastructure

  * AWS Regions
    * Specific geographic location
    * Cluster of data centers working together
    * Currently 22 regions, 5 more announced
    * 4 public regions in the US
    * 2 GovCloud regions
  * Availability Zone (AZ)
    * One or more data centers
    * Each region has multiple AZs
    * Redundant power / networking
    * 69 AZz
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