---
title: "Đề xuất dự án"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Campus IT Support Ticket Portal
## Hệ thống Helpdesk Serverless trên AWS cho hỗ trợ IT trong trường học

---

### 1. Tổng quan dự án

Campus IT Support Ticket Portal là một hệ thống web hỗ trợ tiếp nhận và xử lý yêu cầu hỗ trợ kỹ thuật trong môi trường trường học. Hệ thống cho phép sinh viên hoặc nhân viên đăng nhập, gửi yêu cầu hỗ trợ IT, theo dõi trạng thái xử lý ticket, đồng thời cung cấp giao diện quản trị để bộ phận IT xem danh sách ticket, cập nhật trạng thái, ghi chú xử lý và xóa ticket khi cần.

Hệ thống được xây dựng theo mô hình serverless trên AWS, giúp giảm nhu cầu quản lý máy chủ, dễ mở rộng và phù hợp với các ứng dụng web hiện đại.

Dự án có thể được triển khai theo hướng cá nhân hoặc nhóm. Trong phạm vi báo cáo này, nội dung tập trung vào kiến trúc AWS, luồng xác thực, backend serverless, lưu trữ dữ liệu, giám sát và tài liệu hóa hệ thống.

---

### 2. Vấn đề cần giải quyết

#### Vấn đề

Trong môi trường trường học, các yêu cầu hỗ trợ IT thường được báo qua tin nhắn, điện thoại, email hoặc trao đổi trực tiếp. Cách làm này có nhiều hạn chế:

- Yêu cầu có thể bị quên, bị trùng lặp hoặc không có lịch sử xử lý rõ ràng.
- Bộ phận IT không có hàng đợi tập trung để ưu tiên xử lý sự cố.
- Người dùng khó theo dõi ticket của mình đang ở trạng thái mới, đang xử lý, đã giải quyết hay đã đóng.
- Admin cần một giao diện rõ ràng để xem chi tiết ticket, cập nhật trạng thái và ghi chú kết quả xử lý.
- File minh chứng như ảnh chụp lỗi thường bị gửi rời rạc, gây khó khăn khi quản lý ticket.

#### Giải pháp

Campus IT Support Ticket Portal giải quyết vấn đề bằng cách cung cấp một hệ thống helpdesk tập trung với hai nhóm người dùng chính:

- **Users**: Đăng nhập, gửi ticket, upload file đính kèm và theo dõi ticket của mình.
- **Admins**: Xem toàn bộ ticket, lọc danh sách, xem chi tiết, cập nhật trạng thái, ghi chú xử lý và xóa ticket.

Ứng dụng sử dụng các dịch vụ managed của AWS để xử lý hosting, xác thực, API, backend logic, database, file storage, phân quyền và monitoring.

---

### 3. Kiến trúc giải pháp

#### Sơ đồ kiến trúc tổng quan

```text
[User/Admin Browser]
        |
        v
[AWS Amplify Hosting]
        |
        v
[Amazon Cognito User Pool]
        |
        v
[Amazon API Gateway + JWT Authorizer]
        |
        v
[AWS Lambda Backend]
        |----------------------|
        v                      v
[Amazon DynamoDB]        [Amazon S3]
        |
        v
[Amazon CloudWatch Logs]

[Amazon Route 53] được thử nghiệm cho custom domain,
nhưng website hiện đang sử dụng domain mặc định của AWS Amplify.
```

#### Các dịch vụ AWS được sử dụng

| Dịch vụ | Vai trò trong hệ thống |
| --- | --- |
| **AWS Amplify Hosting** | Triển khai và lưu trữ frontend; kết nối GitHub và tự động build/deploy khi có thay đổi mã nguồn |
| **Amazon Cognito** | Quản lý đăng ký, đăng nhập, xác thực và phân quyền thông qua group `Users` và `Admins` |
| **Amazon API Gateway** | Cung cấp API endpoint và xác thực JWT token từ Cognito bằng JWT Authorizer |
| **AWS Lambda** | Xử lý nghiệp vụ backend như tạo ticket, lấy danh sách, cập nhật trạng thái, ghi chú, xóa ticket và kiểm tra quyền truy cập |
| **Amazon DynamoDB** | Lưu dữ liệu ticket gồm người gửi, nhóm sự cố, mức độ ưu tiên, mô tả, trạng thái, thời gian cập nhật và ghi chú admin |
| **Amazon S3** | Lưu file đính kèm khi người dùng gửi ticket, ví dụ ảnh chụp lỗi hoặc tài liệu minh họa |
| **AWS IAM** | Quản lý quyền truy cập giữa Lambda, DynamoDB, S3, API Gateway và các dịch vụ AWS liên quan |
| **Amazon CloudWatch** | Ghi log, theo dõi hoạt động backend, kiểm tra lỗi API/Lambda và hỗ trợ debug |
| **Amazon Route 53** | Được thử nghiệm để đăng ký custom domain; hiện dùng domain mặc định của Amplify do lỗi registrar/account validation |

