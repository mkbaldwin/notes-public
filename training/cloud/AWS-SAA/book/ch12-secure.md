# Secure Architecture

## IAM

* root user
  * Has unrestricted access to your account. 
  * Should not be routinely used. 
  * Should use strong passwords and MFA.
* Password policy can be set and applied to all users to ensure strong
  account passwords are being used. 
* You can control if an IAM user has console access, programmatic access, 
  or both.
* Fine Grained Authorization
  * Concept of least privilege. 
  * IAM policies can be used to control what access IAM principals have.
  * IAM principals have no permissions by default.
  * IAM policy is effectively an ACL.
  * A policy consists of one or more permission statements.
  * A permissions statement consists of:
    * *Effect* - Allow or Deny
    * *Action/Operation* - Specifies the action or operation that can be
      performed on a specific AWS service.
    * *Resource* - Certain actions may require you to specify a specific
      resource. For example EC2 RunInstances can be restricted to specific
      AMIs.
    * *Condition* - Specify conditions that must be met for the rule. For
      example require a specific IP address.  
* AWS Managed Policies - Prepackaged policies managed by AWS that cover 
  different common scenarios.
* Customer-Managed Policies - A stand-alone policy you create and can 
  associate with principals in your account.
* Inline Policies - Permissions embedded in an IAM principal or group directly.
* Permissions Boundaries - Let you limit the maximum permissions that an IAM
  principal can be assigned. This prevents inadvertently attaching the wrong
  policy and giving too many permissions. 
* Roles
  * An IAM principal that does not have a password or access key.
  * Can have permissions policies and permissions boundaries associated with it.
  * Primarily useful for applications running on EC2 instances to access AWS 
    resources without needing an access key. 
  * Roles can be created and you can allow any IAM user to assume it.
  * 