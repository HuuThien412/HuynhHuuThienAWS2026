---
title: "Chia sẻ và phản hồi"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

## Chia sẻ quá trình thực hiện

Trong quá trình thực tập, tôi bắt đầu từ việc làm quen với AWS Cloud và các dịch vụ nền tảng, sau đó từng bước thực hành các chủ đề nâng cao hơn như mạng, bảo mật, cơ sở dữ liệu, serverless, CI/CD, giám sát và kiểm soát chi phí. Việc ghi worklog theo từng tuần giúp tôi nhìn lại rõ hơn mình đã học gì, gặp khó khăn ở đâu và cần bổ sung phần nào trước khi hoàn thiện báo cáo.

Project chính của tôi là **Campus IT Support Ticket Portal**, một hệ thống web hỗ trợ tiếp nhận và xử lý yêu cầu hỗ trợ kỹ thuật trong môi trường trường học. Hệ thống có hai luồng chính: người dùng gửi ticket, theo dõi trạng thái và upload file đính kèm; quản trị viên xem danh sách ticket, lọc yêu cầu, cập nhật trạng thái, thêm ghi chú xử lý và xóa ticket khi cần.

Điểm đáng chú ý nhất của project là hệ thống được xây dựng theo kiến trúc serverless trên AWS. Frontend được triển khai bằng **AWS Amplify Hosting**, xác thực sử dụng **Amazon Cognito**, API được quản lý bằng **Amazon API Gateway**, backend xử lý bằng **AWS Lambda**, dữ liệu lưu trong **Amazon DynamoDB**, file đính kèm lưu ở **Amazon S3**, thông báo sử dụng **Amazon SES**, log theo dõi bằng **Amazon CloudWatch** và quyền truy cập được kiểm soát bằng **AWS IAM**.

Thông qua project này, tôi hiểu rõ hơn rằng một ứng dụng cloud hoàn chỉnh không chỉ nằm ở việc tạo từng dịch vụ riêng lẻ. Điều quan trọng là phải thiết kế đúng luồng kết nối giữa các dịch vụ, phân quyền hợp lý, kiểm thử từng chức năng và ghi lại tài liệu đủ rõ để người khác có thể hiểu quá trình triển khai.

## Những nội dung học được

- Hiểu cách frontend được host và tự động deploy thông qua AWS Amplify Hosting.
- Biết cách dùng Amazon Cognito để đăng ký, đăng nhập, tạo JWT token và phân quyền theo group `Users`/`Admins`.
- Hiểu vai trò của API Gateway trong việc nhận request, xác thực JWT và chuyển tiếp đến Lambda.
- Thực hành viết luồng xử lý ticket bằng Lambda theo các chức năng tạo, xem, cập nhật và xóa ticket.
- Biết cách lưu dữ liệu dạng NoSQL bằng DynamoDB và quản lý file đính kèm bằng S3.
- Làm quen với email notification bằng Amazon SES và luồng cập nhật realtime thông qua DynamoDB Streams/WebSocket.
- Biết dùng CloudWatch Logs để kiểm tra lỗi và theo dõi hoạt động của backend.
- Có ý thức hơn về IAM least privilege và kiểm soát chi phí bằng Billing Dashboard.

## Khó khăn gặp phải

Trong quá trình thực hiện, tôi gặp một số khó khăn khi kết nối các dịch vụ với nhau. Ví dụ, luồng xác thực bằng Cognito và JWT Authorizer ban đầu khá dễ nhầm vì frontend, API Gateway và Lambda đều cần xử lý đúng token và quyền của người dùng. Phần phân quyền giữa user thường và admin cũng cần kiểm tra kỹ để tránh trường hợp user có thể truy cập chức năng quản trị.

Một khó khăn khác là việc debug lỗi backend. Khi request từ frontend không hoạt động đúng, tôi cần kiểm tra nhiều lớp khác nhau như cấu hình API Gateway, log Lambda, dữ liệu DynamoDB, quyền IAM hoặc cấu hình CORS. Sau khi quen dần với CloudWatch Logs, tôi có thể xác định lỗi nhanh hơn và biết cách kiểm thử từng bước.

Ngoài ra, phần tài liệu cũng mất nhiều thời gian vì phải đảm bảo Worklog, Proposal, Blogs Posted, Workshop, Self-Assessment và Sharing and Feedback thống nhất với nhau. Khi kiến trúc hoặc nội dung project thay đổi, các phần tài liệu liên quan cũng cần được cập nhật lại để tránh mâu thuẫn.

## Phản hồi và đề xuất

Theo trải nghiệm của tôi, hình thức học theo workshop rất phù hợp với sinh viên vì vừa có lý thuyết vừa có thao tác thực hành. Tuy nhiên, để việc học hiệu quả hơn, người học nên ghi chú lại lỗi gặp phải ngay trong lúc thực hiện, chụp màn hình sau mỗi bước quan trọng và cập nhật sơ đồ kiến trúc khi project thay đổi.

Tôi cũng nhận thấy cần chuẩn bị kỹ phần cleanup và theo dõi Billing Dashboard. Với người mới học AWS, đôi khi chỉ tập trung vào việc tạo tài nguyên mà quên kiểm tra tài nguyên còn chạy sau khi thực hành. Việc theo dõi chi phí nên được đưa vào thói quen từ đầu.

Nếu tiếp tục phát triển project, tôi muốn cải thiện thêm các phần sau:

- Hoàn thiện dashboard thống kê ticket theo trạng thái, mức độ ưu tiên và nhóm sự cố.
- Cải thiện giao diện quản trị để việc lọc và xử lý ticket rõ ràng hơn.
- Bổ sung audit log cho các thao tác của admin.
- Hoàn thiện custom domain nếu tài khoản và quá trình xác thực domain cho phép.
- Tối ưu lại IAM policy để quyền truy cập giữa các dịch vụ chặt chẽ hơn.

## Kết luận

Nhìn chung, quá trình thực tập giúp tôi có cái nhìn thực tế hơn về cách xây dựng một ứng dụng serverless trên AWS. Tôi không chỉ học được cách sử dụng từng dịch vụ, mà còn hiểu được cách thiết kế luồng hệ thống, kiểm soát quyền, theo dõi lỗi, quản lý chi phí và trình bày tài liệu kỹ thuật. Đây là nền tảng quan trọng để tôi tiếp tục học sâu hơn về cloud computing và phát triển các project AWS sau này.
