---
title: "Backend API with API Gateway and Lambda"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Goal

Create the backend API layer that receives frontend requests, validates JWT tokens, invokes Lambda, and processes ticket operations.

### API Gateway setup

1. Create an API Gateway API.
2. Configure API routes for ticket operations.
3. Enable CORS for the Amplify frontend domain.
4. Configure a JWT Authorizer connected to the Cognito User Pool.
5. Attach the authorizer to protected routes.

### Lambda setup

1. Create Lambda functions for ticket operations.
2. Read JWT claims from the request context.
3. Check whether the caller belongs to `Users` or `Admins`.
4. Validate request body fields.
5. Call DynamoDB for ticket data operations.
6. Call S3 for attachment file operations.
7. Return JSON responses to API Gateway.

### API routes

| Method | Endpoint | Permission | Purpose |
| --- | --- | --- | --- |
| POST | `/tickets` | User/Admin | Create ticket |
| GET | `/tickets/my` | User | View own tickets |
| GET | `/tickets` | Admin | View all tickets |
| GET | `/tickets/{ticketId}` | Owner/Admin | View ticket detail |
| PATCH | `/tickets/{ticketId}` | Admin | Update status and note |
| DELETE | `/tickets/{ticketId}` | Admin | Delete ticket |

### Screenshot evidence to include

- API Gateway routes.
- JWT Authorizer configuration.
- Lambda function overview.
- Successful API test result.
