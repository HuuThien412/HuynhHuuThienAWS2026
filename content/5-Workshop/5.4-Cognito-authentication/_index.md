---
title: "Authentication with Amazon Cognito"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Goal

Configure Amazon Cognito so users can sign up, sign in, and receive JWT tokens. The system uses groups to separate normal users and admins.

### Implementation steps

1. Create a Cognito User Pool.
2. Configure sign-in options such as email-based login.
3. Create two groups: `Users` and `Admins`.
4. Create test accounts for a normal user and an admin.
5. Add the admin account to the `Admins` group.
6. Configure the frontend to use the Cognito User Pool ID and App Client ID.
7. Test sign-up and sign-in from the frontend.

### Authorization behavior

| Group | Permission |
| --- | --- |
| Users | Submit tickets and view their own tickets |
| Admins | View all tickets, update ticket status, add notes, and delete tickets |

### Screenshot evidence to include

- Cognito User Pool overview.
- `Users` and `Admins` groups.
- Successful login screen.
