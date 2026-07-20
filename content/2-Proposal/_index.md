---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Campus IT Support Ticket Portal
## A Serverless Helpdesk System on AWS for Campus IT Support

---

### 1. Executive Summary

Campus IT Support Ticket Portal is a web-based system for receiving, tracking, and resolving IT support requests in a school or university environment. The system allows students and staff to sign in, submit IT support tickets, track ticket status, and attach supporting files such as screenshots. It also provides an admin console for IT staff to view ticket lists, filter tickets, update status, add resolution notes, and delete tickets when needed.

The system is built with a serverless architecture on AWS. This approach reduces server management, supports easier scaling, and fits modern web applications with event-driven traffic.

The project can be implemented as an individual or group project. In this report, the focus is on the AWS architecture, authentication flow, backend processing, data storage, monitoring, and documentation of the system.

---

### 2. Problem Statement

#### The Problem

In many campus environments, IT support requests are reported through direct messages, phone calls, email, or in-person conversations. This creates several issues:

- Requests can be forgotten, duplicated, or handled without a clear record.
- IT staff do not have a centralized queue for prioritizing incidents.
- Users cannot easily track whether their issue is new, being processed, resolved, or closed.
- Admins need a clear way to review ticket details, update status, and record resolution notes.
- File evidence such as screenshots is often sent separately, making the support process harder to manage.

#### The Solution

Campus IT Support Ticket Portal solves these issues by providing a centralized helpdesk system with two main roles:

- **Users**: Sign in, submit support tickets, upload attachments, and track their own tickets.
- **Admins**: View all tickets, filter and inspect details, update status, add notes, and delete tickets.

The application uses AWS managed services to handle hosting, authentication, API routing, backend logic, database storage, file storage, access control, and monitoring.

---

### 3. Solution Architecture

#### Overall Architecture Diagram

```text
[User/Admin Browser]
        |
        v
[AWS Amplify Hosting]
        |
        v
[Amazon Cognito User Pool]
        |
        v
[Amazon API Gateway + JWT Authorizer]
        |
        v
[AWS Lambda Backend]
        |----------------------|
        v                      v
[Amazon DynamoDB]        [Amazon S3]
        |
        v
[Amazon CloudWatch Logs]

[Amazon Route 53] was tested for custom domain registration,
but the website currently uses the default AWS Amplify domain.
```

#### AWS Services Used

| Service | Role in System |
| --- | --- |
| **AWS Amplify Hosting** | Deploys and hosts the frontend; connects with GitHub and automatically builds/deploys changes |
| **Amazon Cognito** | Manages user registration, login, authentication, and role-based access using `Users` and `Admins` groups |
| **Amazon API Gateway** | Provides API endpoints and validates Cognito JWT tokens through a JWT Authorizer |
| **AWS Lambda** | Handles backend logic such as creating tickets, listing tickets, updating status, adding notes, deleting tickets, and checking user permissions |
| **Amazon DynamoDB** | Stores ticket records including requester information, category, priority, description, status, timestamps, and admin notes |
| **Amazon S3** | Stores ticket attachments such as screenshots or supporting documents |
| **AWS IAM** | Controls permissions between Lambda, DynamoDB, S3, API Gateway, and other AWS services |
| **Amazon CloudWatch** | Stores logs and supports backend debugging, request tracing, and error investigation |
| **Amazon Route 53** | Tested for custom domain registration; deployment currently uses the default Amplify domain due to registrar/account validation issues |

#### User Groups and Permissions

| Group | Permission Scope |
| --- | --- |
| **Users** | Submit tickets, upload attachments, and view their own tickets |
| **Admins** | View all tickets, filter ticket lists, update status, add resolution notes, and delete tickets |

---

### 4. Main System Flow

#### User Flow

1. A user accesses the website hosted on AWS Amplify.
2. The user signs up or signs in through Amazon Cognito.
3. The user submits an IT support ticket with issue category, priority, description, and optional attachment.
4. API Gateway validates the Cognito JWT token using a JWT Authorizer.
5. Lambda processes the request, stores ticket data in DynamoDB, and uploads the attachment to S3 if included.
6. The user can track the ticket status from the User Portal.

#### Admin Flow

1. An admin signs in with an account belonging to the `Admins` Cognito group.
2. The admin opens the Admin Console.
3. API Gateway validates the JWT token and Lambda checks the admin group claim.
4. The admin can view ticket lists, filter by status or priority, open ticket details, update processing status, add notes, or delete tickets.
5. Lambda writes updates to DynamoDB and sends logs to CloudWatch.

---

### 5. Ticket Data Model

| Attribute | Description |
| --- | --- |
| `ticketId` | Unique ticket identifier |
| `userId` | Cognito user identifier of the requester |
| `fullName` | Name of requester |
| `email` | Requester email |
| `category` | Issue category such as WiFi, account, software, hardware, or device |
| `priority` | Ticket priority: LOW, MEDIUM, HIGH, URGENT |
| `location` | Campus location where the issue occurs |
| `description` | Detailed issue description |
| `status` | Current ticket status: NEW, IN_PROGRESS, RESOLVED, CLOSED |
| `adminNote` | IT staff note or resolution summary |
| `attachmentKey` | S3 object key for uploaded file, if available |
| `createdAt` | Ticket creation timestamp |
| `updatedAt` | Last update timestamp |

