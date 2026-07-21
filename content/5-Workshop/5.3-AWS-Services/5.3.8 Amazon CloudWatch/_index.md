---
title : "Amazon CloudWatch"
date : 2026-07-21
weight : 8
chapter : false
pre : " <b> 5.3.8 </b> "
---

# Amazon CloudWatch

## Introduction

Amazon CloudWatch is a monitoring and observability service provided by AWS that collects metrics, logs, and operational data from AWS resources. It enables developers to monitor application performance, troubleshoot issues, and analyze system behavior in real time.

In the Campus IT Support Portal project, Amazon CloudWatch is used to monitor AWS Lambda functions by collecting execution logs and providing operational visibility for the deployed services.

---

## CloudWatch Dashboard

Amazon CloudWatch provides a centralized dashboard where developers can access monitoring services, logs, metrics, and alarms from AWS resources.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/cloudwatch-dashboard.png"
alt="Amazon CloudWatch dashboard"
caption="Figure 5.3.8.1: Amazon CloudWatch dashboard."
>}}

The dashboard serves as the entry point for monitoring AWS services and managing application observability.

---

## Log Groups

CloudWatch automatically creates Log Groups for AWS Lambda functions after they are deployed and executed. Each Log Group stores execution records for an individual Lambda function.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/lambda-logs.png"
alt="CloudWatch Log Groups"
caption="Figure 5.3.8.2: Log Groups created for AWS Lambda functions."
>}}

The project contains multiple Log Groups corresponding to the deployed Lambda functions, including CampusSupportTicketService, CampusSupportNotificationService, CampusSupportWebSocketService, and CognitoPostConfirmationAddUserGroup.

---

## Log Streams

Each Log Group contains multiple Log Streams that record every Lambda invocation. These logs include execution details such as timestamps, request information, execution duration, and system-generated reports.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/log-streams.png"
alt="CloudWatch Log Streams"
caption="Figure 5.3.8.3: Log Streams of the CampusSupportTicketService Lambda function."
>}}

The Log Streams confirm that the Lambda function has been executed successfully and provide detailed information for debugging and monitoring application behavior.

---

## Results

Amazon CloudWatch provides several important benefits for the Campus IT Support Portal:

- Centralized monitoring of AWS resources.
- Automatic collection of Lambda execution logs.
- Easier debugging and troubleshooting.
- Continuous monitoring of deployed services.
- Improved system reliability through operational visibility.