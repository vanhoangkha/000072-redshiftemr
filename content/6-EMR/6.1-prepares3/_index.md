+++
title = "Chuẩn bị thư mục và script"
date = 2021
weight = 1
chapter = false
pre = "<b>6.1 </b>"
+++

#### Chuẩn bị thư mục và script trên S3

1. Ở bước này, chúng ta sẽ đến S3 Console và tạo một số folder để sử dụng cho bước transform dữ liệu với EMR.

2. Truy cập tới [giao diện quản trị S3](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1).

3. Mở **yourname-analytics-workshop-bucket**.
    + Click : **Create folder**.
      + Tạo 1 folder mới tên ```scripts```.
      + Click **Save**.

![Architect](/images/6/1.png?width=90pc)

4. Mở **scripts**.
  + Tải xuống file: [emr_pyspark.py](https://intro-to-analytics-on-aws.workshop.aws/scripts/emr_pyspark.py)
  + Bạn có thể tải file script ở dưới đây.

{{%attachments style="orange" title="EMR scripts" pattern=".*(py)"/%}}

  + Trong S3 console, Click **Upload**:
  + Click **Add files** và tải lên file **emr_pyspark.py** vừa tải xuống
  + Click **Upload**

![Architect](/images/6/2.png?width=90pc)

5. Tạo folder cho EMR logs:
  + Mở **yourname-analytics-workshop-bucket**.
    + Click : **Create folder**.
      + Tạo 1 folder mới tên ```logs```.
      + Click **Save**.

![Architect](/images/6/3.png?width=90pc)
