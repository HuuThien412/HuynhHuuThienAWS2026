---
title: "Data storage with DynamoDB and S3"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

### Goal

Store ticket records in DynamoDB and ticket attachment files in Amazon S3.

### DynamoDB table

Create a DynamoDB table for ticket data.

| Attribute | Purpose |
| --- | --- |
| `ticketId` | Unique ticket identifier |
| `userId` | Cognito user ID |
| `email` | Requester email |
| `category` | Issue category |
| `priority` | Ticket priority |
| `description` | Issue description |
| `status` | Ticket status |
| `adminNote` | Admin processing note |
| `attachmentKey` | S3 object key for uploaded file |
| `createdAt` | Creation timestamp |
| `updatedAt` | Last update timestamp |

### S3 attachment bucket

1. Create a private S3 bucket for attachments.
2. Disable public access.
3. Allow Lambda to put and get objects through IAM permissions.
4. Store uploaded files using a clear key structure such as `tickets/{ticketId}/filename`.
5. Save the S3 object key in the DynamoDB ticket item.

### IAM permissions

Lambda execution role should have least privilege access:

- DynamoDB: `PutItem`, `GetItem`, `Query`, `Scan`, `UpdateItem`, `DeleteItem`
- S3: `PutObject`, `GetObject`, `DeleteObject`
- CloudWatch Logs: write logs

### Screenshot evidence to include

- DynamoDB table and sample ticket item.
- S3 bucket with uploaded attachment.
- Lambda execution role permissions.
