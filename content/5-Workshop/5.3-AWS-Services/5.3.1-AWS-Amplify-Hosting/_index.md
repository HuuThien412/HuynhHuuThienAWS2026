---
title: "AWS Amplify Hosting"
date: 2026-07-21
weight: 1
chapter: false
pre: "<b>5.3.1 </b>"
---

## Introduction

AWS Amplify Hosting is used to build, deploy, and host the frontend of the **Campus IT Support Ticket Portal**.

The service is connected directly to the project GitHub repository. Whenever new source code is pushed to the `main` branch, AWS Amplify automatically starts a build and deployment process.

This integration provides a continuous integration and continuous deployment workflow without requiring a manually managed web server.

---

## Role in the Project

AWS Amplify Hosting is responsible for:

- Hosting the frontend application.
- Connecting the application to the GitHub repository.
- Automatically detecting new commits.
- Building and deploying the latest version.
- Providing a public HTTPS endpoint.
- Maintaining deployment history.
- Allowing previous versions to be redeployed when required.

---

## Deployment Workflow

The frontend deployment process operates as follows:

1. Source code is updated locally.
2. The changes are committed and pushed to the GitHub repository.
3. AWS Amplify detects the new commit on the `main` branch.
4. Amplify downloads the latest source code.
5. The build process is executed.
6. After a successful build, the application is deployed.
7. The updated version becomes available through the Amplify domain.

---

## Amplify Application

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.1-AWS-Amplify-Hosting/amplify-hosting.png"
alt="AWS Amplify Hosting application overview"
caption="Figure 5.3.1: Campus IT Support Ticket Portal deployed on AWS Amplify Hosting."
>}}

The Amplify application overview displays the application name, App ID, production branch, public domain, latest deployment, and connected GitHub repository.

---

## Build and Deployment

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.1-AWS-Amplify-Hosting/deployment-success.png"
alt="Successful AWS Amplify deployment"
caption="Figure 5.3.2: Successful build and deployment process on AWS Amplify."
>}}

The deployment page confirms that both the build and deployment stages completed successfully. It also records the build duration, deployment duration, source commit, and previous deployment history.

---

## Results

AWS Amplify Hosting provides the following results:

- The frontend is publicly available through HTTPS.
- Deployment is automatically triggered by GitHub commits.
- The CI/CD workflow reduces manual deployment errors.
- No frontend web server needs to be maintained.
- Deployment history is available for troubleshooting and rollback.