#### Nhóm người dùng và quyền truy cập

| Group | Quyền trong hệ thống |
| --- | --- |
| **Users** | Gửi ticket, upload file đính kèm và xem ticket của chính mình |
| **Admins** | Xem toàn bộ ticket, lọc danh sách, cập nhật trạng thái, ghi chú xử lý và xóa ticket |

---

### 4. Luồng hoạt động chính

#### Luồng người dùng

1. Người dùng truy cập website được host trên AWS Amplify.
2. Người dùng đăng ký hoặc đăng nhập thông qua Amazon Cognito.
3. Người dùng gửi ticket hỗ trợ IT với nhóm sự cố, mức độ ưu tiên, mô tả và file đính kèm nếu có.
4. API Gateway xác thực Cognito JWT token bằng JWT Authorizer.
5. Lambda xử lý request, lưu dữ liệu ticket vào DynamoDB và upload file đính kèm lên S3 nếu có.
6. Người dùng có thể theo dõi trạng thái ticket trong User Portal.

#### Luồng admin

1. Admin đăng nhập bằng tài khoản thuộc group `Admins` trong Cognito.
2. Admin truy cập giao diện quản trị.
3. API Gateway xác thực JWT token và Lambda kiểm tra group claim của admin.
4. Admin có thể xem danh sách ticket, lọc ticket, xem chi tiết, cập nhật trạng thái, thêm ghi chú hoặc xóa ticket.
5. Lambda cập nhật dữ liệu vào DynamoDB và ghi log vào CloudWatch.

---

### 5. Mô hình dữ liệu ticket

| Thuộc tính | Mô tả |
| --- | --- |
| `ticketId` | Mã ticket duy nhất |
| `userId` | Mã người dùng từ Cognito |
| `fullName` | Họ tên người gửi |
| `email` | Email người gửi |
| `category` | Nhóm sự cố như WiFi, tài khoản, phần mềm, phần cứng hoặc thiết bị |
| `priority` | Mức độ ưu tiên: LOW, MEDIUM, HIGH, URGENT |
| `location` | Vị trí xảy ra sự cố trong trường |
| `description` | Mô tả chi tiết lỗi |
| `status` | Trạng thái ticket: NEW, IN_PROGRESS, RESOLVED, CLOSED |
| `adminNote` | Ghi chú hoặc kết quả xử lý từ nhân viên IT |
| `attachmentKey` | Object key của file trên S3 nếu có upload |
| `createdAt` | Thời điểm tạo ticket |
| `updatedAt` | Thời điểm cập nhật gần nhất |

---

### 6. Thiết kế API

| Method | Endpoint | Quyền | Mục đích |
| --- | --- | --- | --- |
| `POST` | `/tickets` | User/Admin | Tạo ticket hỗ trợ mới |
| `GET` | `/tickets` | Admin | Lấy danh sách toàn bộ ticket cho Admin Console |
| `GET` | `/tickets/my` | User | Lấy danh sách ticket của người dùng đang đăng nhập |
| `GET` | `/tickets/{ticketId}` | Owner/Admin | Xem chi tiết ticket |
| `PATCH` | `/tickets/{ticketId}` | Admin | Cập nhật trạng thái và ghi chú admin |
| `DELETE` | `/tickets/{ticketId}` | Admin | Xóa ticket |

#### Luồng trạng thái ticket

```text
NEW -> IN_PROGRESS -> RESOLVED -> CLOSED
```

---

### 7. Kế hoạch triển khai

| Giai đoạn | Nội dung | Thời gian |
| --- | --- | --- |
| **Tuần 1-2** | Tìm hiểu AWS cơ bản, chuẩn bị môi trường local và xác định yêu cầu dự án | Tháng 1 |
| **Tuần 3-4** | Thiết kế User Portal và Admin Console; chuẩn bị repository frontend và triển khai Amplify | Tháng 1 |
| **Tuần 5-6** | Cấu hình Cognito User Pool, user groups, DynamoDB table và S3 attachment bucket | Tháng 2 |
| **Tuần 7-8** | Xây dựng Lambda backend và API Gateway endpoints với JWT Authorizer | Tháng 2 |
| **Tuần 9-10** | Hoàn thiện luồng admin, tra cứu ticket của user, xử lý file đính kèm và CloudWatch logging | Tháng 3 |
| **Tuần 11-12** | Kiểm thử end-to-end, viết tài liệu triển khai, rà soát IAM/security và hoàn thiện cleanup | Tháng 3 |

