---
title: "Học Serverless, Authentication, Monitoring và Security trên AWS"
date: 2026-07-03
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

Sau khi thực hành các dịch vụ AWS core, tôi chuyển sang các tác vụ xây dựng ứng dụng serverless. Giai đoạn này quan trọng vì giúp tôi hiểu cách ứng dụng cloud hiện đại có thể chạy mà không cần quản lý server truyền thống. Thay vì tạo và duy trì EC2 instance cho mọi chức năng backend, tôi học cách các dịch vụ như API Gateway, Lambda, Cognito, DynamoDB, S3, CloudWatch và IAM phối hợp với nhau.

Dịch vụ serverless đầu tiên tôi tập trung là AWS Lambda. Lambda thay đổi cách tôi nhìn về backend processing. Với cách truyền thống, application server chạy liên tục và chờ request. Với Lambda, function chỉ chạy khi được invoke. Mô hình này phù hợp với workflow theo sự kiện như tạo ticket, cập nhật trạng thái, xử lý file upload hoặc trả dữ liệu cho frontend.

Khi thực hành Lambda, tôi học cách chia logic thành các function nhỏ. Một Lambda function tốt nên có trách nhiệm rõ ràng: validate input, xử lý logic, gọi dịch vụ AWS khác và trả response. Tôi cũng học rằng quyền của Lambda được kiểm soát bằng execution role. Nếu function cần ghi vào DynamoDB, upload lên S3 hoặc ghi log vào CloudWatch, IAM role phải cho phép các action đó.

Dịch vụ quan trọng tiếp theo là Amazon API Gateway. API Gateway giúp tôi hiểu cách frontend giao tiếp với backend logic. Tôi thực hành định nghĩa route, chọn HTTP method, bật CORS và kết nối route với Lambda. Nhờ đó, khái niệm REST API trở nên thực tế hơn. Một route như `POST /tickets` không chỉ là URL. Nó đại diện cho một workflow thật: frontend gửi dữ liệu, API Gateway nhận request, Lambda xử lý và response trả về người dùng.

Authentication là một mảng học tập quan trọng khác. Tôi tìm hiểu Amazon Cognito vì project cần user và admin access. Cognito giúp tôi hiểu sign-up, sign-in, user pool, app client, JWT token và group. Ban đầu, luồng token khá khó hình dung. Điểm chính tôi học được là Cognito xác thực người dùng và trả JWT token về frontend. Sau đó frontend gửi token đó khi gọi API Gateway. API Gateway có thể xác thực token bằng JWT Authorizer trước khi invoke Lambda.

Việc phân quyền cũng rõ hơn thông qua Cognito groups. User thường chỉ nên gửi ticket và xem ticket của chính mình. Admin có thể xem toàn bộ ticket, cập nhật trạng thái, thêm ghi chú và xóa ticket. Từ đây tôi hiểu authentication và authorization là hai khái niệm khác nhau. Authentication xác nhận người dùng là ai. Authorization quyết định người đó được phép làm gì.

Với lưu trữ dữ liệu, tôi thực hành Amazon DynamoDB. DynamoDB khác database quan hệ vì thiết kế table nên bắt đầu từ access pattern. Với ticket portal, tôi cần nghĩ đến các thao tác như tạo ticket, xem ticket của user, liệt kê toàn bộ ticket cho admin, cập nhật trạng thái và xóa ticket. Điều này giúp tôi hiểu vì sao thiết kế NoSQL nên đi theo query của ứng dụng.

Tôi cũng sử dụng Amazon S3 cho lưu trữ file đính kèm. Tác vụ này giúp tôi hiểu rằng file và record trong database cần được liên kết cẩn thận. File thật có thể lưu trong S3, còn item ticket trong DynamoDB lưu metadata như S3 object key. Cách này giúp database gọn hơn nhưng ứng dụng vẫn tìm được file liên quan.

Monitoring là phần học tập rất quan trọng. Khi có lỗi, CloudWatch Logs là nơi đầu tiên cần kiểm tra. Tôi học cách xem Lambda invocation logs, lỗi validation, lỗi permission và lỗi khi gọi DynamoDB hoặc S3. Việc này giúp quá trình debug có hệ thống hơn. Thay vì đoán, tôi có thể đọc log để biết request lỗi ở bước nào.

Security và cleanup cũng là các tác vụ không thể bỏ qua. Tôi rà soát IAM least privilege, CORS, private S3 bucket và protected API routes. Tôi cũng học cách xóa tài nguyên không dùng và kiểm tra Billing Dashboard. Một project cloud không kết thúc ở việc chức năng chạy được một lần. Nó còn cần đủ an toàn trong phạm vi của mình, có log để quan sát và được cleanup để tránh phát sinh chi phí.

Bài học lớn nhất trong giai đoạn này là serverless không có nghĩa là không có kiến trúc. Nó có nghĩa là kiến trúc được xây từ các managed services. Mỗi dịch vụ có một trách nhiệm riêng và developer cần kết nối chúng đúng cách. API Gateway xử lý điểm vào API, Lambda xử lý logic, Cognito xử lý identity, DynamoDB lưu dữ liệu, S3 lưu file, CloudWatch ghi log và IAM kiểm soát quyền.

Giai đoạn học này giúp tôi chuyển từ việc thực hành từng dịch vụ riêng lẻ sang hiểu một workflow ứng dụng end-to-end. Nó cũng giúp tôi biết cách viết workshop rõ ràng hơn, vì mỗi bước đều có mục đích: deploy frontend, cấu hình authentication, tạo API routes, viết backend logic, lưu dữ liệu, kiểm thử luồng user/admin, xem logs và cleanup tài nguyên.

## Tài liệu tham khảo

- [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
- [Amazon API Gateway REST API documentation](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-rest-api.html)
- [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)
- [What is Amazon DynamoDB?](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
- [Sending Lambda logs to CloudWatch Logs](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html)
