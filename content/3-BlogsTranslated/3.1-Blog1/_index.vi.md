---
title: "Học AWS từ tạo tài khoản, IAM và kiểm soát chi phí"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Khi bắt đầu học AWS, tôi nhận ra bài học đầu tiên không phải là xây dựng ngay một hệ thống lớn. Bài học đầu tiên là học cách sử dụng một cloud account sao cho an toàn. AWS cung cấp rất nhiều dịch vụ mạnh, nhưng điều đó cũng có nghĩa là người học cần hiểu về tài khoản, billing, phân quyền và quản lý tài nguyên cơ bản ngay từ đầu.

Tác vụ học tập đầu tiên của tôi là tạo và chuẩn bị AWS account. Sau khi đăng nhập, tôi dành thời gian làm quen với AWS Management Console. Ban đầu giao diện console khá rộng vì mỗi dịch vụ có một trang quản lý, cấu hình và thuật ngữ riêng. Tôi học cách tìm kiếm dịch vụ, kiểm tra region đang sử dụng, mở dashboard của từng dịch vụ và nhận biết các khu vực quen thuộc như EC2, S3, IAM, Billing và CloudWatch. Việc làm quen này giúp các bước thực hành sau dễ hơn vì tôi có thể thao tác trong môi trường AWS tự tin hơn.

Tác vụ quan trọng tiếp theo là kiểm soát chi phí. Khi làm việc ở môi trường local, sai sót thường chỉ làm mất thời gian. Nhưng khi làm việc trên cloud, sai sót có thể tạo ra chi phí thật. Vì vậy, tôi học cách kiểm tra Billing Dashboard và AWS Free Tier thường xuyên. Tôi cũng chú ý những dịch vụ có thể phát sinh phí nếu để tài nguyên chạy sau khi test, ví dụ EC2 instance, NAT Gateway, Route 53 domain, load balancer hoặc dữ liệu lưu trữ. Thói quen này giúp tôi hiểu rằng cost control là một phần của cloud engineering, không chỉ là việc quản trị tài khoản.

Một bài học nền tảng khác là IAM. IAM là một trong những dịch vụ quan trọng nhất của AWS vì nó kiểm soát ai được truy cập tài nguyên nào. Tôi học sự khác nhau giữa user, group, role và policy. Ban đầu, việc cấp quyền rộng có vẻ tiện hơn khi thực hành. Tuy nhiên, AWS best practices khuyến khích nguyên tắc least privilege: mỗi identity hoặc service chỉ nên có đúng quyền nó cần. Ý tưởng này trở nên quan trọng hơn khi tôi làm việc với Lambda, DynamoDB, S3 và API Gateway.

Ví dụ, nếu một Lambda function chỉ cần ghi dữ liệu ticket vào DynamoDB, function đó không nên có quyền administrator. Nếu một function cần upload file lên S3, IAM role nên giới hạn trong bucket và action cần thiết. Việc học IAM từ sớm giúp tôi hiểu rằng security cần được tính từ đầu, kể cả với project sinh viên.

Tôi cũng thực hành một số tác vụ EC2 cơ bản. Việc tạo và xóa EC2 instance giúp tôi hiểu khái niệm máy chủ ảo trên AWS. Tôi học về AMI, instance type, key pair và security group. Dù project cuối cùng của tôi tập trung nhiều hơn vào serverless, EC2 vẫn hữu ích vì nó giúp tôi hiểu mô hình compute truyền thống trước khi so sánh với serverless compute.

Ngoài ra, tôi tìm hiểu sơ bộ Amazon Bedrock. Tôi không dùng Bedrock làm dịch vụ chính trong project cuối, nhưng việc tìm hiểu dịch vụ này giúp tôi thấy AWS không chỉ là hạ tầng. AWS còn có các dịch vụ managed ở tầng cao hơn, hỗ trợ phát triển ứng dụng hiện đại và AI.

Bài học chính trong giai đoạn đầu khá rõ ràng: trước khi xây dựng ứng dụng trên AWS, người học cần hiểu môi trường tài khoản. Một quá trình học AWS tốt nên bắt đầu từ việc dùng account an toàn, kiểm soát billing, hiểu IAM và làm quen console. Những kỹ năng này có vẻ cơ bản nhưng giúp tránh nhiều lỗi phổ biến về sau.

Với tôi, giai đoạn này tạo nền tảng cho toàn bộ quá trình thực tập. Sau khi biết cách thao tác trên console, kiểm tra chi phí và suy nghĩ về quyền truy cập, tôi sẵn sàng hơn để thực hành các dịch vụ core và xây dựng project serverless ticket portal.

## Tài liệu tham khảo

- [Getting started with AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/getting-started-with-aws.html)
- [AWS Management Console](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-is.html)
- [AWS Billing and Cost Management](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
