---
title: "Amazon API Gateway"
date: 2026-07-21
weight: 3
chapter: false
pre: "<b>5.3.3 </b>"
---

# Amazon API Gateway

## Giới thiệu

Amazon API Gateway là cổng giao tiếp giữa giao diện người dùng (Frontend) và các dịch vụ xử lý phía Backend của hệ thống **Campus IT Support Ticket Portal**.

Mọi yêu cầu từ ứng dụng Web đều được gửi đến API Gateway. Dịch vụ này sẽ xác thực người dùng thông qua Amazon Cognito trước khi chuyển tiếp request đến AWS Lambda để xử lý nghiệp vụ.

Việc sử dụng API Gateway giúp hệ thống hoạt động theo kiến trúc serverless, giảm chi phí quản lý máy chủ và dễ dàng mở rộng khi số lượng người dùng tăng lên.

---

## Vai trò trong dự án

Amazon API Gateway chịu trách nhiệm:

- Tiếp nhận các yêu cầu HTTPS từ Frontend.
- Xác thực JWT Token do Amazon Cognito phát hành.
- Định tuyến request đến AWS Lambda.
- Quản lý các API Routes.
- Cung cấp API Endpoint công khai.
- Quản lý các Stage triển khai.

---

## Tổng quan API

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/api-overview.png"
alt="API Gateway Overview"
caption="Hình 5.3.3.1: Danh sách API được sử dụng trong hệ thống."
>}}

Hệ thống hiện đang sử dụng hai API chính:

- CampusSupportTicketAPI (HTTP API)
- CampusSupportNotificationAPI (WebSocket API)

Trong đó HTTP API chịu trách nhiệm xử lý các thao tác CRUD của Ticket, còn WebSocket API được sử dụng để gửi thông báo theo thời gian thực.

---

## API Routes

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/routes.png"
alt="API Routes"
caption="Hình 5.3.3.2: Các Route được cấu hình trong Campus Support Ticket API."
>}}

Các Route của API Gateway định nghĩa các Endpoint mà Frontend có thể truy cập.

Trong dự án bao gồm:

- GET /tickets
- POST /tickets
- GET /{ticketId}
- PATCH /{ticketId}

Mỗi Route sẽ được liên kết với một hàm AWS Lambda tương ứng để xử lý nghiệp vụ.

---

## JWT Authorization

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/jwt-authorizer.png"
alt="JWT Authorization"
caption="Hình 5.3.3.3: Cấu hình JWT Authorization sử dụng Amazon Cognito."
>}}

API Gateway sử dụng Amazon Cognito làm JWT Authorizer để bảo vệ các API.

Mỗi request đều được kiểm tra:

- Chữ ký JWT.
- Issuer.
- Audience.
- Thời gian hết hạn của Token.

Chỉ những người dùng đã đăng nhập hợp lệ mới có thể truy cập các API được bảo vệ.

---

## Lambda Integration

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/lambda-integration.png"
alt="Lambda Integration"
caption="Hình 5.3.3.4: Liên kết giữa API Gateway và AWS Lambda."
>}}

Sau khi request được xác thực thành công, API Gateway sẽ chuyển tiếp dữ liệu đến AWS Lambda.

Mỗi Route được liên kết với một Lambda Function để thực hiện các thao tác như:

- Lấy danh sách Ticket.
- Tạo Ticket mới.
- Cập nhật Ticket.
- Lấy thông tin chi tiết của Ticket.

Việc tích hợp này giúp Backend hoàn toàn không cần quản lý máy chủ.

---

## Deployment Stage

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.3-Amazon-API-Gateway/stage.png"
alt="Deployment Stage"
caption="Hình 5.3.3.5: Stage triển khai mặc định của API Gateway."
>}}

API được triển khai thông qua Stage mặc định ($default).

Mỗi khi cấu hình API thay đổi và được Deploy, Stage sẽ tự động cập nhật phiên bản mới nhất và cung cấp một Invoke URL để Frontend truy cập.

Việc sử dụng Stage giúp quản lý nhiều môi trường triển khai như Development, Testing và Production trong tương lai.

---

## Kết quả

Amazon API Gateway mang lại các lợi ích sau:

- Cung cấp API Endpoint bảo mật thông qua HTTPS.
- Xác thực người dùng bằng JWT Token từ Amazon Cognito.
- Định tuyến request đến AWS Lambda.
- Hỗ trợ triển khai tự động thông qua Stage.
- Dễ dàng mở rộng khi số lượng người dùng tăng.
- Phù hợp với kiến trúc Serverless của hệ thống.