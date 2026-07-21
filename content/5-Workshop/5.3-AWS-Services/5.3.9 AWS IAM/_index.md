---
title: "AWS IAM"
date : 2026-07-21
weight : 9
chapter : false
pre : " <b> 5.3.9 </b> "
---

# AWS Identity and Access Management (IAM)

## Introduction

AWS Identity and Access Management (IAM) is a security service that enables administrators to manage authentication and authorization for AWS resources. IAM allows fine-grained access control through users, groups, roles, and policies, ensuring that AWS services operate securely based on the principle of least privilege.

In the Campus IT Support Portal project, IAM is primarily used to grant permissions to AWS services such as Lambda, API Gateway, Cognito, and RDS through IAM Roles, allowing these services to securely access the required AWS resources.

---

## IAM Dashboard

The IAM Dashboard provides an overview of the AWS account's security status and IAM resources. It displays security recommendations, account information, and the number of users, roles, and policies configured within the account.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-dashboard.png"
alt="AWS IAM Dashboard"
caption="Figure 5.3.9.1: AWS IAM Dashboard showing security recommendations and IAM resources."
>}}

The dashboard confirms that Multi-Factor Authentication (MFA) is enabled for the root account and provides an overview of the IAM resources currently configured for the project.

---

## IAM Users

IAM Users represent individual identities that can authenticate and access AWS resources. Each user can be assigned specific permissions through IAM policies or user groups.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-users.png"
alt="AWS IAM Users"
caption="Figure 5.3.9.2: IAM Users management page."
>}}

No IAM users were created for this project because AWS services are granted permissions through IAM Roles. This approach follows AWS security best practices by avoiding the use of long-term user credentials for service-to-service communication.

---

## IAM Roles

IAM Roles provide temporary permissions that AWS services can assume while interacting with other AWS resources. Roles eliminate the need to store permanent access keys and improve overall security.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-roles.png"
alt="AWS IAM Roles"
caption="Figure 5.3.9.3: IAM Roles configured for AWS services in the project."
>}}

Several IAM Roles were created automatically for the deployed AWS services, including Lambda functions, API Gateway, Cognito, and RDS. These roles allow each service to securely access only the resources required for its operation while maintaining the principle of least privilege.

---

## Results

AWS IAM provides several important security benefits for the Campus IT Support Portal:

- Centralized identity and access management.
- Secure permission management using IAM Roles.
- Fine-grained access control through IAM policies.
- Improved security by avoiding long-term credentials.
- Reliable authorization for AWS services interacting within the serverless architecture.

The implementation of IAM ensures that every AWS service operates with only the permissions required to perform its designated tasks, improving both security and maintainability.