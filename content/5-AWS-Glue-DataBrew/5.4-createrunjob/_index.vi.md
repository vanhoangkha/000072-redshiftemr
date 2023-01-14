+++
title = "Khởi tạo và chạy job"
date = 2021
weight = 4
chapter = false
pre = "<b>5.4 </b>"
+++


#### Khởi tạo và chạy AWS Glue DataBrew job

1. Click **PROFILE** để xem lại kết quả profiling của raw dataset như summary, missing cells, duplicate rows, value distribution, và columns statistics, nó sẽ cho bạn insights về dữ liệu của bạn.

![Data Analysis on AWS](/images/5/20.png?featherlight=false&width=90pc)

2. Click **LINEAGE** ở góc bên phải.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)

3. Bạn có thể thấy luồng dữ liệu của bạn, được trình bày để cung cấp về luồng dữ liệu với sự chuyển đổi qua tất cả các bước.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)

4. Trở lại **GRID**, và Click **Create job**

![Data Analysis on AWS](/images/5/22.png?featherlight=false&width=90pc)

5. Điền vào những giá trị dưới đây:
  + Mục **Job details**.
    + Job Name: **AnalyticsOnAWS-GlueDataBrew-Job**.
  + Mục **Job output settings**.
    + File type: **GlueParquet**.
    + S3 location: **s3://yourname-analytics-workshop-bucket/data/processed-data/**.


![Data Analysis on AWS](/images/5/23.png?featherlight=false&width=90pc)

6. Kéo xuống dưới phần **Permission**, và chọn role name mà bạn đã tạo ở bước đầu, và Click **Create and run job**.

![Data Analysis on AWS](/images/5/24.png?featherlight=false&width=90pc)

7. Bạn sẽ thấy 1 job đang trong tiến trình.

8. Click **Jobs** ở menu bên trái, bạn sẽ thấy như màn hình dưới đây.
  + Click vào tên job.

![Data Analysis on AWS](/images/5/26.png?featherlight=false&width=90pc)

9. Ở đây bạn có thể coi lịch sử chạy, chi tiết job, và luồng dữ liệu.
  + Lịch sử chạy.

![Data Analysis on AWS](/images/5/27.png?featherlight=false&width=90pc)
  + Chi tiết về job.
  
![Data Analysis on AWS](/images/5/28.png?featherlight=false&width=90pc)

  + Luồng đi dữ liệu.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)

