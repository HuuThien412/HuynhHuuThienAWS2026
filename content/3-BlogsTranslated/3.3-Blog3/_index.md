---
title: "Learning Serverless, Authentication, Monitoring, and Security on AWS"
date: 2026-07-03
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

After practicing core AWS services, I moved to serverless application tasks. This stage was important because it helped me understand how modern cloud applications can run without managing traditional servers. Instead of creating and maintaining EC2 instances for every backend feature, I learned how services such as API Gateway, Lambda, Cognito, DynamoDB, S3, CloudWatch, and IAM can work together.

The first serverless service I focused on was AWS Lambda. Lambda changed how I thought about backend processing. In a traditional approach, an application server runs continuously and waits for requests. With Lambda, the function runs only when it is invoked. This model is useful for event-driven workflows such as creating a ticket, updating a status, processing an uploaded file, or returning data to a frontend application.

While practicing Lambda, I learned to think in small functions. A good Lambda function should have a clear responsibility: validate input, process logic, call another AWS service, and return a response. I also learned that Lambda permissions are controlled by an execution role. If the function needs to write to DynamoDB, upload to S3, or write logs to CloudWatch, the IAM role must allow those actions.

The next major service was Amazon API Gateway. API Gateway helped me understand how a frontend application communicates with backend logic. I practiced defining routes, choosing HTTP methods, enabling CORS, and connecting routes to Lambda. This made REST API concepts more practical. A route such as `POST /tickets` is not only a URL. It represents a real workflow where the frontend sends data, API Gateway receives the request, Lambda processes it, and the response returns to the user.

Authentication was another important learning area. I studied Amazon Cognito because my project required user and admin access. Cognito helped me understand sign-up, sign-in, user pools, app clients, JWT tokens, and groups. At first, the token flow was confusing. The key point I learned is that Cognito authenticates the user and returns a JWT token to the frontend. Then the frontend includes that token when calling API Gateway. API Gateway can validate the token with a JWT Authorizer before invoking Lambda.

Role separation also became clearer through Cognito groups. A normal user should be able to submit tickets and view only their own tickets. An admin should be able to view all tickets, update status, add notes, and delete tickets. This is where authentication and authorization become different. Authentication confirms who the user is. Authorization decides what the user is allowed to do.

For data storage, I practiced Amazon DynamoDB. DynamoDB is different from relational databases because table design should start from access patterns. For a ticket portal, I needed to think about operations such as creating a ticket, viewing a user's own tickets, listing all tickets for admin, updating ticket status, and deleting a ticket. This helped me understand why NoSQL design should follow application queries.

I also used Amazon S3 for attachment storage. This task taught me that files and database records should be connected carefully. The file itself can be stored in S3, while the ticket item in DynamoDB stores metadata such as the S3 object key. This keeps the database lightweight while still allowing the application to find the related attachment.

Monitoring was another key part of the learning process. When something failed, CloudWatch Logs became the first place to check. I learned to look for Lambda invocation logs, validation errors, permission errors, and failed calls to DynamoDB or S3. This made debugging more systematic. Instead of guessing, I could check logs and understand where the request failed.

Security and cleanup were also important tasks. I reviewed IAM least privilege, CORS settings, private S3 buckets, and protected API routes. I also learned to clean up unused resources and check the Billing Dashboard. A cloud project is not complete when the feature works once. It should also be secure enough for its scope, observable through logs, and cleaned up to avoid unnecessary cost.

The biggest lesson from this stage is that serverless does not mean there is no architecture. It means the architecture is built from managed services. Each service has a responsibility, and the developer must connect them correctly. API Gateway handles API entry points, Lambda handles logic, Cognito handles identity, DynamoDB stores data, S3 stores files, CloudWatch records logs, and IAM controls permissions.

This learning stage helped me move from practicing individual services to understanding an end-to-end application workflow. It also prepared me to document a workshop clearly because every step had a purpose: deploy frontend, configure authentication, create API routes, write backend logic, store data, test user/admin flows, monitor logs, and clean up resources.

## References

- [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
- [Amazon API Gateway REST API documentation](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html)
- [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)
- [What is Amazon DynamoDB?](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
- [Sending Lambda logs to CloudWatch Logs](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html)
