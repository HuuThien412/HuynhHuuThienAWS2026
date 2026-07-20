---
title: "Chia sẻ và đóng góp ý kiến"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

### Chia sẻ

Trong quá trình thực tập và học AWS, tôi có cơ hội tìm hiểu và thực hành nhiều dịch vụ cloud quan trọng thông qua tài liệu FCJ Cloud Journey và AWS Study Group. Điều giá trị nhất trong quá trình này là tôi không chỉ học từng dịch vụ riêng lẻ, mà còn hiểu cách các dịch vụ AWS phối hợp với nhau để tạo thành một ứng dụng hoàn chỉnh.

Với project cá nhân/nhóm, tôi thực hiện và tài liệu hóa **Campus IT Support Ticket Portal**, một hệ thống helpdesk serverless dùng để tiếp nhận và quản lý yêu cầu hỗ trợ IT trong môi trường trường học. Thông qua project này, tôi đã thực hành với AWS Amplify Hosting, Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, IAM và Amazon CloudWatch.

Project giúp tôi hiểu rõ hơn luồng hoạt động của một ứng dụng cloud:

- Host frontend bằng AWS Amplify.
- Xác thực user/admin bằng Amazon Cognito.
- Bảo vệ API bằng JWT Authorizer trong API Gateway.
- Xử lý backend logic bằng AWS Lambda.
- Lưu dữ liệu ticket trong DynamoDB.
- Lưu file đính kèm trong Amazon S3.
- Kiểm tra log và lỗi bằng Amazon CloudWatch.
- Quản lý quyền truy cập giữa các dịch vụ bằng IAM role.

Bên cạnh kiến thức kỹ thuật, tôi cũng cải thiện kỹ năng viết tài liệu. Việc viết proposal, worklog, blog và workshop giúp tôi biết cách tổ chức nội dung dự án rõ ràng hơn và trình bày quyết định kỹ thuật có cấu trúc hơn.

### Khó khăn gặp phải

Một số khó khăn tôi gặp trong quá trình thực hiện project:

- Hiểu đúng cách Cognito JWT token được truyền từ frontend đến API Gateway.
- Phân quyền rõ ràng giữa user thường và admin.
- Thiết kế dữ liệu DynamoDB để hỗ trợ cả luồng user và luồng admin.
- Xử lý lưu trữ file đính kèm bằng S3.
- Debug lỗi backend thông qua CloudWatch Logs.
- Thử nghiệm đăng ký custom domain bằng Route 53 nhưng chưa hoàn tất do lỗi registrar/account validation.

Những khó khăn này giúp tôi nhận ra rằng xây dựng một hệ thống cloud không chỉ là tạo tài nguyên, mà còn cần kết nối dịch vụ đúng cách, kiểm soát quyền cẩn thận và kiểm thử từng luồng theo từng bước.

### Đóng góp ý kiến

Tài liệu FCJ Cloud Journey và AWS Study Group rất hữu ích cho sinh viên muốn học AWS theo hướng thực hành. Cách trình bày dạng workshop giúp người học dễ theo dõi vì mỗi phần có mục tiêu, bước triển khai, kiểm thử và cleanup rõ ràng.

Theo trải nghiệm của tôi, quá trình học sẽ hiệu quả hơn nếu người học:

- Chụp màn hình ngay sau mỗi bước triển khai.
- Ghi lại lỗi và cách xử lý trong quá trình deploy.
- Tài liệu hóa IAM permissions rõ ràng.
- Cập nhật sơ đồ kiến trúc khi project thay đổi.
- Thêm bước cleanup để tránh phát sinh chi phí AWS không cần thiết.

### Đề xuất cải thiện

Với người học sau này, tôi đề xuất nên bắt đầu bằng một project nhỏ nhưng có tính thực tế. Một project như ticket portal khá phù hợp vì bao gồm các thành phần phổ biến của ứng dụng cloud: frontend hosting, authentication, API, backend processing, database, file storage, monitoring và security.

Trong tương lai, project này có thể mở rộng thêm:

- Gửi email thông báo khi ticket được tạo hoặc cập nhật.
- Dashboard thống kê ticket theo trạng thái và mức độ ưu tiên.
- Chức năng preview file đính kèm trong admin console.
- Hoàn tất cấu hình custom domain bằng Route 53.
- Audit log chi tiết hơn cho thao tác của admin.

### Kết luận

Nhìn chung, báo cáo thực tập và project này giúp tôi kết nối kiến thức AWS lý thuyết với triển khai thực tế. Tôi hiểu rõ hơn về serverless architecture, authentication, API design, data storage, monitoring và documentation. Quá trình thực hiện cũng cho tôi thấy tầm quan trọng của việc lập kế hoạch, kiểm thử từng bước và viết tài liệu kỹ thuật rõ ràng khi xây dựng cloud project.
