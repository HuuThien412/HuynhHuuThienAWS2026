---
title: "Amazon Cognito"
date: 2026-07-21
weight: 2
chapter: false
pre: "<b>5.3.2 </b>"
---

## Giới thiệu

Amazon Cognito được sử dụng làm dịch vụ xác thực và phân quyền cho hệ thống **Campus IT Support Ticket Portal**. Dịch vụ này cung cấp cơ chế đăng ký, đăng nhập và quản lý phiên người dùng mà không cần xây dựng hệ thống xác thực riêng.

Trong dự án, Amazon Cognito được tích hợp với **AWS Amplify Hosting**, **Amazon API Gateway** và **AWS Lambda** nhằm đảm bảo chỉ những người dùng hợp lệ mới có thể truy cập các chức năng của hệ thống.

---

## Vai trò trong dự án

Amazon Cognito đảm nhận các chức năng sau:

- Quản lý tài khoản người dùng.
- Đăng ký và đăng nhập thông qua Hosted UI.
- Cấp JWT Token sau khi xác thực thành công.
- Phân quyền người dùng bằng Cognito Groups.
- Tích hợp với API Gateway để bảo vệ các API.
- Cung cấp thông tin người dùng cho AWS Lambda.

---

## User Pool

User Pool là nơi lưu trữ toàn bộ tài khoản người dùng của hệ thống.

Trong dự án, User Pool chịu trách nhiệm:

- Quản lý tài khoản.
- Xác thực người dùng.
- Cấp ID Token, Access Token và Refresh Token.
- Quản lý thông tin hồ sơ người dùng.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/user-pool-overview.png"
alt="Tổng quan User Pool"
caption="Hình 5.3.3: Tổng quan User Pool của Amazon Cognito."
>}}
Hình trên thể hiện User Pool được sử dụng để quản lý toàn bộ tài khoản của hệ thống cùng các thông tin định danh và cấu hình xác thực.

---

## Cognito Groups

Để phân quyền người dùng, dự án sử dụng hai nhóm trong Amazon Cognito:

- **Users:** Người dùng thông thường có quyền gửi và theo dõi ticket.
- **Admins:** Quản trị viên có quyền xem, cập nhật và xóa ticket.

Sau khi người dùng đăng ký thành công, Lambda Post Confirmation sẽ tự động thêm tài khoản mới vào nhóm **Users**. Đối với quản trị viên, tài khoản được thêm thủ công vào nhóm **Admins**.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/user-groups.png"
alt="User Groups"
caption="Hình 5.3.4: Phân quyền người dùng bằng Cognito Groups."
>}}

Thông tin nhóm được đưa vào JWT Token và được sử dụng bởi AWS Lambda để kiểm tra quyền trước khi thực hiện các chức năng quản trị.

---

## App Client

Amazon Cognito App Client đại diện cho ứng dụng frontend của hệ thống.

Frontend sử dụng App Client để:

- Chuyển hướng người dùng tới Hosted UI.
- Nhận JWT Token sau khi đăng nhập.
- Duy trì phiên làm việc.
- Thực hiện đăng xuất.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/app-client.png"
alt="App Client"
caption="Hình 5.3.5: Cấu hình App Client của Amazon Cognito."
>}}

App Client là cầu nối giữa giao diện người dùng và Amazon Cognito trong toàn bộ quá trình xác thực.

---

## Hosted UI

Dự án sử dụng **Amazon Cognito Hosted UI** để cung cấp giao diện đăng nhập và đăng ký.

Sau khi người dùng xác thực thành công, Cognito tự động chuyển hướng về frontend và trả về JWT Token.

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/5.3.2-Amazon-Cognito/hosted-ui.png"
alt="Hosted UI"
caption="Hình 5.3.6: Giao diện đăng nhập Amazon Cognito Hosted UI."
>}}

Việc sử dụng Hosted UI giúp giảm đáng kể thời gian phát triển vì không cần xây dựng giao diện xác thực riêng, đồng thời đảm bảo các tiêu chuẩn bảo mật do AWS cung cấp.

---

## Kết quả đạt được

Sau khi tích hợp Amazon Cognito, hệ thống đạt được các kết quả sau:

- Người dùng có thể đăng ký và đăng nhập an toàn.
- JWT Token được cấp tự động sau khi xác thực.
- API được bảo vệ thông qua JWT Authorizer.
- Phân quyền giữa User và Admin được thực hiện bằng Cognito Groups.
- Không cần xây dựng hệ thống xác thực riêng.
- Hệ thống có khả năng mở rộng và dễ dàng tích hợp với các dịch vụ AWS khác.
