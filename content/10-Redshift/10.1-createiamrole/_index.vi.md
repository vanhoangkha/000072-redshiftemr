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


![Data Analysis on AWS](/images/10/1.png?featherlight=false&width=90pc)

2. Chọn **Redshift**.
  + Chọn **Redshift - customizable** dưới phần **Select your use case**.

![Data Analysis on AWS](/images/10/2.png?featherlight=false&width=90pc)

3. Nhấn **Next**.


![Data Analysis on AWS](/images/10/3.png?featherlight=false&width=90pc)

4.   Cho **Role Name** là ```Analyticsworkshop_RedshiftRole```.


![Data Analysis on AWS](/images/10/4.png?featherlight=false&width=90pc)

5. Check những policies sau:
    + **AmazonS3FullAccess**.a
    + **AWSGlueConsoleFullAccess**.
    + Tuỳ chọn thêm Tags:
      + workshop: AnalyticsOnAWS.
    + Nhấn **Create role**.

![Data Analysis on AWS](/images/10/5.png?featherlight=false&width=90pc)

6. Tạo role thành công.

![Data Analysis on AWS](/images/10/6.png?featherlight=false&width=90pc)

Tiếp theo chúng ta sẽ tiến hành tạo Redshift cluster.

