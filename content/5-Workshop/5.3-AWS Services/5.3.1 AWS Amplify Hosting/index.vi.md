---
title: "5.3 Dịch vụ AWS"
date: 2026-07-21
weight: 3
chapter: false
pre: "<b>5.3 </b>"
---

# Dịch vụ AWS

## 5.3.1 AWS Amplify Hosting

### Giới thiệu

AWS Amplify Hosting được lựa chọn làm dịch vụ triển khai frontend cho dự án **Campus IT Support Ticket Portal**. Dịch vụ này cung cấp môi trường lưu trữ website tĩnh với khả năng tích hợp trực tiếp cùng GitHub để tự động xây dựng (Build) và triển khai (Deploy) sau mỗi lần cập nhật mã nguồn.

Việc sử dụng AWS Amplify giúp loại bỏ nhu cầu cấu hình máy chủ web truyền thống, đồng thời cung cấp chứng chỉ HTTPS, tối ưu hiệu năng phân phối nội dung và hỗ trợ quy trình CI/CD.

---

### Vai trò trong dự án

Trong dự án này, AWS Amplify đảm nhận các nhiệm vụ sau:

- Lưu trữ giao diện frontend của hệ thống.
- Tự động build website Hugo sau mỗi lần Push lên GitHub.
- Tự động triển khai phiên bản mới mà không cần thao tác thủ công.
- Cung cấp địa chỉ truy cập công khai thông qua HTTPS.
- Quản lý lịch sử các lần triển khai.
- Hỗ trợ mở rộng hệ thống trong tương lai thông qua nhiều Branch.

---

### Quy trình hoạt động

Quy trình triển khai frontend được thực hiện như sau:

1. Nhà phát triển cập nhật mã nguồn lên GitHub Repository.
2. AWS Amplify phát hiện Commit mới trên nhánh **main**.
3. Amplify tự động tải mã nguồn.
4. Hệ thống thực hiện Build dự án.
5. Sau khi Build thành công, Amplify tự động Deploy.
6. Website mới được cập nhật và sẵn sàng phục vụ người dùng.

Quy trình này giúp giảm thiểu sai sót trong quá trình triển khai và đảm bảo phiên bản mới luôn được cập nhật nhanh chóng.

---

### Giao diện AWS Amplify

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/Amplify Hosting.png"
alt="AWS Amplify Hosting"
caption="Hình 5.3.1: Ứng dụng Campus IT Support Ticket Portal trên AWS Amplify Hosting."
>}}

Hình trên thể hiện ứng dụng đã được triển khai trên AWS Amplify. Amplify quản lý ứng dụng, nhánh triển khai (Production Branch), tên miền mặc định và liên kết với GitHub Repository.

---

### Quy trình Build và Deploy

{{< project-image
src="images/5-Workshop/5.3-AWS-Services/Deployment Success.png"
alt="Deployment Success"
caption="Hình 5.3.2: Quá trình Build và Deploy thành công trên AWS Amplify."
>}}

Mỗi lần mã nguồn được cập nhật, AWS Amplify sẽ tự động kích hoạt quy trình Build và Deploy. Hệ thống hiển thị thời gian Build, thời gian Deploy, lịch sử triển khai và trạng thái của từng phiên bản, giúp theo dõi quá trình triển khai một cách trực quan.

---

### Kết quả đạt được

Sau khi triển khai bằng AWS Amplify Hosting, hệ thống đạt được các kết quả sau:

- Frontend được triển khai công khai thông qua HTTPS.
- Quy trình CI/CD được tự động hóa hoàn toàn.
- Website luôn được cập nhật sau mỗi lần Push lên GitHub.
- Không cần quản lý máy chủ web.
- Hỗ trợ mở rộng và triển khai nhiều môi trường trong tương lai.