---
title: "AWS Amplify Hosting"
date: 2026-07-21
weight: 1
chapter: false
pre: "<b>5.3.1 </b>"
---

## Giới thiệu

AWS Amplify Hosting được sử dụng để build, triển khai và lưu trữ frontend của hệ thống **Campus IT Support Ticket Portal**.

Dịch vụ được kết nối trực tiếp với GitHub Repository của dự án. Khi mã nguồn mới được push lên nhánh `main`, AWS Amplify tự động kích hoạt quá trình build và deploy.

Việc tích hợp này tạo ra quy trình CI/CD tự động mà không cần vận hành máy chủ web thủ công.

---

## Vai trò trong dự án

AWS Amplify Hosting đảm nhận các nhiệm vụ sau:

- Lưu trữ ứng dụng frontend.
- Kết nối ứng dụng với GitHub Repository.
- Tự động phát hiện commit mới.
- Build và triển khai phiên bản mới nhất.
- Cung cấp địa chỉ truy cập công khai qua HTTPS.
- Lưu lịch sử các lần triển khai.
- Cho phép triển khai lại phiên bản trước khi cần thiết.

---

## Quy trình triển khai

Quá trình triển khai frontend diễn ra như sau:

1. Mã nguồn được cập nhật trên máy local.
2. Các thay đổi được commit và push lên GitHub.
3. AWS Amplify phát hiện commit mới trên nhánh `main`.
4. Amplify tải phiên bản mã nguồn mới nhất.
5. Hệ thống thực hiện quá trình build.
6. Sau khi build thành công, ứng dụng được triển khai.
7. Phiên bản mới được cung cấp qua tên miền của Amplify.

---

## Ứng dụng trên AWS Amplify

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.1-AWS-Amplify-Hosting/amplify-hosting.png"
alt="Tổng quan ứng dụng trên AWS Amplify Hosting"
caption="Hình 5.3.1: Campus IT Support Ticket Portal được triển khai trên AWS Amplify Hosting."
>}}

Trang tổng quan của Amplify hiển thị tên ứng dụng, App ID, nhánh production, tên miền công khai, lần triển khai gần nhất và GitHub Repository được kết nối.

---

## Quá trình Build và Deploy

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.1-AWS-Amplify-Hosting/deployment-success.png"
alt="Triển khai AWS Amplify thành công"
caption="Hình 5.3.2: Quá trình build và triển khai thành công trên AWS Amplify."
>}}

Trang triển khai xác nhận cả giai đoạn build và deploy đều hoàn thành thành công. Trang này cũng ghi nhận thời gian build, thời gian triển khai, commit nguồn và lịch sử các lần triển khai trước.

---

## Kết quả đạt được

AWS Amplify Hosting mang lại các kết quả sau:

- Frontend được cung cấp công khai qua HTTPS.
- Việc triển khai được tự động kích hoạt từ commit GitHub.
- Quy trình CI/CD giúp giảm lỗi triển khai thủ công.
- Không cần vận hành máy chủ frontend.
- Lịch sử deployment hỗ trợ kiểm tra lỗi và khôi phục phiên bản.
