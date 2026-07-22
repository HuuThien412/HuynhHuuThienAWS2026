---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Campus IT Support Ticket Portal Workshop

#### Project overview

This workshop documents the implementation process of **Campus IT Support Ticket Portal**, a serverless helpdesk web system for receiving and managing IT support requests in a campus environment.

The completed system allows users to sign in, submit support tickets, upload attachments, and track their ticket status. Admin users can view all tickets, filter requests, update status, add resolution notes, and delete tickets when needed.

#### Architecture

{{< project-image
src="images/5-Workshop/5.2-System-Architecture/Architecture.jpg"
alt="Campus IT Support Ticket Portal Architecture"
caption="Campus IT Support Ticket Portal Architecture"
>}}

#### AWS services used

| Service | Purpose in this workshop |
| --- | --- |
| AWS Amplify Hosting | Hosts and deploys the frontend from GitHub |
| Amazon Cognito | Handles sign-up, sign-in, JWT tokens, and `Users`/`Admins` groups |
| Amazon API Gateway | Provides API endpoints and validates Cognito JWT tokens |
| AWS Lambda | Processes ticket operations and permission checks |
| Amazon DynamoDB | Stores ticket data |
| Amazon S3 | Stores ticket attachment files |
| AWS IAM | Grants Lambda permission to access DynamoDB, S3, and CloudWatch |
| Amazon CloudWatch | Stores logs and metrics for debugging |
| Amazon Route 53 | Tested for custom domain registration, but the project currently uses the default Amplify domain |

#### Content

1. [Project result and architecture](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Frontend hosting with AWS Amplify](5.3-Amplify-hosting/)
4. [Authentication with Amazon Cognito](5.4-Cognito-authentication/)
5. [Backend API with API Gateway and Lambda](5.5-Backend-api/)
6. [Data storage with DynamoDB and S3](5.6-Data-storage/)
7. [Testing, monitoring, and cleanup](5.7-Testing-monitoring-cleanup/)
