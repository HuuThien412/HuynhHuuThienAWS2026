---
title: "Sharing and Feedback"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Sharing and Feedback

## Learning and Implementation Experience

During the internship, I started by learning AWS Cloud fundamentals and core services, then gradually moved to more advanced topics such as networking, security, databases, serverless computing, CI/CD, monitoring, and cost control. Writing weekly worklogs helped me review what I had learned, identify difficulties, and complete missing parts before finalizing the report.

My main project was **Campus IT Support Ticket Portal**, a web-based system for receiving and managing IT support requests in a campus environment. The system includes two main workflows: users can submit tickets, track their status, and upload attachments; administrators can view ticket lists, filter requests, update status, add resolution notes, and delete tickets when needed.

The most important point of this project is that it was built with a serverless architecture on AWS. The frontend is deployed with **AWS Amplify Hosting**, authentication is handled by **Amazon Cognito**, APIs are managed by **Amazon API Gateway**, backend logic runs on **AWS Lambda**, ticket data is stored in **Amazon DynamoDB**, attachments are stored in **Amazon S3**, notifications use **Amazon SES**, logs are monitored through **Amazon CloudWatch**, and permissions are controlled by **AWS IAM**.

Through this project, I understood that a complete cloud application is not only about creating individual services. The more important part is designing the connection flow between services, applying suitable permissions, testing each function carefully, and documenting the implementation clearly enough for others to understand.

## Knowledge Gained

- I understood how a frontend can be hosted and automatically deployed through AWS Amplify Hosting.
- I learned how Amazon Cognito supports sign-up, sign-in, JWT tokens, and authorization through `Users`/`Admins` groups.
- I understood the role of API Gateway in receiving requests, validating JWT tokens, and forwarding requests to Lambda.
- I practiced implementing ticket operations with Lambda, including create, read, update, and delete functions.
- I learned how to store NoSQL data in DynamoDB and manage attachments with S3.
- I became familiar with email notifications using Amazon SES and real-time update flows using DynamoDB Streams/WebSocket.
- I learned to use CloudWatch Logs to inspect errors and monitor backend activity.
- I became more aware of IAM least privilege and cost monitoring through Billing Dashboard.

## Difficulties

During implementation, I faced several difficulties when connecting services together. For example, the Cognito and JWT Authorizer flow was easy to misunderstand at first because the frontend, API Gateway, and Lambda all needed to handle the token and user permissions correctly. Separating normal user permissions from admin permissions also required careful testing to prevent users from accessing administrative functions.

Another challenge was backend debugging. When a frontend request did not work as expected, I had to check multiple layers such as API Gateway configuration, Lambda logs, DynamoDB data, IAM permissions, and CORS settings. After becoming more familiar with CloudWatch Logs, I could identify issues faster and test the system step by step.

Documentation also took considerable time because the Worklog, Proposal, Blogs Posted, Workshop, Self-Assessment, and Sharing and Feedback sections needed to be consistent with one another. When the architecture or project content changed, related documentation sections also had to be updated to avoid inconsistency.

## Feedback and Suggestions

From my experience, the workshop-based learning format is suitable for students because it combines theory with hands-on practice. However, to learn more effectively, learners should record errors while implementing, capture screenshots after important steps, and update the architecture diagram whenever the project changes.

I also realized that cleanup and Billing Dashboard monitoring should be prepared carefully. New AWS learners may focus on creating resources and forget to check whether resources are still running after practice. Cost monitoring should become a habit from the beginning.

If I continue developing this project, I would improve the following parts:

- Build a dashboard for ticket statistics by status, priority, and category.
- Improve the admin interface so filtering and handling tickets become clearer.
- Add audit logs for administrator actions.
- Complete custom domain configuration if the account and domain verification process allow it.
- Refine IAM policies so service-to-service permissions are more strictly controlled.

## Conclusion

Overall, the internship gave me a more practical view of how to build a serverless application on AWS. I not only learned how to use individual AWS services, but also understood system flow design, access control, error monitoring, cost management, and technical documentation. This experience gave me a stronger foundation to continue learning cloud computing and building AWS projects in the future.
