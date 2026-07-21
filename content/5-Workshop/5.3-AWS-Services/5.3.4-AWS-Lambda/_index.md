---
title: "AWS Lambda"
date: 2026-07-21
weight: 4
chapter: false
pre: "<b>5.3.4 </b>"
---

# AWS Lambda

## Introduction

AWS Lambda provides the serverless computing platform for the Campus IT Support Ticket Portal.

Instead of managing application servers, each backend feature is implemented as an independent Lambda function that is automatically invoked by AWS services such as Amazon API Gateway, Amazon Cognito, and DynamoDB Streams.

This architecture allows the application to scale automatically while reducing infrastructure management.

---

## Role in the Project

AWS Lambda is responsible for:

- Processing all ticket management requests.
- Executing business logic.
- Reading and writing ticket data in Amazon DynamoDB.
- Uploading attachments to Amazon S3.
- Processing Cognito Post Confirmation events.
- Sending real-time notifications through WebSocket APIs.
- Integrating with other AWS managed services.

---

## Lambda Functions

The project contains several Lambda functions, each responsible for a different task.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-functions.png"
alt="AWS Lambda functions"
caption="Figure 5.3.4.1: AWS Lambda functions used in the Campus IT Support Ticket Portal."
>}}

The application currently includes the following functions:

- CampusSupportTicketService
- CampusSupportNotificationService
- CampusSupportWebSocketService
- CognitoPostConfirmationAddUserGroup

Each function performs an independent responsibility while communicating through AWS managed services.

---

## Function Overview

The primary backend service is implemented by the CampusSupportTicketService Lambda function.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-overview.png"
alt="Lambda overview"
caption="Figure 5.3.4.2: Overview of the CampusSupportTicketService Lambda function."
>}}

The function is triggered by Amazon API Gateway and executes all business logic related to ticket management.

The overview also displays the Lambda function ARN, API Gateway trigger, and associated resources.

---

## Source Code

The Lambda function is implemented using Node.js.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-code.png"
alt="Lambda source code"
caption="Figure 5.3.4.3: Source code of the CampusSupportTicketService Lambda function."
>}}

The implementation uses:

- AWS SDK v3
- Amazon DynamoDB
- Amazon S3
- JWT authentication
- REST API handlers

The business logic processes ticket creation, retrieval, updating, attachment uploads, and permission validation.

---

## Function Configuration

Lambda execution settings are configured through the Configuration page.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-configuration.png"
alt="Lambda configuration"
caption="Figure 5.3.4.4: General configuration of the Lambda function."
>}}

The configuration defines:

- Memory allocation
- Timeout
- Temporary storage
- Environment variables
- IAM execution role

These settings ensure that the backend service executes efficiently while remaining fully serverless.

---

## Monitoring

AWS Lambda integrates directly with Amazon CloudWatch.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-monitoring.png"
alt="Lambda monitoring"
caption="Figure 5.3.4.5: CloudWatch monitoring dashboard for the Lambda function."
>}}

CloudWatch provides operational metrics including:

- Invocation count
- Execution duration
- Error rate
- Concurrent executions
- Throttling events

These metrics help monitor application health and troubleshoot runtime issues.

---

## Results

AWS Lambda provides the following benefits:

- Fully serverless backend execution.
- Automatic scaling based on incoming requests.
- Tight integration with API Gateway, Cognito, DynamoDB, and S3.
- Reduced infrastructure management.
- Built-in monitoring through Amazon CloudWatch.