# AWS Certified Developer Associate

## Exam Overview

  * 130 min
  * 65 Questions
  * 720/1000 == PASS

| Topic                          | Percentage |
|--------------------------------|:----------:|
| Development with AWS Services  |    32%     |
| Security                       |    26%     |
| Deployment                     |    24%     |
| Troubleshooting & Optimization |    18%     |

## Beginners Guide to IAM

AWS Identity & Access Management (IAM) is a global service that applies across all regions. Though, it is possible to
restrict permissions to only a specific region. This service provides:

  * Centralized control over AWS account
  * Shared access
  * Granular permissions
  * Identity federation
  * MFA
  * Temporary Access
  * Password Policies
  * PCI/DSS Compliance

### Core Concepts

  * **User** - End users (actual people)
  * **Group** - Collections of users with a common set of permissions.
  * **Role** - Used to define a set of permissions that can then be granted to users, groups, or instances.
  * **Policy** - A JSON document that defines one or more permission. Can then be assigned to one or more user, group or role.
  * **Amazon Resource Name (ARN)** - A unique identifier for a specific resource. Users in IAM are types of resources.

Access Types

  * **Programmatic** - Via API, CLI, or SDL using access key ID and secret key access.
  * **Management Coneole** - Via the web interface and username/password.

Policy Types

  * **Managed Policy** - A policy created and managed by AWS or someone in your organization that can be used in multiple places.
  * **Inline Policy** - A policy that exists only where it is assigned to one user or group.

Policy Concepts

  * Policies can be specific to an individual instance. For example, it is possible to define stop/start permissions for
a specific EC2 instance rather than to all instances.
  * An explicit deny in a policy always overrides any other allows defined in the policy.
  * All permissions are implicitly denied until allowed by a policy.

IAM Policy simulator

* Test the effects of IAM policies before committing to prod.
* Validate policies work as expected.
* Test policies applied to existing users (good for troubleshooting).
* https://policysim.aws.amazon.com
