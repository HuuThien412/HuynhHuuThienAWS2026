---
title: "Practicing Core AWS Services: EC2, S3, VPC, and Databases"
date: 2026-07-02
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

After becoming familiar with the AWS account and console, the next stage of my learning process was practicing core AWS services. I focused on services that appear in many cloud projects: Amazon EC2, Amazon S3, Amazon VPC, security groups, IAM, and database services such as Amazon RDS/Aurora. These tasks helped me understand the basic building blocks of cloud infrastructure.

The first service I practiced deeply was Amazon EC2. EC2 helped me understand how virtual servers are created and managed in AWS. When launching an instance, I had to choose an AMI, instance type, key pair, network setting, and security group. Each option taught a different concept. The AMI defines the operating system image, the instance type defines compute capacity, the key pair supports secure access, and the security group controls inbound and outbound traffic.

One practical lesson from EC2 was that cloud resources must be managed intentionally. Starting an instance is easy, but stopping or terminating unused instances is just as important. I learned to check instance state, public IP address, security group rules, and running cost. This practice helped me connect compute usage with cost control.

The next important service was Amazon S3. S3 is an object storage service, and it is used in many AWS workloads because it is simple, durable, and flexible. I practiced creating buckets, uploading objects, organizing files, and reviewing bucket permissions. Through this task, I learned that storage is not only about putting files somewhere. It also includes access control, naming, lifecycle thinking, and public access protection.

S3 also helped me understand why permissions matter. A bucket should not be public unless there is a clear reason. In most application use cases, files should be private and accessed through controlled application logic. Later, this idea became useful in my ticket portal project, where S3 can store attachment files while Lambda and IAM control how those files are accessed.

Another major topic was networking with Amazon VPC. At first, VPC felt more difficult than EC2 or S3 because it involves subnets, route tables, internet gateways, and security groups. However, practicing VPC tasks helped me understand how AWS resources communicate. A VPC is like an isolated network area in the cloud. Subnets divide the network, route tables define traffic paths, and security groups act as virtual firewalls for resources.

Learning VPC also helped me understand why network design affects security. If a resource does not need direct internet access, it should not be placed in a public path unnecessarily. Even though my final project used mostly serverless services, understanding VPC concepts was still valuable because many real systems use a mix of serverless, managed services, and networked resources.

I also practiced database concepts with Amazon RDS and Aurora. These services showed me how managed relational databases work on AWS. I learned that RDS reduces the need to manage database servers manually, but the user still needs to think about instance size, database engine, networking, backup, and security. This experience helped me compare relational databases with DynamoDB later.

The comparison between RDS and DynamoDB was one of the useful learning points. RDS is suitable when the application needs relational structure, SQL queries, joins, and traditional database behavior. DynamoDB is more suitable for simple access patterns, high scalability, and serverless applications. For a ticket system with predictable operations such as create, list, update, and delete, DynamoDB can be a simpler fit. But learning RDS first helped me understand why database choice depends on application requirements.

During this stage, I also kept practicing AWS Study Group workshops and taking notes. I learned that hands-on tasks are more effective than only reading documentation. When I created a resource, configured it, tested it, broke it, and fixed it, the service became much easier to remember. The mistakes were useful too. For example, a blocked connection often pointed back to a security group rule, and a failed access attempt often pointed back to IAM permission.

The main value of this stage was building practical confidence. EC2 taught compute. S3 taught object storage and permissions. VPC taught networking and isolation. RDS/Aurora taught managed relational databases. IAM and Billing connected all of these tasks to security and cost awareness.

By the end of this learning stage, I had a clearer view of how AWS infrastructure is organized. This foundation made it easier to move to serverless services and build a real application flow using API Gateway, Lambda, Cognito, DynamoDB, S3, and CloudWatch.

## References

- [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- [What is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [What is Amazon VPC?](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [Amazon RDS User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
- [Amazon Aurora User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)
