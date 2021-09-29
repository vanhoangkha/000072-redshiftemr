+++
title = "Kiểm tra Glue catalog"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Xác nhận table mới được tạo trong catalog

Điều hướng đến Glue Catalog và khám phá dữ liệu đã được crawl

1. Truy cập [trang quản trị database của dịch vụ AWS Glue](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=databases)
  + Click **analyticsworkshopdb**.
  + Click **Tables in analyticsworkshopdb**.
  + Click **raw**.

![Architect](/images/2/10.png?width=90pc)

2. Kiểm tra các schema của dataset.
    + Tìm những dữ liệu ```averageRecordSize```, ```recordCount```, ```compressionType```

![Architect](/images/2/12.png?width=90pc)
   
Tiếp theo chúng ta sẽ thực hiện truy vấn dữ liệu sử dụng **Amazon Athena**.


