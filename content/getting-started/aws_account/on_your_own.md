---
title: "On your own"
chapter: false
weight: 3
---


## Requirements

Your account must have the ability to create new IAM roles and scope other IAM permissions.

::alert[Do not create the IAM roles in any production AWS account. Having admin privileges in production account is not recommended security best practice.]{header="Warning" type="warning"}

## Configure your account

1. If you don't already have an AWS account with Administrator access: 
   [create one now by clicking here](https://aws.amazon.com/getting-started/).

2. Once you have an AWS account, ensure you are following the remaining workshop steps
as an IAM user with administrator access to the AWS account:
[Create a new IAM user to use for the workshop](https://us-east-1.console.aws.amazon.com/iam/home?#/users$new). To do so, follow the next steps:

   1. Enter the user details:
        ![Sysdig Trial](/static/10_prerequisites/iam-1-create-user.png)

   2. Attach the AdministratorAccess IAM Policy:
       ![Sysdig Trial](/static/10_prerequisites/iam-2-attach-policy.png)

   3. Click to create the new user:
       ![Sysdig Trial](/static/10_prerequisites/iam-3-create-user.png)

   4. Take note of the login URL and save:
       ![Sysdig Trial](/static/10_prerequisites/iam-4-save-url.png)

   5. Access the console with the new admin user.


::alert[You are responsible for the cost of the AWS services used while running this workshop in your AWS account.]{header="Note"}
