---
title: "AWS Lambda"
date: 2026-07-21
weight: 4
chapter: false
pre: "<b>5.3.4 </b>"
---

## Giới thiệu

AWS Lambda là nền tảng điện toán serverless được sử dụng để xử lý toàn bộ backend của hệ thống Campus IT Support Ticket Portal.

Thay vì triển khai và quản lý máy chủ, mỗi chức năng của hệ thống được xây dựng dưới dạng một Lambda Function và được kích hoạt tự động bởi các dịch vụ AWS như Amazon API Gateway, Amazon Cognito và DynamoDB Streams.

Kiến trúc này giúp hệ thống mở rộng tự động đồng thời giảm chi phí quản trị hạ tầng.

---

## Vai trò trong hệ thống

AWS Lambda chịu trách nhiệm:

- Xử lý các yêu cầu quản lý ticket.
- Thực thi business logic.
- Đọc và ghi dữ liệu trong Amazon DynamoDB.
- Upload tệp đính kèm lên Amazon S3.
- Xử lý Cognito Post Confirmation Trigger.
- Gửi thông báo thời gian thực qua WebSocket.
- Tích hợp với các dịch vụ AWS khác.

---

## Các Lambda Function

Hệ thống sử dụng nhiều Lambda Function để xử lý các chức năng khác nhau.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-functions.png"
alt="AWS Lambda functions"
caption="Hình 5.3.4.1: Các AWS Lambda Function của hệ thống Campus IT Support Ticket Portal."
>}}

Các Lambda Function bao gồm:

- CampusSupportTicketService
- CampusSupportNotificationService
- CampusSupportWebSocketService
- CognitoPostConfirmationAddUserGroup

Mỗi function đảm nhiệm một vai trò riêng và phối hợp với nhau thông qua các dịch vụ AWS.

---

## Tổng quan Function

CampusSupportTicketService là Lambda Function chính của hệ thống.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-overview.png"
alt="Lambda overview"
caption="Hình 5.3.4.2: Tổng quan Lambda Function CampusSupportTicketService."
>}}

Function này được kích hoạt bởi Amazon API Gateway và thực hiện toàn bộ nghiệp vụ xử lý ticket.

Trang tổng quan cũng hiển thị Lambda ARN, API Gateway Trigger và các tài nguyên liên quan.

---

## Mã nguồn

CampusSupportTicketService được phát triển bằng Node.js.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-code.png"
alt="Lambda source code"
caption="Hình 5.3.4.3: Mã nguồn của Lambda Function CampusSupportTicketService."
>}}

Mã nguồn sử dụng:

- AWS SDK v3
- Amazon DynamoDB
- Amazon S3
- JWT Authentication
- REST API Handler

Business logic thực hiện các chức năng tạo, cập nhật, truy vấn ticket, upload tệp và kiểm tra quyền truy cập.

---

## Cấu hình Function

Các tham số thực thi được cấu hình trong mục Configuration.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-configuration.png"
alt="Lambda configuration"
caption="Hình 5.3.4.4: Cấu hình thực thi của Lambda Function."
>}}

Các cấu hình chính bao gồm:

- Memory
- Timeout
- Temporary Storage
- Environment Variables
- IAM Execution Role

Các tham số này giúp Lambda hoạt động hiệu quả và đảm bảo khả năng mở rộng tự động.

---

## Giám sát

AWS Lambda tích hợp trực tiếp với Amazon CloudWatch.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.4-AWS-Lambda/lambda-monitoring.png"
alt="Lambda monitoring"
caption="Hình 5.3.4.5: Dashboard giám sát Lambda trên Amazon CloudWatch."
>}}

CloudWatch cung cấp các chỉ số:

- Số lần thực thi
- Thời gian xử lý
- Tỷ lệ lỗi
- Concurrent Executions
- Throttling Events

Các chỉ số này hỗ trợ theo dõi hoạt động và xử lý sự cố của hệ thống.

---

## Kết quả

AWS Lambda mang lại các lợi ích sau:

- Backend serverless hoàn toàn.
- Tự động mở rộng theo lưu lượng truy cập.
- Tích hợp chặt chẽ với API Gateway, Cognito, DynamoDB và S3.
- Giảm chi phí quản trị máy chủ.
- Hỗ trợ giám sát thông qua Amazon CloudWatch.
