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

![Architect](/images/2/1.png?width=90pc)

2. Thực hiện tìm kiếm policy **AmazonS3FullAccess**.
  + Click chọn policy **AmazonS3FullAccess**.

3. Thực hiện tìm kiếm policy **AWSGlueServiceRole**.
  + Click chọn policy **AWSGlueServiceRole**.
  + Click **Next: Tags**

4. Tại trang **Add tags**.
  + Thêm tag Key = **workshop** và Value = **AnalyticsOnAWS**.
  + Click **Next: Review**
![Architect](/images/2/2.png?width=90pc)

5. Tại trang **Create role**.
  + Role name: ```AnalyticsworkshopGlueRole```.
  + Kiểm tra 2 policy chúng ta đã thêm vào ở bước 2 và 3 (**AmazonS3FullAccess, AWSGlueServiceRole**).
  + Click **Create role**.

![Architect](/images/2/3.png?width=90pc)

