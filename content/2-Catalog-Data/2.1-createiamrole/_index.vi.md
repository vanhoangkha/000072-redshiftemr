+++
title = "Tạo IAM Role"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Tạo IAM Role

Ở bước này, chúng ta sẽ đi đến IAM Console và tạo 1 role service mới cho AWS Glue. Việc này sẽ giúp AWS Glue có thể truy cập dữ liệu lưu trong S3 và có thể tạo những entities cần thiết trong Glue Data Catalog.

1. Đi đến giao diện quản trị [IAM Roles](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles)
+ Click **Create role**.
  + Chọn service sẽ sử dụng role là : **Glue**.
  + Click **Next: Permissions**.

![Data Analysis on AWS](/images/2/1.png?featherlight=false&width=90pc)

2. Role name: **AnalyticsworkshopGlueRole**.

![Data Analysis on AWS](/images/2/2.png?featherlight=false&width=90pc)

3. Thực hiện tìm kiếm policy **AmazonS3FullAccess**.
   - Click chọn policy **AmazonS3FullAccess**.
   - Thực hiện tìm kiếm policy **AWSGlueServiceRole**.
   - Click chọn policy **AWSGlueServiceRole**.
   - Tại trang **Add tags**.
   - Thêm tag Key = **workshop** và Value = **AnalyticsOnAWS**.
   - Click **Create role**

![Data Analysis on AWS](/images/2/3.png?featherlight=false&width=90pc)

4. Hoàn thành tạo role.

![Data Analysis on AWS](/images/2/3.1.png?featherlight=false&width=90pc)
