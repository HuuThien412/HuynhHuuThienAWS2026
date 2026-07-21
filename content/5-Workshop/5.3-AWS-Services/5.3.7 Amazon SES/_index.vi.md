---
title : "Amazon SES"
date : 2026-07-21
weight : 7
chapter : false
pre : " <b> 5.3.7 </b> "
---

Amazon Simple Email Service (Amazon SES) là dịch vụ gửi email trên nền tảng đám mây của AWS, được sử dụng để gửi email giao dịch, email thông báo và các loại email tự động từ ứng dụng. Dịch vụ giúp hệ thống gửi email một cách bảo mật, ổn định mà không cần tự triển khai máy chủ email riêng.

Trong dự án Campus IT Support Portal, Amazon SES được triển khai để chuẩn bị cho chức năng gửi email thông báo tự động trong tương lai. Hệ thống đã cấu hình thành công tài khoản gửi email (Verified Identity), tạo nền tảng để tích hợp với AWS Lambda khi cần gửi email đến người dùng.

---

## Bảng điều khiển Amazon SES

Bảng điều khiển Amazon SES cung cấp thông tin tổng quan về trạng thái tài khoản, giới hạn gửi email, tốc độ gửi tối đa và tình trạng hoạt động của dịch vụ. Giao diện này xác nhận rằng Amazon SES đã được cấu hình thành công và sẵn sàng cho việc tích hợp trong tương lai.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/ses-dashboard.png"
    title="Hình 5.3.7.1: Bảng điều khiển Amazon SES hiển thị trạng thái tài khoản và giới hạn gửi email." >}}

Bảng điều khiển cho thấy tài khoản đang hoạt động trong môi trường Sandbox, đồng thời hiển thị hạn mức gửi email hằng ngày, tốc độ gửi tối đa và trạng thái sức khỏe của dịch vụ.

---

## Xác thực địa chỉ email gửi

Để có thể gửi email bằng Amazon SES, địa chỉ email hoặc tên miền sử dụng để gửi phải được xác thực trước. Việc xác thực này giúp đảm bảo chỉ những địa chỉ hợp lệ mới được phép sử dụng dịch vụ gửi email của AWS.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/verified-identity.png"
    title="Hình 5.3.7.2: Địa chỉ email đã được xác thực trong Amazon SES." >}}

Trong quá trình triển khai, một địa chỉ Gmail đã được xác thực thành công và được sử dụng làm địa chỉ gửi email của hệ thống. Mặc dù chức năng gửi email tự động chưa được tích hợp vào ứng dụng, việc xác thực này đã chuẩn bị đầy đủ cho các bước phát triển tiếp theo.

---

## Configuration Sets

Amazon SES hỗ trợ tính năng Configuration Sets nhằm quản lý các quy tắc gửi email, theo dõi trạng thái gửi và thu thập các sự kiện liên quan đến email như gửi thành công, mở email hoặc lỗi gửi.

{{< figure src="/images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/email-configuration.png"
    title="Hình 5.3.7.3: Giao diện Configuration Sets trong Amazon SES." >}}

Trong phạm vi dự án, chưa tạo Configuration Set do chức năng gửi email chưa được triển khai hoàn chỉnh. Tuy nhiên, tính năng này đã được khảo sát và sẵn sàng sử dụng khi tích hợp Amazon SES với AWS Lambda trong tương lai.

---

## Kết quả

Amazon SES đã được cấu hình thành công và bổ sung vào kiến trúc của hệ thống Campus IT Support Portal. Địa chỉ email gửi đã được xác thực, đảm bảo sẵn sàng cho việc triển khai chức năng gửi email tự động trong các phiên bản tiếp theo của hệ thống.

Việc triển khai Amazon SES mang lại các kết quả sau:

- Cấu hình thành công dịch vụ gửi email trên nền tảng AWS.
- Xác thực thành công địa chỉ email gửi.
- Chuẩn bị hạ tầng cho chức năng gửi email thông báo tự động.
- Sẵn sàng tích hợp với AWS Lambda để gửi email theo sự kiện.
- Tăng khả năng mở rộng và tính chuyên nghiệp của hệ thống thông báo.
