---
title: "Amazon SES"
date: 2026-07-21
weight: 7
chapter: false
pre: "<b>5.3.7 </b>"
---

# Amazon SES

## Giới thiệu

Amazon Simple Email Service (Amazon SES) là dịch vụ gửi email trên nền tảng đám mây của AWS, được sử dụng để gửi email giao dịch và email thông báo một cách an toàn, ổn định.

Dịch vụ cho phép ứng dụng gửi email mà không cần tự triển khai hoặc vận hành máy chủ email riêng. Amazon SES cũng cung cấp các chức năng theo dõi trạng thái tài khoản, xác minh địa chỉ gửi, giới hạn gửi và hỗ trợ giám sát quá trình gửi email.

Trong dự án Campus IT Support Portal, Amazon SES được cấu hình để hỗ trợ chức năng thông báo qua email. Một địa chỉ email gửi đã được xác minh thành công, tạo nền tảng cần thiết để tích hợp với AWS Lambda.

---

## Vai trò trong dự án

Amazon SES được sử dụng để hỗ trợ các trường hợp thông báo sau:

- Gửi email xác nhận khi ticket được tạo.
- Gửi cảnh báo khi xuất hiện ticket có mức ưu tiên High hoặc Critical.
- Thông báo cho người dùng khi trạng thái ticket thay đổi.
- Gửi thông báo quản trị đến đội hỗ trợ IT.
- Hỗ trợ gửi email bất đồng bộ thông qua AWS Lambda.

Tài khoản SES hiện đang hoạt động trong môi trường Sandbox. Vì vậy, việc gửi email hiện tại chỉ được phép giữa các địa chỉ đã được xác minh.

---

## Bảng điều khiển Amazon SES

Bảng điều khiển Amazon SES cung cấp thông tin tổng quan về trạng thái dịch vụ, giới hạn gửi email, tình trạng tài khoản và môi trường đang hoạt động.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/ses-dashboard.png"
alt="Bảng điều khiển Amazon SES"
caption="Hình 5.3.7.1: Bảng điều khiển Amazon SES hiển thị trạng thái tài khoản và giới hạn gửi email."
>}}

Bảng điều khiển cho thấy tài khoản đang hoạt động tại Region Asia Pacific (Singapore) và vẫn đang ở môi trường SES Sandbox.

Trang này cũng hiển thị:

- Hạn mức gửi email mỗi ngày.
- Tốc độ gửi email tối đa.
- Trạng thái sức khỏe tài khoản.
- Khu vực theo dõi Reputation Metrics.
- Thông tin về việc yêu cầu Production Access.

Tài khoản hiện hỗ trợ tối đa 200 email trong vòng 24 giờ và tốc độ gửi tối đa là một email mỗi giây.

---

## Xác minh địa chỉ email gửi

Amazon SES yêu cầu các địa chỉ gửi phải được xác minh trước khi có thể sử dụng để gửi email.

Identity trong Amazon SES có thể là:

- Một địa chỉ email.
- Một tên miền.
- Một tên miền phụ.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/verified-identity.png"
alt="Địa chỉ gửi đã xác minh trong Amazon SES"
caption="Hình 5.3.7.2: Địa chỉ email gửi đã được xác minh trong Amazon SES."
>}}

Trong dự án này, một địa chỉ Gmail đã được xác minh thành công trong Amazon SES. Trạng thái Verified xác nhận rằng địa chỉ này được phép sử dụng để gửi email thông qua dịch vụ.

Do tài khoản vẫn đang ở Sandbox mode, hệ thống hiện chỉ có thể gửi email đến những địa chỉ nhận đã được xác minh. Cần yêu cầu Production Access trước khi gửi email đến các địa chỉ bên ngoài không giới hạn.

---

## Configuration Sets

Amazon SES cung cấp Configuration Sets để quản lý hành vi gửi email, ghi nhận sự kiện và giám sát hoạt động gửi thư.

Configuration Sets có thể được sử dụng để theo dõi các sự kiện như:

- Email được gửi thành công.
- Email bị từ chối.
- Bounce.
- Complaint.
- Email được mở.
- Liên kết trong email được nhấn.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.7-Amazon-SES/email-configuration.png"
alt="Configuration Sets của Amazon SES"
caption="Hình 5.3.7.3: Configuration Sets trong Amazon SES phục vụ quản lý quá trình gửi email."
>}}

Trong phiên bản hiện tại của dự án chưa tạo Configuration Set. Tính năng này có thể được bổ sung trong tương lai khi hệ thống cần theo dõi chi tiết trạng thái gửi email, phân tích dữ liệu hoặc xuất bản các sự kiện gửi thư.

Đối với chức năng gửi email giao dịch cơ bản, Amazon SES vẫn có thể hoạt động mà không cần Configuration Set.
