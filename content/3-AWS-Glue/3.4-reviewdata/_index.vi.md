+++
title = "Kiểm tra dữ liệu"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++


#### Xác Nhận - Những dữ liệu đã được chuyển đổi /  xử lí đã đi đến S3

Sau khi chúng ta chạy ETL script thành công, chúng ta sẽ quay lại giao diện dịch vụ S3 để kiểm tra dữ liệu sau khi được chuyển đổi.

1. Truy cập [giao diện quản trị S3](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)

2. Click - **yourname-analytics-workshop-bucket > data**.
  + Mở folder **processed-data**:
  + Kiểm tra các tập tin với format là **.parquet** đã được tạo trong folder.
  
![Data Analysis on AWS](/images/3/00029.png?featherlight=false&width=90pc)

Chúc mừng bạn chuyển đổi dữ liệu với AWS Glue thành công, chúng ta có thể query dữ liệu bằng cách sử dụng Amazon Athena.
Chúng ta vẫn còn nhiều cách để xử lí dữ liệu như là sử dụng Glue Studio, Glue DataBrew và Amazon EMR.
