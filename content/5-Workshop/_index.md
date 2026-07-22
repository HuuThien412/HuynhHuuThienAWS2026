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

The completed system allows users to register, sign in, submit support tickets, upload attachments, track ticket history, and receive status updates. Administrators can view all tickets, search and filter requests, update ticket status, add processing notes, delete tickets, and receive alerts for high-priority issues.

The frontend is deployed publicly through **AWS Amplify Hosting** and is integrated with GitHub for automatic build and deployment.

#### Architecture

The system uses a serverless architecture on AWS. The frontend communicates with **Amazon Cognito** for authentication and sends authenticated requests to **Amazon API Gateway**. API Gateway validates Cognito JWT tokens before invoking **AWS Lambda** functions.

Lambda handles ticket operations, authorization checks, attachment processing, and integration with **Amazon DynamoDB** and **Amazon S3**. The system also uses **Amazon SES**, **Amazon CloudWatch**, **AWS IAM**, and real-time notification components such as DynamoDB Streams and WebSocket API.

{{< project-image
src="images/5-Workshop/5.2-System-Architecture/Architecture.jpg"
alt="Campus IT Support Ticket Portal Architecture"
caption="Campus IT Support Ticket Portal Architecture"
>}}

#### AWS services used

| Service | Purpose in this workshop |
| --- | --- |
| AWS Amplify Hosting | Hosts the frontend and deploys updates automatically from GitHub |
| Amazon Cognito | Handles sign-up, sign-in, sign-out, JWT tokens, and `Users`/`Admins` groups |
| Amazon API Gateway | Provides HTTP API and WebSocket API endpoints for frontend-backend communication |
| AWS Lambda | Processes ticket operations, permission checks, notifications, and WebSocket events |
| Amazon DynamoDB | Stores ticket data and WebSocket connection records |
| Amazon S3 | Stores ticket attachment files in a private bucket |
| Amazon SES | Sends ticket confirmation, alert, and status-update emails |
| Amazon CloudWatch | Stores Lambda/API logs and supports debugging and monitoring |
| AWS IAM | Grants least-privilege permissions between Lambda and other AWS services |

#### Content

1. [Project Overview](5.1-project-overview/)
2. [System Architecture](5.2-system-architecture/)
3. [AWS Services](5.3-aws-services/)
   - [AWS Amplify Hosting](5.3-aws-services/5.3.1-aws-amplify-hosting/)
   - [Amazon Cognito](5.3-aws-services/5.3.2-amazon-cognito/)
   - [Amazon API Gateway](5.3-aws-services/5.3.3-amazon-api-gateway/)
   - [AWS Lambda](5.3-aws-services/5.3.4-aws-lambda/)
   - [Amazon DynamoDB](5.3-aws-services/5.3.5-amazon-dynamodb/)
   - [Amazon S3](5.3-aws-services/5.3.6-amazon-s3/)
   - [Amazon SES](5.3-aws-services/5.3.7-amazon-ses/)
   - [Amazon CloudWatch](5.3-aws-services/5.3.8-amazon-cloudwatch/)
   - [AWS IAM](5.3-aws-services/5.3.9-aws-iam/)
   - [Summary](5.3-aws-services/5.3.10-summary/)
