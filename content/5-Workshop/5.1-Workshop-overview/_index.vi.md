---
title: "Kết quả project và kiến trúc"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Kết quả project

Project sau khi hoàn thành là một website IT support ticket portal được triển khai trên AWS. Hệ thống có hai giao diện chính:

| Giao diện | Chức năng chính |
| --- | --- |
| User Portal | Đăng nhập, gửi ticket, upload file đính kèm, xem ticket của mình |
| Admin Console | Xem toàn bộ ticket, lọc ticket, cập nhật trạng thái, ghi chú xử lý, xóa ticket |

### Luồng kiến trúc

1. User/Admin truy cập website thông qua HTTPS.
2. AWS Amplify phục vụ frontend UI.
3. Frontend chuyển người dùng đến Amazon Cognito để đăng ký/đăng nhập.
4. Cognito trả JWT token về frontend.
5. Frontend gửi API request kèm JWT token đến API Gateway.
6. API Gateway xác thực token và invoke Lambda.
7. Lambda tạo, đọc, cập nhật hoặc xóa dữ liệu ticket trong DynamoDB và lưu file đính kèm vào S3.

![Kiến trúc Campus IT Support Ticket Portal](/images/5-Workshop/ticket-portal-architecture.png)

### Kết quả mong đợi

Sau khi hoàn thành workshop, hệ thống cần hỗ trợ luồng user/admin đã xác thực, quản lý ticket, lưu file đính kèm, ghi log backend và có tài liệu cleanup.
