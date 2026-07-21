---
title: "AWS IAM"
date : 2026-07-21
weight : 9
chapter : false
pre : " <b> 5.3.9 </b> "
---

# AWS Identity and Access Management (IAM)

## Giới thiệu

AWS Identity and Access Management (IAM) là dịch vụ quản lý danh tính và phân quyền của AWS, cho phép kiểm soát quyền truy cập vào các tài nguyên trên nền tảng AWS. IAM hỗ trợ quản lý người dùng, nhóm người dùng, vai trò (Roles) và các chính sách (Policies), giúp đảm bảo hệ thống hoạt động an toàn theo nguyên tắc phân quyền tối thiểu (Least Privilege).

Trong dự án Campus IT Support Portal, IAM được sử dụng chủ yếu để cấp quyền cho các dịch vụ AWS như Lambda, API Gateway, Cognito và RDS thông qua IAM Roles, giúp các dịch vụ có thể truy cập tài nguyên AWS một cách an toàn mà không cần sử dụng thông tin xác thực cố định.

---

## IAM Dashboard

IAM Dashboard cung cấp giao diện tổng quan về trạng thái bảo mật của tài khoản AWS cũng như các tài nguyên IAM đang được sử dụng. Dashboard hiển thị các khuyến nghị bảo mật, thông tin tài khoản và số lượng Users, Roles và Policies hiện có.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-dashboard.png"
alt="Dashboard AWS IAM"
caption="Hình 5.3.9.1: Dashboard của AWS IAM hiển thị thông tin bảo mật và tài nguyên IAM."
>}}

Dashboard cho thấy tài khoản đã bật xác thực đa yếu tố (MFA) cho Root User và cung cấp tổng quan về các tài nguyên IAM được cấu hình trong dự án.

---

## IAM Users

IAM Users đại diện cho các tài khoản người dùng có thể đăng nhập và truy cập các tài nguyên AWS. Mỗi người dùng có thể được cấp quyền thông qua IAM Policies hoặc User Groups.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-users.png"
alt="AWS IAM Users"
caption="Hình 5.3.9.2: Trang quản lý IAM Users."
>}}

Trong dự án này không tạo IAM User riêng vì các dịch vụ AWS được cấp quyền thông qua IAM Roles. Cách triển khai này tuân theo khuyến nghị bảo mật của AWS, giúp hạn chế việc sử dụng thông tin xác thực dài hạn cho các dịch vụ.

---

## IAM Roles

IAM Roles cung cấp quyền truy cập tạm thời cho các dịch vụ AWS khi cần tương tác với các tài nguyên khác. Việc sử dụng Roles giúp loại bỏ nhu cầu lưu trữ Access Key cố định và nâng cao tính bảo mật của hệ thống.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.9-AWS-IAM/iam-roles.png"
alt="AWS IAM Roles"
caption="Hình 5.3.9.3: Các IAM Roles được cấu hình cho các dịch vụ AWS trong dự án."
>}}

Nhiều IAM Role đã được tạo để phục vụ các dịch vụ triển khai trong dự án như Lambda Functions, API Gateway, Cognito và RDS. Mỗi Role chỉ được cấp những quyền cần thiết để thực hiện chức năng của mình, đảm bảo tuân thủ nguyên tắc phân quyền tối thiểu.

---

## Kết quả

AWS IAM mang lại nhiều lợi ích quan trọng cho dự án Campus IT Support Portal:

- Quản lý tập trung danh tính và quyền truy cập.
- Cấp quyền an toàn cho các dịch vụ thông qua IAM Roles.
- Kiểm soát truy cập chi tiết bằng IAM Policies.
- Hạn chế sử dụng thông tin xác thực dài hạn.
- Đảm bảo các dịch vụ AWS hoạt động an toàn trong kiến trúc serverless.

Việc triển khai IAM giúp các dịch vụ AWS trong dự án chỉ được cấp những quyền cần thiết để thực hiện chức năng của mình, từ đó nâng cao tính bảo mật và khả năng quản lý của toàn bộ hệ thống.