---
title: "AWS Amplify Hosting"
date: 2026-07-21
weight: 1
chapter: false
pre: "<b>5.3.1 </b>"
---

## Tổng quan

AWS Amplify Hosting được sử dụng để triển khai và lưu trữ giao diện người dùng (Frontend) của hệ thống Campus IT Support Ticket Portal.

Dịch vụ này hỗ trợ triển khai tự động từ GitHub, cung cấp kết nối HTTPS và tích hợp quy trình Continuous Integration / Continuous Deployment (CI/CD). Mỗi lần mã nguồn được cập nhật lên nhánh **main**, Amplify sẽ tự động build và triển khai phiên bản mới nhất.

Frontend sau khi được triển khai sẽ giao tiếp với Amazon Cognito để xác thực người dùng và Amazon API Gateway để truy cập các dịch vụ Backend.

---

## Giao diện AWS Amplify

Hình dưới đây thể hiện giao diện quản lý ứng dụng sau khi Frontend được triển khai thành công trên AWS Amplify.

{{< project-image
src="images/5-Workshop/5.3-AWS Services/5.3.1 AWS Amplify Hosting/Amplify Hosting.png"
alt="AWS Amplify Hosting"
caption="Hình 5.3.1: Giao diện quản lý AWS Amplify Hosting."
>}}

---

## Quá trình triển khai

Sau mỗi lần cập nhật mã nguồn lên GitHub, AWS Amplify sẽ tự động thực hiện quá trình Build và Deploy phiên bản mới nhất của ứng dụng.

Trang Deployment History cho phép theo dõi trạng thái triển khai, thời gian Build và các phiên bản đã triển khai trước đó để phục vụ việc kiểm tra hoặc khôi phục khi cần thiết.

{{< project-image
src="images/5-Workshop/5.3-AWS Services/5.3.1 AWS Amplify Hosting/Deployment Success.png"
alt="Deployment Success"
caption="Hình 5.3.2: Quá trình triển khai ứng dụng thành công trên AWS Amplify."
>}}

---

## Lợi ích

AWS Amplify Hosting mang lại nhiều ưu điểm như:

- Tự động triển khai từ GitHub.
- Hỗ trợ HTTPS mặc định.
- Tích hợp quy trình CI/CD.
- Phân phối nội dung nhanh.
- Không cần quản lý máy chủ Frontend.

Trong kiến trúc của dự án, AWS Amplify đóng vai trò là điểm truy cập đầu tiên của người dùng trước khi hệ thống chuyển sang Amazon Cognito để xác thực và Amazon API Gateway để xử lý các yêu cầu từ Backend.