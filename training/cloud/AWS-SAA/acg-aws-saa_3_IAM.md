# Identity and Access Management

 * Centralized control of your AWS account
 * Granular Permissions
 * Identity Federation
 * Multifactor Authentication
 * Provisions for temporary access
 * Define custom password rotation policies
 * PCI DSS Compliance (for credit card processing)
 * Key Terms
   * User - End user (people)
   * Group - A collection of users. Each user will inherit the permissions of the group.
   * Policies - Consist of policy documents that define permissions as to what a user/group/role can do.
   * Role - Assigned to AWS resources to control privileges. 
 * IAM is a global service and not tied to regions.
   * Users, groups, etc. are created for the whole account.
 * "root" account is the initial account and has complete admin access.
   * Always turn on multifactor authentication for this account.
 * New users
   * Have no permission by default
   * Assigned access key Id and secret access keys for API usage when created.
   * Password and Access Key/Secret Access Key are not the same.
   * Only password can be used to access the console.

