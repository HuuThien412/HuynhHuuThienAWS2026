---
title: "Chuẩn bị"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

### Tài khoản và công cụ cần có

Trước khi triển khai, cần chuẩn bị:

- AWS account có quyền sử dụng Amplify, Cognito, API Gateway, Lambda, DynamoDB, S3, IAM và CloudWatch.
- GitHub repository chứa source code frontend.
- Môi trường local có Git, Node.js và code editor.
- Kiến thức cơ bản về serverless architecture và REST API.

### Checklist cấu hình AWS

| Hạng mục | Mục đích |
| --- | --- |
| AWS Region | Triển khai tài nguyên cùng region nếu có thể |
| IAM permissions | Cho phép Lambda truy cập DynamoDB, S3 và CloudWatch |
| Cognito User Pool | Lưu tài khoản và group người dùng |
| DynamoDB table | Lưu dữ liệu ticket |
| S3 bucket | Lưu file đính kèm |
| Amplify app | Host website frontend |

### Quy ước đặt tên

Nên dùng tên tài nguyên rõ ràng:

- `campus-ticket-user-pool`
- `campus-ticket-table`
- `campus-ticket-attachments`
- `campus-ticket-api`
- `campus-ticket-backend`
