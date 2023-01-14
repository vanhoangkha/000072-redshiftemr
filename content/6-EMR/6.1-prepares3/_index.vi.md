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

![Data Analysis on AWS](/images/6/1.png?featherlight=false&width=90pc)

4. Click : **Create folder**.
      + Tạo 1 folder mới tên ```scripts```.
      + Click **Save**.

![Data Analysis on AWS](/images/6/2.png?featherlight=false&width=90pc)

5. Mở **scripts**.
  + Tải xuống file: [emr_pyspark.py](https://intro-to-analytics-on-aws.workshop.aws/scripts/emr_pyspark.py)
  + Bạn có thể tải file script ở dưới đây.

{{%attachments style="orange" title="EMR scripts" pattern=".*(py)"/%}}

  + Trong S3 console, Click **Upload**:
  + Click **Add files** và tải lên file **emr_pyspark.py** vừa tải xuống
  + Click **Upload**

![Data Analysis on AWS](/images/6/3.png?featherlight=false&width=90pc)

6. Upload thành công.

![Data Analysis on AWS](/images/6/4.png?featherlight=false&width=90pc)

7. Tạo folder cho EMR logs:
  + Mở **yourname-analytics-workshop-bucket**.
    + Click : **Create folder**.
      + Tạo 1 folder mới tên ```logs```.
      + Click **Save**.

![Data Analysis on AWS](/images/6/5.png?featherlight=false&width=90pc)

8. Tạo thành công.

![Data Analysis on AWS](/images/6/6.png?featherlight=false&width=90pc)

