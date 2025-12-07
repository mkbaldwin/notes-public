# Introduction

 * AWS Organizations
    * Allow for grouping individual AWS accounts for centralized management.
    * Apply Global IAM rules
    * Share resources through unified AWS SSO. 
    * Audit all environments for compliance.
    * Consolidated billing (replaces consolidated billing tool)
 * AWS Control Tower
    * Extends the functionality of AWS Organizations and allows creations of "landing zones."
    * Landing zones streamline onboarding of new accounts and automatically apply your organization's governance policies.
    * Blueprints for security best practices.
 * AWS Service Catalog
    * Allows for providing end users easy access to approved services.
    * Create a predefined set of resources via CloudFormation. 
 * AWS License Manager
    * Service that helps you manage software licenses. 
    * Dashboard that allows tracking usage, monitoring compliance, and enforcing rules. 
    * No recurring cost.
 * AWS Artifact
    * Allows for downloading compliance related information about their AWS accounts.
    * Useful for collecting compliance details for audits.
 * AWS CLI
    * Run complex AWS operations from your local command line
 * AWS SDK
    * Allows for incorporating AWS resources into custom application code.
    * SDK available for multiple languages including Java, .NET, and Python.

## Migration Tools

 * Migration Hub
    * Helps organizations track progress as they migrate workloads to the AWS cloud.
    * Dashboard provides a central place to view information about existing inventory and migration project status.
 * AWS Application Migration Service
    * Automates testing and transfer of non-cloud application servers.
    * Useful in a lift-and-shift migration. 
    * Install AWS replication on each server to be migrated, and the agent performs the replication in the background. 
    * NOTE: CloudEndure would be used to migrate to GovCloud
 * AWS Database Migration Service
    * Performs migration of databases to the cloud.
    * Can be homogeneous migration (e.g. Oracle to Oracle), or migrate to a different platform.
      * Move relational DB to data lake in S3
      * Move oracle db to aurora
 * AWS Application Discovery Service
    * Help plan migration by identifying which applications you have running, how they are interconnected, and resources used. 
    * Normally install Application Discovery Service agents on each server. 
    