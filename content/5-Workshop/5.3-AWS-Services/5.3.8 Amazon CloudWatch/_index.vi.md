---
title : "Amazon CloudWatch"
date : 2026-07-21
weight : 8
chapter : false
pre : " <b> 5.3.8 </b> "
---

# Amazon CloudWatch

## Giới thiệu

Amazon CloudWatch là dịch vụ giám sát và theo dõi của AWS, cho phép thu thập các chỉ số (Metrics), nhật ký (Logs) và dữ liệu vận hành từ các tài nguyên AWS. CloudWatch giúp theo dõi hiệu năng hệ thống, phát hiện lỗi và hỗ trợ phân tích hoạt động của ứng dụng theo thời gian thực.

Trong dự án Campus IT Support Portal, Amazon CloudWatch được sử dụng để giám sát các hàm AWS Lambda thông qua việc lưu trữ nhật ký thực thi và cung cấp khả năng theo dõi hoạt động của hệ thống.

---

## Dashboard CloudWatch

Amazon CloudWatch cung cấp giao diện tập trung để theo dõi các dịch vụ AWS, truy cập nhật ký hệ thống, chỉ số hiệu năng và các công cụ giám sát.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/cloudwatch-dashboard.png"
alt="Dashboard Amazon CloudWatch"
caption="Hình 5.3.8.1: Giao diện Dashboard của Amazon CloudWatch."
>}}

Dashboard đóng vai trò là điểm truy cập trung tâm giúp quản lý và giám sát các tài nguyên AWS.

---

## Log Groups

CloudWatch tự động tạo Log Group cho mỗi AWS Lambda sau khi hàm được triển khai và thực thi. Mỗi Log Group lưu trữ toàn bộ nhật ký của một Lambda Function.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/lambda-logs.png"
alt="CloudWatch Log Groups"
caption="Hình 5.3.8.2: Các Log Group được tạo cho các hàm AWS Lambda."
>}}

Trong dự án có nhiều Log Group tương ứng với các Lambda Function như CampusSupportTicketService, CampusSupportNotificationService, CampusSupportWebSocketService và CognitoPostConfirmationAddUserGroup.

---

## Log Streams

Bên trong mỗi Log Group là nhiều Log Stream, ghi lại từng lần thực thi của Lambda. Các bản ghi bao gồm thời gian thực thi, thông tin request và báo cáo hệ thống do CloudWatch tạo tự động.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.8-Amazon-CloudWatch/log-streams.png"
alt="CloudWatch Log Streams"
caption="Hình 5.3.8.3: Các Log Stream của hàm CampusSupportTicketService."
>}}

Các Log Stream cho thấy Lambda đã được thực thi thành công và cung cấp đầy đủ thông tin phục vụ việc theo dõi, kiểm tra và xử lý lỗi trong quá trình vận hành hệ thống.

---

## Kết quả

Amazon CloudWatch mang lại nhiều lợi ích cho dự án Campus IT Support Portal:

- Giám sát tập trung các dịch vụ AWS.
- Tự động lưu nhật ký thực thi của AWS Lambda.
- Hỗ trợ kiểm tra và xử lý lỗi nhanh chóng.
- Theo dõi liên tục hoạt động của hệ thống.
- Nâng cao độ ổn định và độ tin cậy của ứng dụng.