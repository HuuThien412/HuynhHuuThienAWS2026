---
title: "Xác thực với Amazon Cognito"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Mục tiêu

Cấu hình Amazon Cognito để người dùng có thể đăng ký, đăng nhập và nhận JWT token. Hệ thống sử dụng group để phân quyền user thường và admin.

### Các bước triển khai

1. Tạo Cognito User Pool.
2. Cấu hình tùy chọn đăng nhập bằng email.
3. Tạo hai group: `Users` và `Admins`.
4. Tạo tài khoản test cho user thường và admin.
5. Thêm tài khoản admin vào group `Admins`.
6. Cấu hình frontend sử dụng User Pool ID và App Client ID.
7. Kiểm thử đăng ký/đăng nhập từ frontend.

### Quyền truy cập

| Group | Quyền |
| --- | --- |
| Users | Gửi ticket và xem ticket của chính mình |
| Admins | Xem toàn bộ ticket, cập nhật trạng thái, ghi chú và xóa ticket |

### Ảnh minh chứng cần có

- Cognito User Pool overview.
- Group `Users` và `Admins`.
- Màn hình login thành công.
