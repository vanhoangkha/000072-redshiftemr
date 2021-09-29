+++
title = "Tạo Kinesis Firehose"
date = 2021
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++


#### Tạo Kinesis Firehose để thu thập dữ liệu và lưu vào S3 bucket.

Ở bước này chúng ta sẽ đi đến Kinesis Console và tạo 1 Kinesis Firehose deliver stream để lấy dữ liệu và lưu vào S3:

1. Đi đến: Kinesis Firehose Console click [Get Started](https://console.aws.amazon.com/kinesis/home?region=ap-southeast-1#/get-started).
+ Click **Create delivery stream**.
  + Tại mục : Name and source.
    + Delivery stream name : ```analytics-workshop-stream```.
    + Source : **Direct PUT or other sources**.
    + Click **Next**.

![Architect](/images/1/5.png?width=90pc)

2. Tại trang **Process records**.
    + Data transformation: Disabled.
    + Record format conversion: Disabled.
    + Click **Next**.

![Architect](/images/1/6.png?width=90pc)

3. Tại trang **Choose destination**.
    + Destination: **Amazon S3**.
    + S3 bucket: **yourname-analytics-workshop-bucket**.
    + Prefix: data/raw/.
    (Lưu ý: Dấu **/** đằng sau **raw** rất quan trọng. Nếu chúng ta không có nó Firehose sẽ sao chép dữ liệu vào nơi không mong muốn)
    + Error prefix: Để trống.
    + Click **Next**.

![Architect](/images/1/7.png?width=90pc)


4. Tại trang **Configure settings**.
    + S3 buffer conditions: Buffer size: **1** (MB).
    + S3 buffer conditions: Buffer interval: **60** (sec).
    + S3 compression: **Disabled**.
    + S3 encryption: **Disabled**.
    + Error logging: **Enabled**.
    + Tuỳ chọn thêm Tags, e.g.:
      + workshop: AnalyticsOnAWS
    + IAM role : Để mặc định **Create or update IAM role KinesisFirehoseServiceRole-xxxx**.
    + Click - **Next**.

![Architect](/images/1/8.png?width=90pc)


5. Tại trang **Review**.
    + Xem lại những cấu hình và chắc chắn rằng nó giống như được nêu ở trên.
    + Click - **Create delivery stream**.