---

### 8. Kế hoạch kiểm thử

| Test case | Kết quả mong đợi |
| --- | --- |
| User đăng ký và đăng nhập | Cognito tạo và xác thực tài khoản thành công |
| User gửi ticket hợp lệ | Ticket được lưu vào DynamoDB |
| User upload file đính kèm | File được upload lên S3 và liên kết với ticket |
| User xem ticket của mình | Chỉ trả về ticket thuộc người dùng đang đăng nhập |
| Admin mở danh sách ticket | Tất cả ticket hiển thị trong Admin Console |
| Admin cập nhật trạng thái ticket | Bản ghi DynamoDB được cập nhật thành công |
| Admin xóa ticket | Ticket được xóa khỏi DynamoDB |
| Request thiếu hoặc sai JWT token | API Gateway từ chối request |
| User thường gọi API admin | Lambda từ chối thao tác |
| Backend phát sinh lỗi | Log lỗi xuất hiện trong CloudWatch Logs |

---

### 9. Ước tính chi phí

**Chi phí AWS ước tính hằng tháng cho môi trường demo nhỏ:**

| Dịch vụ | Chi phí ước tính/tháng | Ghi chú |
| --- | --- | --- |
| AWS Amplify Hosting | ~$0-2 | Host frontend tĩnh, traffic nhỏ |
| Amazon Cognito | ~$0 | Free tier đủ cho demo users |
| Amazon API Gateway | ~$0-2 | Số lượng request thấp |
| AWS Lambda | ~$0-1 | Backend serverless, chỉ chạy khi có request |
| Amazon DynamoDB | ~$0-2 | Dữ liệu ticket nhỏ, dùng on-demand |
| Amazon S3 | ~$0-1 | File đính kèm dung lượng nhỏ |
| Amazon CloudWatch | ~$0-1 | Log cơ bản cho API/Lambda |
| Amazon Route 53 | Thay đổi theo domain | Đã thử custom domain nhưng chưa hoàn tất |
| **Tổng cộng** | **~$0-10/tháng** | Phụ thuộc traffic, dung lượng lưu trữ và domain |

---

### 10. Đánh giá rủi ro

| Rủi ro | Ảnh hưởng | Khả năng xảy ra | Cách giảm thiểu |
| --- | --- | --- | --- |
| Cấu hình sai quyền Cognito group | Cao | Trung bình | Kiểm tra claim `Users` và `Admins` trong Lambda |
| API bị gọi khi không có token hợp lệ | Trung bình | Trung bình | Sử dụng API Gateway JWT Authorizer |
| Lambda được cấp quyền quá rộng | Cao | Trung bình | Áp dụng least privilege IAM role cho DynamoDB và S3 |
| File đính kèm trên S3 bị lộ | Cao | Thấp | Giữ bucket private và chỉ truy cập file qua backend được kiểm soát |
| Thiết kế DynamoDB chưa tối ưu query | Trung bình | Trung bình | Xác định access pattern sớm và thêm index nếu cần |
| CORS làm frontend không gọi được API | Trung bình | Trung bình | Cấu hình API Gateway CORS cho domain của Amplify |
| Đăng ký custom domain Route 53 bị lỗi | Thấp | Trung bình | Dùng domain mặc định của Amplify cho đến khi hoàn tất validation |
| Quên xóa tài nguyên gây phát sinh chi phí | Trung bình | Trung bình | Viết cleanup steps và theo dõi Billing Dashboard |

---

### 11. Kết quả mong đợi

**Kết quả đã đạt được:**

- Frontend được triển khai bằng AWS Amplify Hosting.
- Đăng ký và đăng nhập người dùng được xử lý bằng Amazon Cognito.
- Phân quyền user/admin thông qua Cognito groups.
- API Gateway xác thực JWT token trước khi chuyển request đến backend.
- Lambda xử lý tạo ticket, tra cứu, cập nhật, xóa và kiểm tra quyền truy cập.
- DynamoDB lưu trữ dữ liệu ticket.
- S3 lưu trữ file đính kèm của ticket.
- CloudWatch logs hỗ trợ kiểm tra lỗi và debug backend.
- Route 53 custom domain đã được thử nghiệm nhưng hiện hệ thống dùng domain mặc định của Amplify.

**Giá trị của project:**

- Project mô phỏng một workflow helpdesk thực tế trong môi trường trường học.
- Kiến trúc serverless giúp giảm nhu cầu quản lý hạ tầng.
- Hệ thống có thể mở rộng thêm thông báo email, dashboard thống kê cho admin và custom domain sau khi Route 53 validation được xử lý.
