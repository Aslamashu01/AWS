# Domain: Security identity & compliance

## Topic: IAM Practical tasks

### Task: Creating and usage of IAM roles/policies

##### Problem to Be Solved
*Study how to create IAM user/roles/policies and use them for different AWS services, e.g. assume a role to use it in the AWS CLI.*

#### Implementation Details
***Pre-requisites:***

- Already created S3 bucket

- Installed jq - [https://stedolan.github.io/jq/download/](https://stedolan.github.io/jq/download/)

- Installed AWS cli v1 - [https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html)

- [https://awspolicygen.s3.amazonaws.com/policygen.html](https://awspolicygen.s3.amazonaws.com/policygen.html) or [https://aws.amazon.com/blogs/security/use-the-new-visual-editor-to-create-and-modify-your-aws-iam-policies/](https://aws.amazon.com/blogs/security/use-the-new-visual-editor-to-create-and-modify-your-aws-iam-policies/)

**Create a new user**
- Attach to the new user AWS managed policy: S3 full access.
- Attach to the new user an inline policy, that should contain the follow "Actions":
  - **iam:ListRoles**
  - **sts:AssumeRole**

_It's highly recommended to read about these "Actions" in the Tutorials and guides._

- After attaching this policy to the new user, add him permission for programmatic api access.
- Add Role named "S3ReadOnlyRole", attach to the role AWS managed policy: **S3 read-only**
- Create a json and assume role policy that defines the trust relationship of the IAM role:

For example,
``` json
{ 
  "Version": "2012-10-17", 
  "Statement": { 
    "Effect": "Allow", 
    "Principal": { 
      "AWS": "arn:aws:iam::123456789012:user/new_created_user" 
    }, 
    "Action": "sts:AssumeRole" 
  } 
}
```

**Verification:**

1. Credentials retrieval from AWS CLI for the newly created user.
2. Authorize in **AWS CLI** using credentials from the previous step.
3. Write file to an existing s3 bucket using AWS CLI, to test full access.
4. Perform role assuming using command `aws sts assume-role`
5. Authorize in **AWS CLI** using credentials from the previous step.
6. Make sure that you are authorized by using role.
7. Make a try to write file to an existing s3 bucket as in step 3.
8. Copy file from s3, that was uploaded in step 3, using **AWS CLI**.

***Solution levels (could be done in a sequence):***

- Basic - create IAM roles and user using AWS Console and policy generator, proceed with verification from AWS CLI.
- Medium - create everything using AWS CLI (hint: use policies in json format from Basic level) and proceed with verification.
- Pro - create everything using IaC approach with CloudFormation/Terraform, proceed with verification from AWS CLI.

#### Benefits / Outcomes / Pros and Cons / Summary

1. Almost everything in AWS is tied with IAM.
2. Usage of AWS managed and custom managed policies.
3. Understanding of IAM roles precedence.
4. Understanding of service-managed roles.
5. Assuming roles practice and key points.
6. Instance-profile
7. Resource-based policies

#### Tearing down

Delete all resources and delete IAM roles/policies, since you cannot delete policy or role that is in use.


# Practice

Additional:
- [IAM hands-on lab](https://general-immersionday-tmp.workshop.aws/en/iam.html)
- [Key Management: KMS](https://encryption-ws.workshop.aws/keymanagement-kms.html)