# IAM – Identity and Access Management

## Table of Content

- [Your goals](#your-goals)
- Service Overview
- IAM Fundamentals
- IAM Policy
- [Self-check](#self-check)
- More details

## Your goals

- Be able to describe identities in IAM

- Understand standard API request flow

- Know what Amazon Resource Number(ARN) is

- Learn about different types of IAM policies and what they consist of

- Be able to tell what types of AWS credentials exist

- Know about IAM Access Analyzer and IAM Policy Simulator


## Service Overview

---
![](images/iam_01.png)

AWS Identity and Access Management (IAM) helps you securely control access to Amazon Web Services (AWS) and your account resources. IAM can also keep your account credentials private. With IAM, you can create multiple IAM users under the umbrella of your AWS account or enable temporary access through identity federation with your corporate directory. In some cases, you can also enable access to resources across AWS accounts.

Without IAM, however, you must either create multiple AWS accounts—each with its own billing and subscriptions to AWS products—or your employees must share the security credentials of a single AWS account. In addition, without IAM, you cannot control the tasks a particular user or system can do and what AWS resources they might use.

Almost everything is tied with IAM in AWS!

## API request flow
![](images/apiflow.png)

It's very important to understand that every interaction with AWS services is a request to API endpoint - create instance, run Lambda function or observe the billing. All of this is availible throug API. Each request is passed via HTTPS[1], validated on API endpoint[2], authenticated and authorized on IAM[3] and recorded in CloudTrail[4] even the request was unsuccessful.

This means that each small interaction in the AWS is authenticated via IAM.


## Use cases / Considerations

---

* **Fine-grained access control to AWS resources** - IAM enables [your users](https://aws.amazon.com/iam/features/manage-users/) to [control access](https://aws.amazon.com/iam/features/manage-permissions/) to AWS service APIs and to specific resources. IAM also enables you to add [specific conditions](https://aws.amazon.com/iam/features/manage-permissions/) such as time of day to control how a user can use AWS, their originating IP address, whether they are using SSL, or whether they have authenticated with a [multi-factor authentication device](https://aws.amazon.com/iam/features/mfa/). IAM is secure by default; users have no access to AWS resources until permissions are explicitly granted.
* **Temporary credentials** - In addition to defining access permissions directly to users and groups, IAM lets you create roles. Roles allow you to define a set of permissions and then let authenticated users or EC2 instances assume them, increasing your security posture by granting temporary access to the resources you define.
* **Multi-factor authentication for highly privileged users** - protect your AWS environment by using [AWS MFA](https://aws.amazon.com/iam/features/mfa/), a security feature available at no extra cost that augments user name and password credentials. MFA requires users to prove physical possession of a hardware MFA token or MFA-enabled mobile device by providing a valid MFA code.
* **Analyze access** - IAM helps you [analyze access](https://aws.amazon.com/iam/features/analyze-access/) across your AWS environment. Your security teams and administrators can quickly validate that your policies only provide the intended public and cross-account access to your resources. You can also easily identify and refine your policies to allow access to only the services being used. This helps you to better adhere to the principle of least privilege.
* **Integrate with your corporate directory** - IAM can be used to grant your employees and applications [federated access](https://aws.amazon.com/identity/federation/) to the AWS Management Console and AWS service APIs, using your existing identity systems such as Microsoft Active Directory. You can use any [identity management](http://docs.aws.amazon.com/IAM/latest/UserGuide/IdP-solution-providers.html) solution that supports [SAML 2.0](https://aws.amazon.com/identity/saml/), or feel free to use one of our federation samples ([AWS Console SSO](http://aws.amazon.com/code/4001165270590826) or [API federation](http://aws.amazon.com/code/1288653099190193)).
* **Seamlessly integrated into AWS services** - IAM is integrated into most AWS services. This provides the ability to define access controls from one place in the AWS Management Console that will take effect throughout your AWS environment.

# IAM Fundamentals

### AWS account root user

When you first create an Amazon Web Services (AWS) account, you begin with one identity that has complete access to all AWS services and resources in the account. This identity is called the AWS account root user. You can sign in as the root user using the email address and password that you used to create the account.
Important

**We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones.**

You can create, rotate, disable, or delete access keys (access key IDs and secret access keys) for your AWS account root user. You can also change your root user password. Anyone who has root user credentials for your AWS account has unrestricted access to all the resources in your account, including billing information.

## IAM Identities
(users, user groups, and roles)

The AWS account root user or an IAM administrator for the account can create IAM identities. An IAM identity provides access to an AWS account. A user group is a collection of IAM users managed as a unit. An IAM identity represents a user, and can be authenticated and then authorized to perform actions in AWS. Each IAM identity can be associated with one or more policies. Policies determine what actions a user, role, or member of a user group can perform, on which AWS resources, and under what conditions.

### IAM users

An [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html) is an entity that you create in AWS. The IAM user represents the person or service who uses the IAM user to interact with AWS. A primary use for IAM users is to give people the ability to sign in to the AWS Management Console for interactive tasks and to make programmatic requests to AWS services using the API or CLI. A user in AWS consists of a name, a password to sign into the AWS Management Console, and up to two access keys that can be used with the API or CLI. When you create an IAM user, you grant it permissions by making it a member of a user group that has appropriate permission policies attached (recommended), or by directly attaching policies to the user. You can also clone the permissions of an existing IAM user, which automatically makes the new user a member of the same user groups and attaches all the same policies. To add IAM users to your IAM account, see [Creating an IAM user in your AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).

### IAM user groups

An [IAM user group](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html) is a collection of IAM users. You can use user groups to specify permissions for a collection of users, which can make those permissions easier to manage for those users. For example, you could have a user group called Admins and give that user group the types of permissions that administrators typically need. Any user in that user group automatically has the permissions that are assigned to the user group. If a new user joins your organization and should have administrator privileges, you can assign the appropriate permissions by adding the user to that user group. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old user groups and add him or her to the appropriate new user groups. A user group cannot be identified as a `Principal` in a resource-based policy. A user group is a way to attach policies to multiple users at one time. When you attach an identity-based policy to a user group, all of the users in the user group receive the permissions from the user group. For more information about these policy types, see [Identity-based policies and resource-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html).

### IAM roles

An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is very similar to a user, in that it is an identity with permission policies that determine what the identity can and cannot do in AWS. However, a role does not have any credentials (password or access keys) associated with it. Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. An IAM user can assume a role to temporarily take on different permissions for a specific task. A role can be assigned to a federated user who signs in by using an external identity provider instead of IAM. AWS uses details passed by the identity provider to determine which role is mapped to the [federated user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html).


## Types of AWS credentials

A user in AWS consists of a name, a password to sign in to the AWS Management Console, and up to two access keys, which can be used with the API or CLI.

### Username and password

You can manage passwords for your AWS account root user and for IAM users in your account. IAM users need passwords in order to access the AWS Management Console. Users do not need passwords to access AWS resources programmatically by using the AWS CLI, Tools for Windows PowerShell, the AWS SDKs or APIs. For those environments, users need access keys instead.
You can set a custom password policy on your AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords. If you don't set a custom password policy, IAM user passwords must meet the default AWS password policy.
A password policy is a set of rules that define the type of password an IAM user can set. You should define a password policy for all of your IAM users to enforce strong passwords and to require your users to regularly change their passwords. Password requirements are similar to those found in most secure online environments.

### Access keys

Access keys are long-term credentials for an IAM user or the AWS account root user. You can use access keys to sign programmatic requests to the AWS CLI or AWS API (directly or using the AWS SDK).

Access keys consist of two parts: an access key ID (for example, `AKIAIOSFODNN7EXAMPLE`) and a secret access key (for example, `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`). Like a user name and password, you must use both the access key ID and secret access key together to authenticate your requests. Manage your access keys as securely as you do your user name and password. Each user can have two active access keys, which is useful when you need to rotate the user's access keys or revoke permissions. 

**Important**
Do not provide your access keys to a third party, even to help find your canonical user ID. By doing this, you might give someone permanent access to your account.

As a best practice, use temporary security credentials (IAM roles) instead of access keys, and disable any AWS account root user access keys. For more information, see Best Practices for Managing AWS Access Keys in the Amazon Web Services General Reference.

### Multi-Factor Authentication (MFA)

Multi-factor authentication (MFA) is an additional layer of security for accessing AWS services. With this authentication method, more than one authentication factor is checked before access is granted, which consists of a user name, a password, and the single-use code from the MFA device. AWS CLI also supports MFA

### Temporary credentials in IAM

[Temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html) are primarily used with IAM roles, but there are also other uses. You can request temporary credentials that have a more restricted set of permissions than your standard IAM user. This prevents you from accidentally performing tasks that are not permitted by the more restricted credentials. A benefit of temporary credentials is that they expire automatically after a set period of time. You have control over the duration that the credentials are valid.

## IAM Policy

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": "ec2:*",
            "Resource": "*",
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ec2:Region": "us-east-2"
                }
            }
        }
    ]
}
```

A policy is an entity in AWS that, when attached to an identity or resource, defines their permissions. AWS evaluates these policies when a principal, such as a user, makes a request. If you specify multiple conditions, or multiple keys in a single condition, IAM evaluates them using a logical AND operation. If you specify a single condition with multiple values for one key, IAM evaluates the condition using a logical OR operation. For a permission to be granted, all conditions must be met. 

Policy types, statements and syntax could be found [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)

Please review core IAM Policy elements 

![](images/iam_policy_elements.png)

#### IAM policy simulator
With the IAM policy simulator, you can test and troubleshoot identity-based policies, IAM permissions boundaries, AWS Organizations service control policies, and resource-based policies. The policy simulator does not make an actual AWS service request, so you can safely test requests that might make unwanted changes to your live AWS environment. The only result returned is whether the requested action would be allowed or denied.

#### IAM Access Analyzer 
It continuously monitors policies for changes where you no longer need to rely on intermittent manual checks in order to catch issues as policies are added or updated. Using IAM Access Analyzer, you can proactively address any resource policies that violate their security and governance best practices around resource sharing and protect their resources from unintended access. IAM Access Analyzer delivers comprehensive, detailed findings through the IAM, Amazon S3, and AWS Security Hub consoles and also through its APIs. Findings can also be exported as a report for auditing purposes. 
IAM Access Analyzer findings provide definitive answers of who has public and cross-account access to AWS resources from outside an account.


### Key points

---

* Policies are expressed in JSON [format](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_grammar.html).
* Use an [instance profile](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html) to pass an IAM role to an EC2 instance (see picture below).
* By default IAM role has "Maximum session duration" 1 hour, it could be changed, but not for role chaining using CLI or API.
* To configure many AWS services, you must [pass an IAM role to the service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_passrole.html).
* Resource-based policies are attached to a resource. For example, you can attach resource-based policies to Amazon S3 buckets, Amazon SQS queues, and AWS Key Management Service encryption keys. For a list of services that support resource-based policies, see [AWS services that work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html).
  
![](images/iam_02.png)

## Cautions

---

* **Roles** and **policies** are global AWS resources, their **names** must be **unique across AWS account**. 

_**Hint**_: in some cross environment and/or regional cases you could add environment suffix (dev, qa, preprod, etc) and/or region name (f.i. us-east-1), short region name (use1).



## Pricing considerations

---
* There is no charge for IAM usage, it's free.


## Self-check

1. What is the the difference between IAM identity and IAM principle?
2. Which type of request to AWS is recorded by CloudTrail?
3. What's the difference between customer managed IAM policy and AWS managed IAM policy?
4. How does inline policy differ from managed policy?
5. What are the limits for inline IAM policy?
6. What are the best practices when working with permissions?
7. The AWS CLI credentials and configuration settings take precedence in which order?(name first 3)
8. What is the allow/deny priority order when policies are configured on different levels (group, user, 
etc.)?


## More details

### Videos
* [IAM ninja (video)](https://www.youtube.com/watch?v=aISWoPf_XNE)
* [Become an IAM policy master in 60 minutes or less (video)](https://youtu.be/YQsK4MtsELU)

### Documentation
* [AWS IAM FAQs](https://aws.amazon.com/iam/faqs/)
* [Policy evaluation logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html)

### Recommended Trainings:

- [AWS Certified Solutions Architect - Associate (SAA-C02): 5 Identity and Access Management](https://learn.epam.com/detailsPage?id=711b13a6-3eba-4d0a-a87c-278c60661983&source=EXTERNAL_COURSE)

 
