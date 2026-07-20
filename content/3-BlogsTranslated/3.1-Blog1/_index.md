---
title: "Learning AWS from Account Setup, IAM, and Cost Control"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

When I first started learning AWS, I realized that the first useful lesson was not about building a large system immediately. The first lesson was learning how to work safely inside a cloud account. AWS gives learners access to many powerful services, but that also means a student must understand account setup, billing, permissions, and basic resource management from the beginning.

My first learning task was creating and preparing an AWS account. After signing in, I spent time exploring the AWS Management Console. At first, the console felt large because each service has its own page, settings, and terminology. I learned to search for services, check the selected region, open service dashboards, and recognize common areas such as EC2, S3, IAM, Billing, and CloudWatch. This basic navigation made later tasks much easier because I could move around the AWS environment with more confidence.

The second important task was billing awareness. In a local development environment, mistakes usually cost time. In cloud computing, mistakes can also create real cost. Because of that, I learned to check the Billing Dashboard and AWS Free Tier usage regularly. I also paid attention to which services could generate charges if resources were left running. EC2 instances, NAT Gateways, Route 53 domains, load balancers, and stored data are examples of resources that should not be ignored after testing. This habit helped me understand that cost control is part of cloud engineering, not just an administrative task.

Another early lesson was IAM. IAM is one of the most important services in AWS because it controls who can access which resources. I learned the difference between users, groups, roles, and policies. At the beginning, it was tempting to think that broad permissions would make development easier. However, AWS best practices encourage least privilege: each identity or service should only have the permissions it needs. This idea became more important later when I worked with Lambda, DynamoDB, S3, and API Gateway.

For example, if a Lambda function only needs to write ticket data to a DynamoDB table, it should not have full administrator permissions. If a function uploads files to an S3 bucket, the IAM role should be limited to the required bucket and required actions. Learning IAM early helped me understand why security must be planned from the start, even in a student project.

I also practiced simple EC2 tasks during the early stage. Creating and deleting an EC2 instance helped me understand the idea of virtual servers in AWS. I learned about AMI, instance type, key pair, and security group. Even though my later project focused more on serverless services, EC2 was still useful because it gave me a clear picture of traditional compute before comparing it with serverless compute.

One more topic I explored was Amazon Bedrock. I did not use Bedrock as the core service of my final project, but learning about it helped me understand how AWS also provides managed AI services. This was useful because it showed that AWS is not only infrastructure. It also includes higher-level services that can support modern application development.

The main lesson from this first stage is simple: before building applications on AWS, learners should understand the account environment. A good AWS learning process starts with safe account usage, billing control, IAM awareness, and basic console navigation. These skills may look simple, but they prevent many common mistakes later.

For me, this stage built the foundation for the rest of the internship. After learning how to navigate the console, monitor cost, and think about permissions, I was more prepared to practice core services and eventually build a serverless ticket portal project.

## References

- [Getting started with AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/getting-started-with-aws.html)
- [AWS Management Console](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-is.html)
- [AWS Billing and Cost Management](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
