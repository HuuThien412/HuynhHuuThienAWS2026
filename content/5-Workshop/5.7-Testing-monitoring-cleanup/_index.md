---
title: "Testing, monitoring, and cleanup"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

### End-to-end testing

Test the main user and admin workflows after deployment.

| Test case | Expected result |
| --- | --- |
| User signs up/signs in | Cognito authenticates successfully |
| User submits a ticket | Ticket is created in DynamoDB |
| User uploads an attachment | File is stored in S3 |
| User views own tickets | Only the user's tickets are displayed |
| Admin opens ticket list | Admin can see all tickets |
| Admin updates status | Ticket status is updated |
| Admin deletes ticket | Ticket is removed |

### Monitoring

Use Amazon CloudWatch to review backend behavior:

- Lambda invocation logs.
- API errors.
- Request payload validation issues.
- DynamoDB or S3 permission errors.

### Route 53 note

Amazon Route 53 custom domain registration was tested, but the process was not completed because of registrar/account validation issues. The project currently uses the default AWS Amplify domain.

### Cleanup

To avoid unnecessary cost:

1. Delete test ticket data in DynamoDB.
2. Remove uploaded test files from S3.
3. Delete unused Lambda functions and API stages.
4. Review CloudWatch log retention.
5. Remove unused Cognito test users if needed.
6. Check AWS Billing Dashboard after cleanup.

### Screenshot evidence to include

- Successful user ticket submission.
- Admin dashboard with ticket list.
- CloudWatch logs.
- Billing dashboard after cleanup.
