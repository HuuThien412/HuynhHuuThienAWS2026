---
title: "AWS Amplify Hosting"
date: 2026-07-21
weight: 1
chapter: false
pre: "<b>5.3.1 </b>"
---

## Overview

AWS Amplify Hosting is used to deploy and host the frontend application of the Campus IT Support Ticket Portal.

It provides automatic deployment from the GitHub repository, HTTPS support, and continuous integration and continuous deployment (CI/CD). Every new commit pushed to the **main** branch automatically triggers a new deployment.

The deployed frontend communicates with Amazon Cognito for authentication and Amazon API Gateway for backend API requests.

---

## Amplify Application

The following figure shows the AWS Amplify application dashboard after the frontend has been successfully deployed.

{{< project-image
src="images/5-Workshop/5.3-AWS Services/5.3.1 AWS Amplify Hosting/Amplify Hosting.png"
alt="AWS Amplify Hosting"
caption="Figure 5.3.1: AWS Amplify Hosting dashboard."
>}}

---

## Deployment Process

After each source code update is pushed to GitHub, AWS Amplify automatically builds and deploys the latest version of the application.

The deployment history allows developers to monitor build status, deployment duration, and rollback previous versions when necessary.

{{< project-image
src="images/5-Workshop/5.3-AWS Services/5.3.1 AWS Amplify Hosting/Deployment Success.png"
alt="Deployment Success"
caption="Figure 5.3.2: Successful deployment using AWS Amplify."
>}}

---

## Benefits

AWS Amplify Hosting provides several advantages:

- Automatic deployment from GitHub
- HTTPS enabled by default
- Continuous Integration / Continuous Deployment (CI/CD)
- Fast global content delivery
- Simple frontend hosting without server management

Amplify serves as the entry point of the system before users access Amazon Cognito for authentication and backend services through Amazon API Gateway.