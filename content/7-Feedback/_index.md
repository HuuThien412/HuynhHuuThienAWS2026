---
title: "Sharing and Feedback"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

### Sharing

During the internship and AWS learning journey, I had the opportunity to study and practice several important cloud services through the FCJ Cloud Journey and AWS Study Group materials. The most valuable part of this process was learning how different AWS services can work together to build a complete application rather than studying each service separately.

For my project, I built and documented the **Campus IT Support Ticket Portal**, a serverless helpdesk system for receiving and managing IT support requests in a campus environment. Through this project, I practiced using AWS Amplify Hosting, Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, IAM, and Amazon CloudWatch.

The project helped me understand the full flow of a cloud application:

- Hosting a frontend website with AWS Amplify.
- Authenticating users and admins with Amazon Cognito.
- Protecting APIs with JWT Authorizer in API Gateway.
- Processing backend logic with AWS Lambda.
- Storing ticket data in DynamoDB.
- Storing uploaded attachments in Amazon S3.
- Checking logs and errors with Amazon CloudWatch.
- Controlling access between services using IAM roles.

Besides technical knowledge, I also improved my documentation skill. Writing the proposal, worklog, blog posts, and workshop helped me organize the project more clearly and explain technical decisions in a structured way.

### Difficulties

Some difficulties I encountered during the project included:

- Understanding how Cognito JWT tokens are passed from the frontend to API Gateway.
- Separating normal user permissions and admin permissions correctly.
- Designing DynamoDB data fields to support both user and admin workflows.
- Handling file attachment storage with S3.
- Debugging backend errors through CloudWatch Logs.
- Testing Route 53 custom domain registration, which could not be completed because of registrar/account validation issues.

These issues helped me realize that building a cloud system is not only about creating resources, but also about connecting services correctly, controlling permissions carefully, and testing each flow step by step.

### Feedback

The FCJ Cloud Journey and AWS Study Group materials are useful for students who want to learn AWS through hands-on practice. The workshop format makes it easier to follow because each section has a clear goal, implementation steps, validation, and cleanup.

From my experience, the learning process would be even more effective if learners:

- Prepare screenshots immediately after each implementation step.
- Record errors and solutions during deployment.
- Document IAM permissions clearly.
- Keep architecture diagrams updated when the project changes.
- Add cleanup steps to avoid unnecessary AWS costs.

### Suggestions

For future learners, I suggest starting with a small but realistic project. A project like a ticket portal is suitable because it includes common cloud application components: frontend hosting, authentication, APIs, backend processing, database storage, file storage, monitoring, and security.

For future improvement, this project can be extended with:

- Email notifications when a ticket is created or updated.
- Dashboard charts for ticket status and priority.
- Better attachment preview in the admin console.
- A completed custom domain configuration with Route 53.
- More detailed audit logging for admin actions.

### Conclusion

Overall, this internship report and project helped me connect AWS theory with real implementation. I gained a clearer understanding of serverless architecture, authentication, API design, data storage, monitoring, and documentation. The experience also showed me the importance of careful planning, step-by-step testing, and clear technical writing when building cloud projects.
