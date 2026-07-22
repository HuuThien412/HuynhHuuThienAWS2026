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

Hệ thống sau khi triển khai cho phép người dùng đăng ký, đăng nhập, gửi ticket hỗ trợ, upload file đính kèm, theo dõi lịch sử ticket và nhận cập nhật trạng thái. Quản trị viên có thể xem toàn bộ ticket, tìm kiếm và lọc yêu cầu, cập nhật trạng thái, thêm ghi chú xử lý, xóa ticket và nhận cảnh báo khi có ticket ưu tiên cao.

Frontend được triển khai công khai bằng **AWS Amplify Hosting** và được kết nối với GitHub để tự động build/deploy khi có thay đổi mã nguồn.

#### Kiến trúc

Hệ thống sử dụng kiến trúc serverless trên AWS. Frontend tích hợp với **Amazon Cognito** để xác thực người dùng và gửi các request đã xác thực đến **Amazon API Gateway**. API Gateway kiểm tra Cognito JWT token trước khi chuyển request đến các hàm **AWS Lambda**.

Lambda xử lý nghiệp vụ ticket, kiểm tra quyền truy cập, xử lý tệp đính kèm và tích hợp với **Amazon DynamoDB** cùng **Amazon S3**. Hệ thống cũng sử dụng **Amazon SES**, **Amazon CloudWatch**, **AWS IAM** và các thành phần cập nhật thời gian thực như DynamoDB Streams và WebSocket API.

{{< project-image
src="images/5-Workshop/5.2-System-Architecture/Architecture.jpg"
alt="Kiến trúc Campus IT Support Ticket Portal"
caption="Kiến trúc Campus IT Support Ticket Portal"
>}}

#### Các dịch vụ AWS sử dụng

| Dịch vụ | Vai trò trong workshop |
| --- | --- |
| AWS Amplify Hosting | Host frontend và tự động deploy thay đổi từ GitHub |
| Amazon Cognito | Xử lý đăng ký, đăng nhập, đăng xuất, JWT token và group `Users`/`Admins` |
| Amazon API Gateway | Cung cấp HTTP API và WebSocket API để frontend giao tiếp với backend |
| AWS Lambda | Xử lý nghiệp vụ ticket, kiểm tra quyền, thông báo và sự kiện WebSocket |
| Amazon DynamoDB | Lưu dữ liệu ticket và thông tin kết nối WebSocket |
| Amazon S3 | Lưu file đính kèm của ticket trong bucket riêng tư |
| Amazon SES | Gửi email xác nhận ticket, cảnh báo và thông báo thay đổi trạng thái |
| Amazon CloudWatch | Lưu log Lambda/API và hỗ trợ debug, giám sát hệ thống |
| AWS IAM | Cấp quyền least privilege giữa Lambda và các dịch vụ AWS khác |

#### Nội dung

1. [Tổng quan dự án](5.1-project-overview/)
2. [Kiến trúc hệ thống](5.2-system-architecture/)
3. [Các dịch vụ AWS](5.3-aws-services/)
   - [AWS Amplify Hosting](5.3-aws-services/5.3.1-aws-amplify-hosting/)
   - [Amazon Cognito](5.3-aws-services/5.3.2-amazon-cognito/)
   - [Amazon API Gateway](5.3-aws-services/5.3.3-amazon-api-gateway/)
   - [AWS Lambda](5.3-aws-services/5.3.4-aws-lambda/)
   - [Amazon DynamoDB](5.3-aws-services/5.3.5-amazon-dynamodb/)
   - [Amazon S3](5.3-aws-services/5.3.6-amazon-s3/)
   - [Amazon SES](5.3-aws-services/5.3.7-amazon-ses/)
   - [Amazon CloudWatch](5.3-aws-services/5.3.8-amazon-cloudwatch/)
   - [AWS IAM](5.3-aws-services/5.3.9-aws-iam/)
   - [Tổng kết](5.3-aws-services/5.3.10-summary/)
