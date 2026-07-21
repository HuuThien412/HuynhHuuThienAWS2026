---
title : "Tổng kết"
date : 2026-07-21
weight : 10
chapter : false
pre : " <b> 5.3.10 </b> "
---

# Tổng kết

## Giới thiệu

Dự án Campus IT Support Portal được xây dựng theo kiến trúc serverless trên nền tảng Amazon Web Services (AWS). Trong quá trình phát triển, nhiều dịch vụ AWS đã được tích hợp nhằm đáp ứng các yêu cầu về xác thực người dùng, triển khai ứng dụng, xử lý nghiệp vụ, lưu trữ dữ liệu, quản lý tệp, giám sát hệ thống và bảo mật quyền truy cập.

Mỗi dịch vụ đảm nhận một vai trò riêng nhưng phối hợp chặt chẽ với nhau để tạo nên một hệ thống điện toán đám mây có khả năng mở rộng, ổn định và an toàn.

---

## Tổng quan các dịch vụ AWS

Dự án sử dụng các dịch vụ AWS sau:

- **AWS Amplify Hosting** triển khai và lưu trữ ứng dụng frontend.
- **Amazon Cognito** quản lý xác thực và phân quyền người dùng.
- **Amazon API Gateway** cung cấp các REST API kết nối giữa frontend và backend.
- **AWS Lambda** xử lý toàn bộ logic nghiệp vụ theo kiến trúc serverless.
- **Amazon DynamoDB** lưu trữ thông tin ticket và dữ liệu của hệ thống.
- **Amazon S3** lưu trữ tệp đính kèm và các tài nguyên tĩnh.
- **Amazon SES** hỗ trợ gửi email thông báo.
- **Amazon CloudWatch** giám sát hoạt động của hệ thống và lưu trữ nhật ký thực thi.
- **AWS Identity and Access Management (IAM)** quản lý danh tính và phân quyền giữa các dịch vụ AWS.

Sự kết hợp của các dịch vụ trên tạo thành một kiến trúc serverless hoàn chỉnh, giúp giảm thiểu việc quản lý hạ tầng đồng thời nâng cao khả năng mở rộng và tính sẵn sàng của hệ thống.

---

## Lợi ích của kiến trúc

Việc kết hợp các dịch vụ AWS mang lại nhiều lợi ích cho dự án Campus IT Support Portal:

- Kiến trúc serverless được quản lý hoàn toàn.
- Khả năng mở rộng tự động theo nhu cầu sử dụng.
- Xác thực và phân quyền người dùng an toàn.
- Lưu trữ dữ liệu và tệp tin hiệu quả.
- Giám sát hệ thống và hỗ trợ xử lý lỗi nhanh chóng.
- Quản lý quyền truy cập an toàn thông qua IAM Roles.
- Giảm chi phí vận hành và bảo trì hệ thống.
- Nâng cao tính ổn định và độ tin cậy của ứng dụng.

Việc tích hợp các dịch vụ AWS giúp hệ thống hoạt động hiệu quả, đồng thời tuân thủ các khuyến nghị của AWS về bảo mật, khả năng mở rộng và phát triển ứng dụng trên nền tảng điện toán đám mây.

---

## Tổng kết

Các dịch vụ AWS được trình bày trong Workshop đã phối hợp với nhau để xây dựng kiến trúc serverless cho dự án Campus IT Support Portal.

Thông qua việc kết hợp AWS Amplify Hosting, Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, Amazon SES, Amazon CloudWatch và AWS IAM, dự án đã xây dựng được một môi trường điện toán đám mây an toàn, linh hoạt và dễ mở rộng. Đây là nền tảng quan trọng để tiếp tục phát triển và bổ sung các chức năng mới cho hệ thống trong tương lai.