---
title: "Prerequisites"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

### Required accounts and tools

Before starting the deployment, prepare:

- An AWS account with permission to use Amplify, Cognito, API Gateway, Lambda, DynamoDB, S3, IAM, and CloudWatch.
- A GitHub repository for the frontend source code.
- A local development environment with Git, Node.js, and a code editor.
- Basic understanding of serverless architecture and REST APIs.

### AWS configuration checklist

| Item | Purpose |
| --- | --- |
| AWS Region | Deploy all resources in the same region when possible |
| IAM permissions | Allow Lambda to access DynamoDB, S3, and CloudWatch |
| Cognito User Pool | Store user accounts and groups |
| DynamoDB table | Store support ticket records |
| S3 bucket | Store ticket attachments |
| Amplify app | Host the frontend website |

### Naming convention

Use clear resource names such as:

- `campus-ticket-user-pool`
- `campus-ticket-table`
- `campus-ticket-attachments`
- `campus-ticket-api`
- `campus-ticket-backend`
