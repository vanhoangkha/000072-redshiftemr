+++
title = "Tạo Redshift IAM role"
date = 2021
weight = 1
chapter = false
pre = "<b>10.1 </b>"
+++

#### Tạo Redshift IAM role

Ở bước này chúng ta sẽ tạo IAM role cho Redshift cluster

1. Truy cập đến [giao diện IAM console](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles).
  + Nhấn **Create role**.
  + Chọn **Redshift**.
  + Chọn **Redshift - customizable** dưới phần **Select your use case**.

![Architect](/images/10/1.png?width=90pc)

2. Nhấn **Next: Permissions**.
  + Ở thanh tìm kiếm, tìm và check những policies sau:
    + **AmazonS3FullAccess**.
    + **AWSGlueConsoleFullAccess**.
  + Nhấn **Next: Tags**.
    + Tuỳ chọn thêm Tags:
      + workshop: AnalyticsOnAWS.
    + Nhấn **Next: Review**.

![Architect](/images/10/2.png?width=90pc)

3. Cho **Role Name** là ```Analyticsworkshop_RedshiftRole```.
  + Xác nhận 2 policies dưới đây đã được gắn.
    + **AmazonS3FullAccess**.
    + **AWSGlueConsoleFullAccess**.
  + Nhấn **Create Role**.

![Architect](/images/10/3.png?width=90pc)

Tiếp theo chúng ta sẽ tiến hành tạo Redshift cluster.