---
title: "Project result and architecture"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Project result

The completed project is a web-based IT support ticket portal deployed on AWS. It includes two main interfaces:

| Interface | Main functions |
| --- | --- |
| User Portal | Sign in, submit ticket, upload attachment, view personal tickets |
| Admin Console | View all tickets, filter tickets, update status, add notes, delete tickets |

### Architecture flow

1. User/Admin accesses the website through HTTPS.
2. AWS Amplify serves the frontend UI.
3. The frontend redirects the user to Amazon Cognito for sign-up/sign-in.
4. Cognito returns a JWT token to the frontend.
5. The frontend sends API requests with the JWT token to API Gateway.
6. API Gateway validates the token and invokes Lambda.
7. Lambda creates, lists, updates, or deletes ticket data in DynamoDB and stores attachments in S3.

![Campus IT Support Ticket Portal Architecture](/images/5-Workshop/ticket-portal-architecture.png)

### Expected outcome

After completing the workshop, the system should support authenticated user and admin flows, ticket management, attachment storage, backend logs, and cleanup documentation.
