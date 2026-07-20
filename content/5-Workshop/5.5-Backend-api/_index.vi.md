---
title: "Backend API với API Gateway và Lambda"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Mục tiêu

Tạo tầng backend API để nhận request từ frontend, xác thực JWT token, invoke Lambda và xử lý nghiệp vụ ticket.

### Cấu hình API Gateway

1. Tạo API Gateway API.
2. Cấu hình các route cho nghiệp vụ ticket.
3. Bật CORS cho domain frontend của Amplify.
4. Cấu hình JWT Authorizer kết nối với Cognito User Pool.
5. Gắn authorizer vào các route cần bảo vệ.

### Cấu hình Lambda

1. Tạo Lambda function cho các thao tác ticket.
2. Đọc JWT claims từ request context.
3. Kiểm tra người gọi thuộc group `Users` hay `Admins`.
4. Validate dữ liệu request body.
5. Gọi DynamoDB để thao tác dữ liệu ticket.
6. Gọi S3 để xử lý file đính kèm.
7. Trả JSON response về API Gateway.

### API routes

| Method | Endpoint | Quyền | Mục đích |
| --- | --- | --- | --- |
| POST | `/tickets` | User/Admin | Tạo ticket |
| GET | `/tickets/my` | User | Xem ticket của mình |
| GET | `/tickets` | Admin | Xem toàn bộ ticket |
| GET | `/tickets/{ticketId}` | Owner/Admin | Xem chi tiết ticket |
| PATCH | `/tickets/{ticketId}` | Admin | Cập nhật trạng thái và ghi chú |
| DELETE | `/tickets/{ticketId}` | Admin | Xóa ticket |

### Ảnh minh chứng cần có

- Các route trong API Gateway.
- Cấu hình JWT Authorizer.
- Lambda function overview.
- Kết quả test API thành công.
