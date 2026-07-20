---
title: "Host frontend với AWS Amplify"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Mục tiêu

Triển khai frontend bằng AWS Amplify Hosting để user và admin có thể truy cập hệ thống thông qua website HTTPS.

### Các bước triển khai

1. Push source code frontend lên GitHub.
2. Mở AWS Amplify console.
3. Chọn **Host web app** và kết nối GitHub repository.
4. Chọn branch cần deploy.
5. Cấu hình build settings.
6. Deploy ứng dụng.
7. Mở domain do Amplify tạo và kiểm tra website tải thành công.

### Kết quả

Frontend được truy cập thông qua domain mặc định của AWS Amplify. Route 53 custom domain đã được thử nghiệm, nhưng hiện hệ thống dùng Amplify domain do quá trình đăng ký custom domain gặp lỗi registrar/account validation.

### Ảnh minh chứng cần có

- Amplify app đã kết nối GitHub.
- Build/deploy thành công.
- Website mở được từ Amplify domain.
