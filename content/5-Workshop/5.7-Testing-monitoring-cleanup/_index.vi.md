---
title: "Kiểm thử, monitoring và cleanup"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

### Kiểm thử end-to-end

Kiểm thử các luồng user và admin chính sau khi deploy.

| Test case | Kết quả mong đợi |
| --- | --- |
| User đăng ký/đăng nhập | Cognito xác thực thành công |
| User gửi ticket | Ticket được tạo trong DynamoDB |
| User upload file đính kèm | File được lưu trong S3 |
| User xem ticket của mình | Chỉ hiển thị ticket của user đó |
| Admin mở danh sách ticket | Admin xem được toàn bộ ticket |
| Admin cập nhật trạng thái | Trạng thái ticket được cập nhật |
| Admin xóa ticket | Ticket được xóa khỏi hệ thống |

### Monitoring

Dùng Amazon CloudWatch để kiểm tra hoạt động backend:

- Log invocation của Lambda.
- Lỗi API.
- Lỗi validate request payload.
- Lỗi permission khi truy cập DynamoDB hoặc S3.

### Ghi chú Route 53

Amazon Route 53 custom domain đã được thử nghiệm, nhưng quá trình đăng ký chưa hoàn tất do lỗi registrar/account validation. Project hiện sử dụng domain mặc định của AWS Amplify.

### Cleanup

Để tránh phát sinh chi phí không cần thiết:

1. Xóa dữ liệu ticket test trong DynamoDB.
2. Xóa file test đã upload trong S3.
3. Xóa Lambda function và API stage không dùng.
4. Kiểm tra CloudWatch log retention.
5. Xóa Cognito test users nếu cần.
6. Kiểm tra AWS Billing Dashboard sau khi cleanup.

### Ảnh minh chứng cần có

- User gửi ticket thành công.
- Admin dashboard có danh sách ticket.
- CloudWatch logs.
- Billing dashboard sau cleanup.
