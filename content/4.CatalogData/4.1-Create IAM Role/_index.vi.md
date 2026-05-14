---
title : "Tạo IAM Role"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

#### Tạo IAM Role

Trong bước này, chúng ta sẽ truy cập vào Bảng điều khiển IAM và tạo một role dịch vụ AWS Glue mới. Điều này cho phép AWS Glue truy cập vào dữ liệu được lưu trữ trong S3 và tạo các thực thể cần thiết trong Bộ sưu tập dữ liệu Glue.

1. Đi đến: 
- Chọn  vào Tạo role
- Chọn dịch vụ sẽ sử dụng role này: Glue
- Chọn  vào Next

![Data Analytics on AWS](/images/4/0001.png?featherlight=false&width=90pc)

2. Tìm kiếm AmazonS3FullAccess
- Chọn hộp kiểm của mục này
- Tìm kiếm AWSGlueServiceRole
- Chọn hộp kiểm của mục này
- Chọn  vào Next

![Data Analytics on AWS](/images/4/0002.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/0003.png?featherlight=false&width=90pc)

3. Tên role: AnalyticsworkshopGlueRole
- Đảm bảo rằng chỉ có hai policy được đính kèm vào role này (AmazonS3FullAccess, AWSGlueServiceRole)
- Tùy chọn thêm Tag, ví dụ: workshop: AnalyticsOnAWS
- Chọn  vào Create role 

![Data Analytics on AWS](/images/4/0004.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/4/0005.png?featherlight=false&width=90pc)

4. Tạo role thành công.

![Data Analytics on AWS](/images/4/0006.png?featherlight=false&width=90pc)
