---
title: "Lưu trữ dữ liệu với DynamoDB và S3"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

### Mục tiêu

Lưu dữ liệu ticket trong DynamoDB và lưu file đính kèm của ticket trong Amazon S3.

### DynamoDB table

Tạo DynamoDB table để lưu dữ liệu ticket.

| Thuộc tính | Mục đích |
| --- | --- |
| `ticketId` | Mã ticket duy nhất |
| `userId` | Mã người dùng từ Cognito |
| `email` | Email người gửi |
| `category` | Nhóm sự cố |
| `priority` | Mức độ ưu tiên |
| `description` | Mô tả lỗi |
| `status` | Trạng thái ticket |
| `adminNote` | Ghi chú xử lý của admin |
| `attachmentKey` | Object key của file upload trên S3 |
| `createdAt` | Thời điểm tạo |
| `updatedAt` | Thời điểm cập nhật gần nhất |

### S3 attachment bucket

1. Tạo S3 bucket private để lưu file đính kèm.
2. Tắt public access.
3. Cấp quyền cho Lambda put/get object thông qua IAM.
4. Lưu file theo cấu trúc rõ ràng, ví dụ `tickets/{ticketId}/filename`.
5. Lưu S3 object key vào item ticket trong DynamoDB.

### IAM permissions

Lambda execution role nên dùng least privilege:

- DynamoDB: `PutItem`, `GetItem`, `Query`, `Scan`, `UpdateItem`, `DeleteItem`
- S3: `PutObject`, `GetObject`, `DeleteObject`
- CloudWatch Logs: ghi log

### Ảnh minh chứng cần có

- DynamoDB table và sample ticket item.
- S3 bucket có file đính kèm đã upload.
- Quyền của Lambda execution role.
