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

2. Tại trang **Crawler info**.
    + Crawler name: ```AnalyticsworkshopCrawler```.
    + Tuỳ chọn thêm tag:.
      + workshop: AnalyticsOnAWS.
    + Click **Next**.

![Architect](/images/2/4.png?width=90pc)

3. Tại trang **Specify crawler source type**.
  + Click Chọn **Data stores**.
  + Click **Next**.

![Architect](/images/2/5.png?width=90pc)

4. Tại trang **Add a data store**.
    + Choose a data store: **S3**.
    + Crawl data in: **Specified path in my account**.
    + Include path: ```s3://yourname-analytics-workshop-bucket/data/```.
    + Click **Next**.
    + Add another data store: **No**.
    + Click **Next**.

![Architect](/images/2/6.png?width=90pc)


5. Tại trang **Choose an IAM Role**.
    + Chọn: **Choose an existing IAM role**.
    + IAM role chọn: **AnalyticsworkshopGlueRole**.
    + Click **Next**.

![Architect](/images/2/7.png?width=90pc)


6. Tại trang **Schedule**.
    + Frequency: **Run on demand**.
    + Click **Next**.

7. Tại trang **Output**.
    + Click **Add database**.
    + Database name: **analyticsworkshopdb**.
    + Click **Create**.
    + Click **Next**.

![Architect](/images/2/8.png?width=90pc)

8. Tại trang **Review all steps**.
    + Kiểm tra lại tất cả cấu hình của bạn.
    + Click **Finish**.

9. Bạn sẽ thấy thông báo: **Crawler analyticsworkshopdb was created to run on demand.**.
    + Chọn vào crawler's check box.
    + Click **Run crawler** để chạy crawler lần đầu tiên.
    + Đợi vài phút để quá trình chạy hoàn tất.

![Architect](/images/2/9.png?width=90pc)


