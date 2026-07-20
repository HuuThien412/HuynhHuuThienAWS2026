---
title: "Frontend hosting with AWS Amplify"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Goal

Deploy the web frontend using AWS Amplify Hosting so users and admins can access the system through an HTTPS website.

### Implementation steps

1. Push the frontend source code to GitHub.
2. Open the AWS Amplify console.
3. Choose **Host web app** and connect the GitHub repository.
4. Select the target branch.
5. Configure build settings.
6. Deploy the application.
7. Open the generated Amplify domain and verify that the website loads successfully.

### Result

The frontend is available through the default AWS Amplify domain. Route 53 custom domain registration was tested, but the system currently uses the Amplify domain because the custom domain process had registrar/account validation issues.

### Screenshot evidence to include

- Amplify app connected to GitHub.
- Successful build/deploy result.
- Website opened from the Amplify domain.
