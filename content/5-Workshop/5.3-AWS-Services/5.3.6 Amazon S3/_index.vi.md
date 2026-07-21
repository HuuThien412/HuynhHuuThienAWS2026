---
title: "Amazon S3"
date: 2026-07-21
weight: 6
chapter: false
pre: "<b>5.3.6 </b>"
---

# Amazon S3

## Giới thiệu

Amazon Simple Storage Service (Amazon S3) là dịch vụ lưu trữ đối tượng được sử dụng để lưu các tệp đính kèm do người dùng tải lên.

Thay vì lưu trực tiếp tệp trong cơ sở dữ liệu, hệ thống lưu tệp trong Amazon S3 và chỉ lưu đường dẫn (URL) của tệp trong DynamoDB. Cách làm này giúp giảm dung lượng cơ sở dữ liệu và tăng khả năng mở rộng.

---

## Vai trò trong hệ thống

Amazon S3 chịu trách nhiệm:

- Lưu trữ tệp đính kèm của ticket.
- Cung cấp dịch vụ lưu trữ có độ bền cao.
- Sinh URL truy cập tệp.
- Giảm dung lượng lưu trữ của DynamoDB.
- Cho phép frontend tải tệp từ S3.

---

## S3 Bucket

Hệ thống sử dụng một S3 Bucket riêng để lưu trữ toàn bộ tệp đính kèm.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/s3-bucket.png"
alt="Amazon S3 bucket"
caption="Hình 5.3.6.1: Amazon S3 Bucket được sử dụng trong hệ thống."
>}}

Bucket đóng vai trò là nơi lưu trữ tập trung cho toàn bộ file upload của người dùng.

---

## Lưu trữ tệp đính kèm

Khi người dùng gửi ticket có kèm tệp, AWS Lambda sẽ tải tệp lên Amazon S3.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/uploaded-files.png"
alt="Uploaded files"
caption="Hình 5.3.6.2: Các tệp đính kèm được lưu trong Amazon S3."
>}}

DynamoDB chỉ lưu URL của tệp, còn dữ liệu thực tế được lưu trong S3.

Thiết kế này giúp tăng hiệu năng và giảm dung lượng lưu trữ của cơ sở dữ liệu.

---

## Cấu trúc thư mục

Các tệp được tổ chức theo thư mục bên trong Bucket.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.6-Amazon-S3/folder-structure.png"
alt="Folder structure"
caption="Hình 5.3.6.3: Cấu trúc thư mục trong Amazon S3."
>}}

Việc tổ chức theo thư mục giúp dễ dàng quản lý và bảo trì dữ liệu.

---

## Kết quả

Amazon S3 mang lại các lợi ích:

- Lưu trữ đối tượng với độ bền cao.
- Tự động mở rộng.
- Tích hợp chặt chẽ với AWS Lambda.
- Quản lý tệp đính kèm hiệu quả.
- Giảm dung lượng lưu trữ của cơ sở dữ liệu.