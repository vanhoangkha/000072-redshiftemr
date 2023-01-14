+++
title = "Tạo Glue Studio job"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1 </b>"
+++

#### Tạo Glue Studio job

1. Truy cập đến giao diện [Glue Studio Console](https://console.aws.amazon.com/gluestudio/home?region=ap-southeast-1)
  + Click - biểu tượng **3 gạch** ở góc bên trái.

2. Click - **Jobs** và chọn **Create job from a blank graph**.
  + Click **Create**.

![Data Analysis on AWS](/images/4/1.png?featherlight=false&width=90pc)

3. Click - **Source** và chọn **S3**

4. Click tab **Data source properties - S3** trong cửa sổ cấu hình ở bên phải màn hình.
+ Dưới **S3 source type** chọn **Data Catalog table**.
+ Chọn những giá trị như dưới đây.
  + Database - **analyticsworkshopdb**.
  + Table - **raw**.

![Data Analysis on AWS](/images/4/2.png?featherlight=false&width=90pc)

5. Tiếp tục làm bước tương tự để thêm reference_data từ S3. Click - **Source** và chọn **S3**.

![Data Analysis on AWS](/images/4/3.png?featherlight=false&width=90pc)

6. Click tab **Data source properties - S3** trong cửa sổ cấu hình ở bên phải màn hình.
+ Dưới **S3 source type** chọn **Data Catalog table**.
+ Chọn những giá trị như dưới đây.
  + Database - **analyticsworkshopdb**.
  + Table - **reference_data**.

![Data Analysis on AWS](/images/4/4.png?featherlight=false&width=90pc)


