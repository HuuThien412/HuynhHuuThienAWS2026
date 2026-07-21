---
title: "Amazon API Gateway"
date: 2026-07-21
weight: 3
chapter: false
pre: "<b>5.3.3 </b>"
---

# Amazon API Gateway

## Introduction

Amazon API Gateway provides the public entry point for all backend services used in the Campus IT Support Ticket Portal.

The frontend application sends HTTPS requests to API Gateway, which authenticates users with Amazon Cognito before forwarding requests to AWS Lambda.

API Gateway removes the need to manage traditional web servers while providing authentication, routing, monitoring, throttling, and deployment capabilities.

---

## Role in the Project

Amazon API Gateway is responsible for:

- Receiving HTTP requests from the frontend.
- Validating JWT access tokens issued by Amazon Cognito.
- Routing requests to AWS Lambda.
- Managing API deployment stages.
- Providing HTTPS endpoints.
- Supporting future REST and WebSocket APIs.

---

## API Overview

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/api-overview.png"
alt="API Gateway overview"
caption="Figure 5.3.3.1: API Gateway services used in the Campus IT Support Ticket Portal."
>}}

The project currently contains two APIs:

- CampusSupportTicketAPI (HTTP API)
- CampusSupportNotificationAPI (WebSocket API)

The HTTP API processes all REST requests, while the WebSocket API delivers real-time notifications.

---

## API Routes

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/routes.png"
alt="API routes"
caption="Figure 5.3.3.2: API routes configured for the Campus Support Ticket API."
>}}

API Gateway maps incoming requests to backend Lambda functions.

The current API exposes routes including:

- GET /tickets
- POST /tickets
- GET /{ticketId}
- PATCH /{ticketId}

---

## JWT Authorization

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/jwt-authorizer.png"
alt="JWT Authorization"
caption="Figure 5.3.3.3: JWT authorization using Amazon Cognito."
>}}

Amazon Cognito is configured as the JWT authorizer.

API Gateway validates:

- JWT signature
- Token issuer
- Audience
- Token expiration

Only authenticated users are allowed to access protected API routes.

---

## Lambda Integration

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/lambda-integration.png"
alt="Lambda Integration"
caption="Figure 5.3.3.4: Integration between API Gateway and AWS Lambda."
>}}

Each API route is integrated with an AWS Lambda function responsible for executing backend business logic.

API Gateway forwards incoming requests to Lambda using Payload Format Version 2.0.

---

## Deployment Stage

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/stage.png"
alt="API deployment stage"
caption="Figure 5.3.3.5: Default deployment stage of the HTTP API."
>}}

The API is deployed using the default stage.

Automatic deployment ensures that configuration updates become available without manually creating new deployments.

---

## Results

Amazon API Gateway provides:

- Secure HTTPS endpoints.
- JWT authentication using Amazon Cognito.
- Automatic request routing.
- Serverless integration with AWS Lambda.
- Automatic deployment management.
- Scalable API infrastructure.