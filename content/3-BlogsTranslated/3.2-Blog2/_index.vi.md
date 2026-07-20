---
title: "Thực hành các dịch vụ AWS core: EC2, S3, VPC và Database"
date: 2026-07-02
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

Sau khi đã quen hơn với AWS account và console, giai đoạn tiếp theo trong quá trình học của tôi là thực hành các dịch vụ AWS core. Tôi tập trung vào những dịch vụ xuất hiện trong rất nhiều project cloud: Amazon EC2, Amazon S3, Amazon VPC, Security Group, IAM và các dịch vụ database như Amazon RDS/Aurora. Những tác vụ này giúp tôi hiểu các thành phần nền tảng của hạ tầng cloud.

Dịch vụ đầu tiên tôi thực hành kỹ hơn là Amazon EC2. EC2 giúp tôi hiểu cách tạo và quản lý máy chủ ảo trên AWS. Khi launch một instance, tôi phải chọn AMI, instance type, key pair, network setting và security group. Mỗi lựa chọn tương ứng với một khái niệm khác nhau. AMI là image hệ điều hành, instance type thể hiện tài nguyên compute, key pair hỗ trợ truy cập an toàn, còn security group kiểm soát traffic vào/ra.

Bài học thực tế từ EC2 là tài nguyên cloud cần được quản lý có chủ đích. Việc khởi tạo instance rất dễ, nhưng stop hoặc terminate instance không dùng nữa cũng quan trọng không kém. Tôi học cách kiểm tra trạng thái instance, public IP, security group rule và chi phí đang phát sinh. Điều này giúp tôi liên kết việc dùng compute với kiểm soát chi phí.

Dịch vụ quan trọng tiếp theo là Amazon S3. S3 là dịch vụ object storage, được dùng trong rất nhiều workload trên AWS vì đơn giản, bền vững và linh hoạt. Tôi thực hành tạo bucket, upload object, tổ chức file và kiểm tra quyền truy cập bucket. Qua tác vụ này, tôi hiểu rằng storage không chỉ là nơi để đưa file lên. Nó còn liên quan đến access control, cách đặt tên, lifecycle và bảo vệ public access.

S3 cũng giúp tôi hiểu rõ hơn vì sao permission quan trọng. Một bucket không nên public nếu không có lý do rõ ràng. Trong hầu hết use case ứng dụng, file nên được giữ private và truy cập thông qua logic ứng dụng có kiểm soát. Ý tưởng này về sau rất hữu ích với project ticket portal của tôi, nơi S3 có thể lưu file đính kèm còn Lambda và IAM kiểm soát cách truy cập file.

Một chủ đề lớn khác là networking với Amazon VPC. Ban đầu, VPC khó hiểu hơn EC2 hoặc S3 vì nó liên quan đến subnet, route table, internet gateway và security group. Tuy nhiên, khi thực hành các tác vụ VPC, tôi hiểu rõ hơn cách tài nguyên AWS giao tiếp với nhau. VPC giống như một khu vực mạng riêng trên cloud. Subnet chia nhỏ network, route table xác định đường đi của traffic, còn security group đóng vai trò firewall ảo cho resource.

Học VPC cũng giúp tôi hiểu vì sao thiết kế network ảnh hưởng đến security. Nếu một resource không cần truy cập trực tiếp từ internet, không nên đặt nó vào public path một cách không cần thiết. Dù project cuối của tôi dùng chủ yếu serverless services, kiến thức VPC vẫn quan trọng vì nhiều hệ thống thực tế kết hợp cả serverless, managed services và networked resources.

Tôi cũng thực hành các khái niệm database với Amazon RDS và Aurora. Các dịch vụ này cho thấy cách database quan hệ managed hoạt động trên AWS. Tôi học rằng RDS giúp giảm việc quản lý database server thủ công, nhưng người dùng vẫn cần quan tâm instance size, database engine, networking, backup và security. Trải nghiệm này giúp tôi so sánh RDS với DynamoDB về sau.

Việc so sánh RDS và DynamoDB là một điểm học tập hữu ích. RDS phù hợp khi ứng dụng cần cấu trúc quan hệ, SQL query, join và hành vi database truyền thống. DynamoDB phù hợp hơn với access pattern đơn giản, khả năng mở rộng cao và ứng dụng serverless. Với hệ thống ticket có thao tác dự đoán được như tạo, liệt kê, cập nhật và xóa, DynamoDB có thể đơn giản hơn. Nhưng việc học RDS trước giúp tôi hiểu rằng lựa chọn database phải dựa trên yêu cầu ứng dụng.

Trong giai đoạn này, tôi tiếp tục thực hành workshop trên AWS Study Group và ghi chú lại quá trình học. Tôi nhận ra rằng các tác vụ hands-on hiệu quả hơn việc chỉ đọc tài liệu. Khi tự tạo resource, cấu hình, test, gặp lỗi và sửa lỗi, tôi nhớ dịch vụ tốt hơn. Các lỗi cũng có giá trị học tập. Ví dụ, lỗi kết nối thường liên quan đến security group, còn lỗi truy cập thường liên quan đến IAM permission.

Giá trị lớn nhất của giai đoạn này là xây dựng sự tự tin thực hành. EC2 giúp hiểu compute. S3 giúp hiểu object storage và permission. VPC giúp hiểu networking và isolation. RDS/Aurora giúp hiểu managed relational database. IAM và Billing kết nối các tác vụ đó với security và cost awareness.

Kết thúc giai đoạn này, tôi có cái nhìn rõ hơn về cách hạ tầng AWS được tổ chức. Nền tảng đó giúp tôi dễ chuyển sang serverless services và xây dựng luồng ứng dụng thực tế với API Gateway, Lambda, Cognito, DynamoDB, S3 và CloudWatch.

## Tài liệu tham khảo

- [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- [What is Amazon S3?](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [What is Amazon VPC?](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [Amazon RDS User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
- [Amazon Aurora User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)
