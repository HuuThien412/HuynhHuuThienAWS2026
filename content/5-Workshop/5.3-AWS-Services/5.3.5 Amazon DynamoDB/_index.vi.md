---
title: "Amazon DynamoDB"
date: 2026-07-21
weight: 5
chapter: false
pre: "<b>5.3.5 </b>"
---

## Giới thiệu

Amazon DynamoDB là cơ sở dữ liệu NoSQL chính được sử dụng trong hệ thống Campus IT Support Ticket Portal.

Dịch vụ này lưu trữ toàn bộ thông tin ticket, dữ liệu người dùng và các kết nối WebSocket. Với mô hình Fully Managed Database, DynamoDB cung cấp hiệu năng cao, khả năng mở rộng tự động và độ sẵn sàng cao mà không cần quản lý máy chủ.

---

## Vai trò trong hệ thống

Amazon DynamoDB chịu trách nhiệm:

- Lưu trữ thông tin ticket hỗ trợ.
- Quản lý trạng thái ticket trong suốt quá trình xử lý.
- Lưu thông tin người gửi yêu cầu.
- Lưu Connection ID của WebSocket phục vụ thông báo thời gian thực.
- Cung cấp dữ liệu cho AWS Lambda.
- Tự động mở rộng theo lưu lượng truy cập.

---

## Các bảng DynamoDB

Hệ thống sử dụng hai bảng DynamoDB.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/dynamodb-tables.png"
alt="Amazon DynamoDB tables"
caption="Hình 5.3.5.1: Các bảng Amazon DynamoDB được sử dụng trong hệ thống Campus IT Support Ticket Portal."
>}}

Hai bảng bao gồm:

- **CampusSupportTickets** – lưu toàn bộ ticket hỗ trợ.
- **CampusSupportConnections** – lưu WebSocket Connection ID phục vụ thông báo thời gian thực.

Việc tách dữ liệu thành nhiều bảng giúp hệ thống dễ quản lý và nâng cao hiệu năng.

---

## Tổng quan bảng Ticket

Bảng CampusSupportTickets lưu toàn bộ dữ liệu của các ticket hỗ trợ.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/ticket-table-overview.png"
alt="CampusSupportTickets table overview"
caption="Hình 5.3.5.2: Tổng quan bảng CampusSupportTickets."
>}}

Bảng sử dụng **ticketId** làm Partition Key và hoạt động ở chế độ **On-Demand**, cho phép DynamoDB tự động mở rộng tài nguyên theo lưu lượng truy cập.

Trang tổng quan cũng hiển thị trạng thái bảng, số lượng dữ liệu, dung lượng lưu trữ và ARN của tài nguyên.

---

## Dữ liệu Ticket

Các yêu cầu hỗ trợ của người dùng được lưu dưới dạng các Item trong bảng CampusSupportTickets.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/ticket-items.png"
alt="Ticket records"
caption="Hình 5.3.5.3: Dữ liệu ticket được lưu trong bảng CampusSupportTickets."
>}}

Mỗi bản ghi bao gồm các thông tin:

- Ticket ID
- Họ tên
- Email
- Danh mục
- Nội dung yêu cầu
- Vị trí
- Mức độ ưu tiên
- Trạng thái
- Thời gian tạo
- Thông tin tệp đính kèm

AWS Lambda thực hiện các thao tác Create, Read, Update và Delete (CRUD) thông qua AWS SDK.

---

## Giám sát

Amazon DynamoDB tích hợp trực tiếp với Amazon CloudWatch.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.5-Amazon-DynamoDB/dynamodb-monitoring.png"
alt="Amazon DynamoDB monitoring"
caption="Hình 5.3.5.4: Dashboard giám sát DynamoDB trên Amazon CloudWatch."
>}}

CloudWatch cung cấp các chỉ số như:

- Read Capacity
- Write Capacity
- Read Throttled Requests
- Write Throttled Requests
- Throughput tiêu thụ
- Hiệu năng của bảng

Các chỉ số này hỗ trợ theo dõi tình trạng hoạt động và phát hiện sớm các vấn đề về hiệu năng.

---

## Kết quả

Amazon DynamoDB mang lại các lợi ích sau:

- Cơ sở dữ liệu NoSQL được quản lý hoàn toàn.
- Tự động mở rộng bằng On-Demand Capacity.
- Truy cập dữ liệu với độ trễ thấp.
- Tích hợp chặt chẽ với AWS Lambda.
- Độ sẵn sàng và độ bền cao.
- Hỗ trợ giám sát thông qua Amazon CloudWatch.