---

### 6. API Design

| Method | Endpoint | Permission | Purpose |
| --- | --- | --- | --- |
| `POST` | `/tickets` | User/Admin | Create a new support ticket |
| `GET` | `/tickets` | Admin | List all tickets in the admin console |
| `GET` | `/tickets/my` | User | List tickets submitted by the signed-in user |
| `GET` | `/tickets/{ticketId}` | Owner/Admin | View ticket detail |
| `PATCH` | `/tickets/{ticketId}` | Admin | Update ticket status and admin note |
| `DELETE` | `/tickets/{ticketId}` | Admin | Delete a ticket |

#### Ticket Status Flow

```text
NEW -> IN_PROGRESS -> RESOLVED -> CLOSED
```

---

### 7. Implementation Plan

| Phase | Content | Timeline |
| --- | --- | --- |
| **Week 1-2** | Study AWS basics, prepare local environment, and define project requirements | Month 1 |
| **Week 3-4** | Design User Portal and Admin Console; prepare frontend repository and Amplify deployment | Month 1 |
| **Week 5-6** | Configure Cognito User Pool, user groups, DynamoDB table, and S3 attachment bucket | Month 2 |
| **Week 7-8** | Build Lambda backend and API Gateway endpoints with JWT Authorizer | Month 2 |
| **Week 9-10** | Implement admin management flow, user ticket tracking, file attachment handling, and CloudWatch logging | Month 3 |
| **Week 11-12** | Test end-to-end workflow, document deployment, review IAM/security, and complete cleanup notes | Month 3 |

---

### 8. Testing Plan

| Test Case | Expected Result |
| --- | --- |
| User signs up and signs in | Cognito creates and authenticates the user successfully |
| User submits a valid ticket | Ticket is stored in DynamoDB |
| User uploads an attachment | File is uploaded to S3 and linked to the ticket |
| User views own tickets | Only the user's tickets are returned |
| Admin opens ticket list | All tickets are displayed in the admin console |
| Admin updates ticket status | DynamoDB record is updated successfully |
| Admin deletes a ticket | Ticket is removed from DynamoDB |
| Invalid or missing JWT token | API Gateway rejects the request |
| Non-admin user calls admin API | Lambda denies the operation |
| Backend error occurs | Error details are available in CloudWatch Logs |

---

### 9. Budget Estimation

**Estimated monthly AWS costs for a small demo environment:**

| Service | Estimated Cost/Month | Notes |
| --- | --- | --- |
| AWS Amplify Hosting | ~$0-2 | Static frontend hosting with small traffic |
| Amazon Cognito | ~$0 | Free tier is enough for demo users |
| Amazon API Gateway | ~$0-2 | Low API request volume |
| AWS Lambda | ~$0-1 | Serverless backend runs only when requested |
| Amazon DynamoDB | ~$0-2 | Small ticket dataset with on-demand usage |
| Amazon S3 | ~$0-1 | Small attachment files |
| Amazon CloudWatch | ~$0-1 | Basic Lambda/API logs |
| Amazon Route 53 | Variable | Custom domain was tested but not completed |
| **Total** | **~$0-10/month** | Depends on traffic, storage, and domain usage |

---

### 10. Risk Assessment

| Risk | Impact | Probability | Mitigation Strategy |
| --- | --- | --- | --- |
| Incorrect Cognito group permissions | High | Medium | Validate `Users` and `Admins` claims in Lambda |
| API is called without a valid token | Medium | Medium | Use API Gateway JWT Authorizer |
| Lambda permission is too broad | High | Medium | Apply least privilege IAM roles for DynamoDB and S3 |
| S3 attachments expose sensitive files | High | Low | Keep bucket private and access files only through controlled backend logic |
| DynamoDB query pattern is inefficient | Medium | Medium | Define access patterns early and add indexes if needed |
| CORS configuration blocks frontend calls | Medium | Medium | Configure API Gateway CORS for the Amplify frontend domain |
| Route 53 custom domain registration fails | Low | Medium | Use Amplify default domain until account/domain validation is resolved |
| Forgotten resources create cost | Medium | Medium | Document cleanup steps and monitor Billing Dashboard |

---

### 11. Expected Outcomes

**Completed Results:**

- Frontend deployed with AWS Amplify Hosting.
- User registration and login handled by Amazon Cognito.
- User/admin authorization separated through Cognito groups.
- API Gateway validates JWT tokens before forwarding requests.
- Lambda backend handles ticket creation, lookup, update, deletion, and permission checks.
- DynamoDB stores ticket data.
- S3 stores ticket attachments.
- CloudWatch logs support troubleshooting and debugging.
- Route 53 custom domain registration was tested, but the system currently uses the default Amplify domain.

**Project Value:**

- The project simulates a realistic campus helpdesk workflow.
- Serverless architecture reduces infrastructure management.
- The system can be extended with email notifications, richer admin analytics, and a custom domain after Route 53 validation is resolved.
