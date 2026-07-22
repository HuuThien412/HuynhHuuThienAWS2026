---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Workshop Campus IT Support Ticket Portal

#### Tổng quan project

Workshop này ghi lại quá trình triển khai **Campus IT Support Ticket Portal**, một hệ thống web helpdesk serverless dùng để tiếp nhận và quản lý yêu cầu hỗ trợ kỹ thuật trong môi trường trường học.

Hệ thống sau khi triển khai cho phép người dùng đăng nhập, gửi ticket hỗ trợ, upload file đính kèm và theo dõi trạng thái ticket. Admin có thể xem toàn bộ ticket, lọc yêu cầu, cập nhật trạng thái, ghi chú xử lý và xóa ticket khi cần.

#### Kiến trúc

{{< project-image
src="images/5-Workshop/5.2-System-Architecture/Architecture.jpg"
alt="Kiến trúc Campus IT Support Ticket Portal"
caption="Kiến trúc Campus IT Support Ticket Portal"
>}}

#### Các dịch vụ AWS sử dụng

| Dịch vụ | Vai trò trong workshop |
| --- | --- |
| AWS Amplify Hosting | Host và deploy frontend từ GitHub |
| Amazon Cognito | Xử lý đăng ký, đăng nhập, JWT token và group `Users`/`Admins` |
| Amazon API Gateway | Cung cấp API endpoint và xác thực Cognito JWT token |
| AWS Lambda | Xử lý nghiệp vụ ticket và kiểm tra quyền truy cập |
| Amazon DynamoDB | Lưu dữ liệu ticket |
| Amazon S3 | Lưu file đính kèm của ticket |
| AWS IAM | Cấp quyền cho Lambda truy cập DynamoDB, S3 và CloudWatch |
| Amazon CloudWatch | Lưu log/metrics để debug |
| Amazon Route 53 | Đã thử đăng ký custom domain, nhưng hiện project dùng domain mặc định của Amplify |

#### Nội dung

1. [Kết quả project và kiến trúc](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Host frontend với AWS Amplify](5.3-Amplify-hosting/)
4. [Xác thực với Amazon Cognito](5.4-Cognito-authentication/)
5. [Backend API với API Gateway và Lambda](5.5-Backend-api/)
6. [Lưu trữ dữ liệu với DynamoDB và S3](5.6-Data-storage/)
7. [Kiểm thử, monitoring và cleanup](5.7-Testing-monitoring-cleanup/)
