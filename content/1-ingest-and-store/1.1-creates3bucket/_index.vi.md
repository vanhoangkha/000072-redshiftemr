+++
title = "Tạo S3 Bucket"
date = 2021
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Tạo S3 Bucket

Ở bước này, chúng ta sẽ đi đến console của S3 và tạo S3 bucket mà sẽ sử dụng xuyên suốt bài lab.

1. Đăng nhập vào [AWS Console](https://console.aws.amazon.com/console/home?region=ap-southeast-1)

2. Đi đến S3 Console và tạo bucket mới ở Region ap-southeast-1:

+ Truy cập đến [giao diện quản trị S3](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)
+ Click - **Create Bucket**.
  + Bucket Name: ```yourname-analytics-workshop-bucket```.
  + Region : Asia Pacific (Singapore).
  + Tuỳ chọn thêm Tags, e.g.:
    + workshop: AnalyticsOnAWS.
  + Click **Create Bucket**.

![Architect](/images/1/1.png?width=90pc)

3. Thêm dữ liệu reference.
  + Mở - ```yourname-analytics-workshop-bucket```.
    + Click - **Create folder**.
      + Folder mới tên : ```data```.
      + Click - **Save**.

![Architect](/images/1/2.png?width=90pc)

4. Mở folder **data**.
    + Click - **Create folder** (trong data folder).
      + Folder mới : ```reference_data```.
      + Click - **Save**.

![Architect](/images/1/3.png?width=90pc)

5. Mở folder **reference_data**.
    + Tải file này xuống máy của bạn: [tracks_list.json](https://intro-to-analytics-on-aws.workshop.aws/data/tracks_list.json)
    + Bạn cũng có thể tải file tracks_list.json ở phần tải về dưới đây:

{{%attachments style="orange" title="tracks_list.json" pattern=".*(json)"/%}}

      + Trong S3 Console - Click chọn **Upload**.
        + Click **Add files** và tải lên file **tracks_list.json**.
        + Click **Upload**.

![Architect](/images/1/4.png?width=90pc)

