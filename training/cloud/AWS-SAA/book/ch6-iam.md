# Identity and Access Management (IAM)

## Identities

### Policies

* An IAM policy is a document that identifies one or more actions as they relate to one or more AWS Services
* Policies have an effect of either Allow or Deny
* Must specify a resource and action.
* Policies are assigned to an identity.
* Deny by default. Any action not explicitly defined to be allowed is blocked by default.

```json
{
    Version: "2025-11-21",
    Statement: [
        {
            "Effect": "Allow",
            "Action": "*",
            "Resource": "*"
        }
    ] 
}
```

* A single IAM policy can be assigned to an unlimited number of identities.
* An IAM identity is limited to being assigned 10 managed policies.
* If there are conflicts between policies assigned to an identity then deny always wins.

### Accounts

* Root Account
  * Should be protected and locked down.
  * Delete associated access keys.
  * Assign long / complex password and enable MFA.
  * Don't use root to perform operations.
  * Always create other user accounts with administrator access before locking down root.

### Access Keys

* Used to provide authentication for programmatic and CLI based actions.
* Used as alternative to username / password.
* Keys should be periodically rotated and replaced.

### Groups

* Create a group for each class of user that will require the same IAM access.
* Permissions can be changed for the whole group and apply to all users. 

### Roles

* A role is a temporary identity that a user or service can request.
* Can be thought of similar to sudo on Linux, gain the privileges only when needed.
* Permissions are assigned by assigning an appropriate Policy document.

## Authentication Tools

* Amazon Cognito
  * Allows you to manage authentication for mobile and web applications
* AWS Managed Microsoft AD
  * Accessed through AWS Directory Service
  * Managed AD Controllers
* AWS Single Sign-On (SSO)
  * Provide users with a streamlined authentication process through existing Microsoft AD
* AWS Key Management Service (KMS)  
  * Manage encryption keys for AWS services
  * Fully managed and centralized
  * Deeply integrated with AWS services
* AWS Secrets Manager
  * APIs and tools for managing secrets for other services (e.g. passwords)
  * Can also handle credential rotation
* AWS Cloud HSM
  * Virtual Hardware Security Modules
  * Launches compute device clusters to handle cryptographic operations for your applications
  * Useful for:
    * High-performance crypto acceleration
    * FIPS 140-2 compliance
    * Integration with Java JCE and Microsoft CNG 
* AWS Resource Access Manager (RAM)
  * Lets you manage access to resources and share with users in multiple accounts.
