---
title: "Amazon Cognito"
date: 2026-07-21
weight: 2
chapter: false
pre: "<b>5.3.2 </b>"
---

# Amazon Cognito

## Introduction

Amazon Cognito is used as the authentication and authorization service for the **Campus IT Support Ticket Portal**. It provides a secure and scalable identity management solution without requiring the development of a custom authentication system.

In this project, Amazon Cognito is integrated with **AWS Amplify Hosting**, **Amazon API Gateway**, and **AWS Lambda** to ensure that only authenticated users can access protected resources and system functions.

---

## Role in the Project

Amazon Cognito is responsible for the following tasks:

- Managing user accounts.
- Providing user registration and sign-in through Hosted UI.
- Issuing JWT tokens after successful authentication.
- Managing user authorization with Cognito Groups.
- Integrating with Amazon API Gateway to protect backend APIs.
- Supplying authenticated user information to AWS Lambda.

---

## User Pool

The User Pool is the central identity store of the system.

Within this project, the User Pool is responsible for:

- Managing user accounts.
- Authenticating users.
- Issuing ID Token, Access Token, and Refresh Token.
- Maintaining user profile information.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/user-pool-overview.png"
alt="User Pool Overview"
caption="Figure 5.3.3: Amazon Cognito User Pool overview."
>}}
The figure above shows the User Pool used to manage application users, identity information, and authentication settings.

---

## Cognito Groups

To implement role-based authorization, the project defines two Cognito Groups:

- **Users** – Regular users who can submit and track support tickets.
- **Admins** – IT administrators who can manage, update, and delete tickets.

After a new account is confirmed, the Post Confirmation Lambda function automatically assigns the user to the **Users** group. Administrator accounts are assigned manually to the **Admins** group.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/user-groups.png"
alt="User Groups"
caption="Figure 5.3.4: User authorization using Amazon Cognito Groups."
>}}

Group information is embedded in the JWT token and later used by AWS Lambda to verify user permissions before performing administrative operations.

---

## App Client

The Amazon Cognito App Client represents the frontend application.

It is responsible for:

- Redirecting users to the Hosted UI.
- Receiving JWT tokens after authentication.
- Maintaining authenticated user sessions.
- Supporting user sign-out.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/app-client.png"
alt="App Client"
caption="Figure 5.3.5: Amazon Cognito App Client configuration."
>}}

The App Client serves as the communication bridge between the frontend application and Amazon Cognito during the authentication process.

---

## Hosted UI

The project uses the **Amazon Cognito Hosted UI** to provide a secure sign-in and registration interface.

After successful authentication, Cognito automatically redirects users back to the frontend application and returns the required JWT tokens.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/hosted-ui.png"
alt="Hosted UI"
caption="Figure 5.3.6: Amazon Cognito Hosted UI used for user authentication."
>}}

Using the Hosted UI significantly reduces development effort because a custom authentication interface is not required while maintaining AWS security best practices.

---

## Results

After integrating Amazon Cognito, the system achieved the following results:

- Secure user registration and authentication.
- Automatic JWT token generation after successful login.
- Protected backend APIs through JWT Authorizer.
- Role-based authorization using Cognito Groups.
- No custom authentication server is required.
- Seamless integration with other AWS services.
- A scalable authentication architecture suitable for future system expansion.