---
title: "Amazon DynamoDB"
date: 2026-07-21
weight: 5
chapter: false
pre: "<b>5.3.5 </b>"
---

# Amazon DynamoDB

## Introduction

Amazon DynamoDB is the primary NoSQL database used by the Campus IT Support Ticket Portal.

The service stores all ticket information, user requests, and WebSocket connection data. As a fully managed database, DynamoDB provides low-latency performance, automatic scaling, and high availability without requiring server administration.

---

## Role in the Project

Amazon DynamoDB is responsible for:

- Storing support ticket information.
- Maintaining ticket status throughout its lifecycle.
- Recording user information submitted with each request.
- Storing WebSocket connection IDs for real-time notifications.
- Providing fast data access for AWS Lambda functions.
- Supporting automatic scaling based on application traffic.

---

## DynamoDB Tables

The project uses two DynamoDB tables.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/dynamodb-tables.png"
alt="Amazon DynamoDB tables"
caption="Figure 5.3.5.1: Amazon DynamoDB tables used in the Campus IT Support Ticket Portal."
>}}

The tables include:

- **CampusSupportTickets** – stores all IT support tickets.
- **CampusSupportConnections** – stores WebSocket connection IDs used for real-time notifications.

Each table is designed for a specific responsibility, improving maintainability and system performance.

---

## Ticket Table Overview

The CampusSupportTickets table stores all information related to submitted support tickets.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/ticket-table-overview.png"
alt="CampusSupportTickets table overview"
caption="Figure 5.3.5.2: Overview of the CampusSupportTickets DynamoDB table."
>}}

The table uses **ticketId** as the partition key and operates in **On-Demand** capacity mode, allowing DynamoDB to automatically adjust throughput according to application traffic.

The overview also displays the table status, item count, storage size, and resource ARN.

---

## Ticket Records

Support requests submitted by users are stored as items inside the CampusSupportTickets table.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/ticket-items.png"
alt="Ticket records stored in DynamoDB"
caption="Figure 5.3.5.3: Ticket records stored in the CampusSupportTickets table."
>}}

Each record contains information such as:

- Ticket ID
- Full name
- Email
- Category
- Description
- Location
- Priority
- Status
- Created date
- Attachment information

AWS Lambda performs Create, Read, Update, and Delete (CRUD) operations on these records through the AWS SDK.

---

## Monitoring

Amazon DynamoDB integrates directly with Amazon CloudWatch for monitoring.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/dynamodb-monitoring.png"
alt="Amazon DynamoDB monitoring"
caption="Figure 5.3.5.4: Amazon CloudWatch monitoring for the DynamoDB table."
>}}

CloudWatch provides operational metrics including:

- Read capacity usage
- Write capacity usage
- Read throttled requests
- Write throttled requests
- Consumed throughput
- Table performance

These metrics help monitor database health and identify potential performance issues.

---

## Results

Amazon DynamoDB provides the following benefits:

- Fully managed NoSQL database service.
- Automatic scaling using On-Demand capacity mode.
- Low-latency data access.
- Seamless integration with AWS Lambda.
- High availability and durability.
- Built-in monitoring through Amazon CloudWatch.