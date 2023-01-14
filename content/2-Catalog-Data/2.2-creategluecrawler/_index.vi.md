+++
title = "Tạo AWS Glue Crawlers"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

#### Tạo AWS Glue Crawlers

Ở bước này, chúng ta sẽ đi đến AWS Glue Console và tạo 1 glue crawlers để khám phá schema của dữ liệu mới được lấy vào trong S3.

1. Truy cập giao diện quản trị của dịch vụ [AWS Glue](https://console.aws.amazon.com/glue/home?region=ap-southeast-1)
+ Ở khung bên trái, chọn **Crawlers** > Click chọn **Add Crawler**

![Data Analysis on AWS](/images/2/4.png?featherlight=false&width=90pc)

2. Tại trang **Crawler info**.
    + Crawler name: ```AnalyticsworkshopCrawler```.
    + Tuỳ chọn thêm tag:.
      + workshop: AnalyticsOnAWS.
    + Click **Next**.

![Data Analysis on AWS](/images/2/5.png?featherlight=false&width=90pc)

3. Đối với **Choose data source and classifiers**

   - Chọn **Not yet**
   - Chọn **Add a data source**

![Data Analysis on AWS](/images/2/6.png?featherlight=false&width=90pc)

4. Tại trang Add a data store.
   - Choose a data store: **S3**.
   - Crawl data in: **Specified path in my account**.
   - Include path: **s3://yourname-analytics-workshop-bucket/data/**.
   - Click **Next**.
   - Add another data store: **No**.
   - Click **Next**.

![Data Analysis on AWS](/images/2/7.png?featherlight=false&width=90pc)

5. Hoàn thành thêm data source và chọn **Next**

![Data Analysis on AWS](/images/2/8.png?featherlight=false&width=90pc)

6. Tại trang **Choose an IAM Role**.
   - Chọn: **Choose an existing IAM role**.
   - IAM role chọn: **AnalyticsworkshopGlueRole**.
   - Click **Next**.

![Data Analysis on AWS](/images/2/9.png?featherlight=false&width=90pc)

7. Sau đó, chúng ta tạo **Database**

   - Nhập name: **```analyticsworkshopdb```**
   - Chọn **Create database**

![Data Analysis on AWS](/images/2/10.png?featherlight=false&width=90pc)

8. Hoàn thành tạo database.

![Data Analysis on AWS](/images/2/11.png?featherlight=false&width=90pc)

9. Đối với **Set output and scheduling**

   - Click **Add database**.
   - Database name: **analyticsworkshopdb**.
   - Click **Create**.
   - Frequency: **Run on demand**.
   - Click Next.

![Data Analysis on AWS](/images/2/12.png?featherlight=false&width=90pc)

10. Tại trang **Review all steps**.

    - Kiểm tra lại tất cả cấu hình của bạn.
    - Click **Create crawler**.

![Data Analysis on AWS](/images/2/13.png?featherlight=false&width=90pc)

11. Hoàn thành tạo **crawler**

![Data Analysis on AWS](/images/2/14.png?featherlight=false&width=90pc)

12.  Bạn kiểm tra bằng cách **Run**

![Data Analysis on AWS](/images/2/00016.png?featherlight=false&width=90pc)

13. **Run** thành công.

![Data Analysis on AWS](/images/2/00017.png?featherlight=false&width=90pc)