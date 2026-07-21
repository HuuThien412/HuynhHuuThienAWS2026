---
title: "5.3 AWS Services"
date: 2026-07-21
weight: 3
chapter: false
pre: "<b>5.3 </b>"
---

# AWS Services

## 5.3.1 AWS Amplify Hosting

### Introduction

AWS Amplify Hosting was selected as the frontend hosting service for the **Campus IT Support Ticket Portal**. It provides a managed environment for hosting static web applications while integrating directly with GitHub to automatically build and deploy the project whenever new source code is pushed.

Using AWS Amplify eliminates the need to configure and maintain a traditional web server while providing HTTPS support, optimized content delivery, and a complete CI/CD workflow.

---

### Role in the Project

Within this project, AWS Amplify is responsible for:

- Hosting the frontend application.
- Automatically building the Hugo website after every GitHub push.
- Deploying new versions without manual intervention.
- Providing a secure HTTPS endpoint for users.
- Managing deployment history.
- Supporting future expansion through multiple deployment branches.

---

### Deployment Workflow

The frontend deployment workflow operates as follows:

1. The developer pushes new source code to GitHub.
2. AWS Amplify detects the new commit on the **main** branch.
3. Amplify downloads the updated repository.
4. The project is automatically built.
5. After a successful build, Amplify deploys the new version.
6. The updated website becomes available to users.

This automated workflow minimizes deployment errors and ensures that the latest version of the application is always available.

---

### AWS Amplify Application

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/Amplify Hosting.png"
alt="AWS Amplify Hosting"
caption="Figure 5.3.1: Campus IT Support Ticket Portal deployed on AWS Amplify Hosting."
>}}

The figure above shows the application hosted on AWS Amplify. Amplify manages the application, production branch, default domain, and GitHub repository integration.

---

### Build and Deployment Process

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/Deployment Success.png"
alt="Deployment Success"
caption="Figure 5.3.2: Successful build and deployment process on AWS Amplify."
>}}

Whenever new source code is pushed, AWS Amplify automatically starts the build and deployment pipeline. The console displays the build duration, deployment duration, deployment history, and deployment status, allowing developers to monitor each release efficiently.

---

### Results

Using AWS Amplify Hosting provides the following benefits:

- The frontend is publicly accessible through HTTPS.
- The CI/CD pipeline is fully automated.
- The website is updated automatically after every GitHub push.
- No web server management is required.
- The architecture is ready for future expansion with multiple deployment environments.