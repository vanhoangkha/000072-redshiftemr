+++
title = "Khởi tạo và chạy job"
date = 2021
weight = 4
chapter = false
pre = "<b>5.4 </b>"
+++


#### Khởi tạo và chạy AWS Glue DataBrew job

1. Click **PROFILE** để xem lại kết quả profiling của raw dataset như summary, missing cells, duplicate rows, value distribution, và columns statistics, nó sẽ cho bạn insights về dữ liệu của bạn.

![Architect](/images/5/14.png?width=90pc)

2. Click **LINEAGE** ở góc bên phải.

![Architect](/images/5/15.png?width=90pc)

3. Bạn có thể thấy luồng dữ liệu của bạn, được trình bày để cung cấp về luồng dữ liệu với sự chuyển đổi qua tất cả các bước.

![Architect](/images/5/16.png?width=90pc)

4. Trở lại **GRID**, và Click **Create job**

![Architect](/images/5/17.png?width=90pc)

5. Điền vào những giá trị dưới đây:
  + Mục **Job details**.
    + Job Name: **AnalyticsOnAWS-GlueDataBrew-Job**.
  + Mục **Job output settings**.
    + File type: **GlueParquet**.
    + S3 location: **s3://yourname-analytics-workshop-bucket/data/processed-data/**.
  + Kéo xuống dưới phần **Permission**, và chọn role name mà bạn đã tạo ở bước đầu, và Click **Create and run job**.

![Architect](/images/5/18.png?width=90pc)

6. Bạn sẽ thấy 1 job đang trong tiến trình.

![Architect](/images/5/19.png?width=90pc)

7. Click **Jobs** ở menu bên trái, bạn sẽ thấy như màn hình dưới đây.
  + Click vào tên job.

![Architect](/images/5/20.png?width=90pc)

8. Ở đây bạn có thể coi lịch sử chạy, chi tiết job, và luồng dữ liệu.
  + Lịch sử chạy.

![Architect](/images/5/21.png?width=90pc)

  + Chi tiết về job.
![Architect](/images/5/22.png?width=90pc)

  + Luồng đi dữ liệu.
![Architect](/images/5/23.png?width=90pc)
