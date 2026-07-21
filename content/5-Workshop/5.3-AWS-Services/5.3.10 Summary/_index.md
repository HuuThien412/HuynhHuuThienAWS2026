---
title : "Summary"
date : 2026-07-21
weight : 10
chapter : false
pre : " <b> 5.3.10 </b> "
---

# Summary

## Introduction

The Campus IT Support Portal is built using a serverless architecture on Amazon Web Services (AWS). Throughout the project, multiple AWS services were integrated to provide authentication, application hosting, business logic execution, data storage, file management, monitoring, and secure access control.

Each service plays a specific role while working together to deliver a scalable, reliable, and secure cloud-based application.

---

## AWS Services Overview

The project utilizes the following AWS services:

- **AWS Amplify Hosting** hosts and deploys the frontend application.
- **Amazon Cognito** provides user authentication and authorization.
- **Amazon API Gateway** exposes RESTful APIs for communication between the frontend and backend.
- **AWS Lambda** executes the backend business logic without managing servers.
- **Amazon DynamoDB** stores ticket information and application data.
- **Amazon S3** stores uploaded files and static assets.
- **Amazon SES** provides email notification capabilities.
- **Amazon CloudWatch** monitors application performance and collects execution logs.
- **AWS Identity and Access Management (IAM)** manages permissions and secure access between AWS services.

Together, these services form a complete serverless solution that minimizes infrastructure management while improving scalability and system availability.

---

## Benefits of the Architecture

The combination of AWS services provides several advantages for the Campus IT Support Portal:

- Fully managed serverless infrastructure.
- Automatic scalability based on application demand.
- Secure authentication and authorization.
- Reliable data storage and file management.
- Efficient monitoring and troubleshooting.
- Secure permission management through IAM Roles.
- Reduced operational and maintenance costs.
- High availability and improved system reliability.

The integration of these AWS services enables the application to operate efficiently while following AWS best practices for security, scalability, and cloud-native application development.

---

## Summary

The AWS services presented in this workshop work together to build a modern serverless architecture for the Campus IT Support Portal.

By combining Amplify Hosting, Cognito, API Gateway, Lambda, DynamoDB, S3, SES, CloudWatch, and IAM, the project achieves a secure, scalable, and maintainable cloud environment. This architecture provides a solid foundation for future feature enhancements while reducing infrastructure management complexity.