---
title : "Tạo Kinesis Firehose"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

#### Tạo Kinesis Firehose
Trong bước này, chúng ta sẽ điều hướng đến Kinesis Console và tạo một luồng dữ liệu Kinesis Firehose để tiếp nhận dữ liệu và lưu trữ trong S3:

1. Đi đến: **Kinesis Firehose Console** [Bấm vào đây](https://console.aws.amazon.com/firehose/home?region=us-east-1)
   - Bấm vào **Create delivery stream** (Tạo luồng dữ liệu)

![Data Analytics on AWS](/images/2/0001.png?featherlight=false&width=90pc)

2. Chọn source và destination
   - Source: **Direct PUT**
   - Destination: **Amazon S3**
   - Delivery stream name: **analytics-workshop-stream**

![Data Analytics on AWS](/images/2/0002.png?featherlight=false&width=90pc)

3. Chuyển đổi và biến đổi các bản ghi

    - Chuyển đổi các bản ghi nguồn bằng AWS Lambda: **Disabled** (Leave 'Enable data transformation' as unchecked)
    - Chuyển đổi định dạng bản ghi RecConvert: **Disabled** (Leave 'Enable record format conversion' as unchecked)
    - Destination settings
    - S3 bucket: **yourname-analytics-workshop-bucket**
    - Dynamic partitioning: **Not Enabled**
    - S3 bucket prefix: data/raw/ (Lưu ý: dấu gạch chéo / sau từ raw là quan trọng. Nếu bạn bỏ qua nó, Firehose sẽ sao chép dữ liệu vào một vị trí không mong muốn)
    - S3 bucket error output prefix: Để trống

![Data Analytics on AWS](/images/2/0003.png?featherlight=false&width=90pc)

4. Expand Buffer hints, compression and encryption
   - Buffer size: 1 MiB
   - Buffer interval: 60 seconds
   - Compression for data records: Not Enabled
   - Encryption for data records: Not Enabled

![Data Analytics on AWS](/images/2/0004.png?featherlight=false&width=90pc)

5. Advanced settings
   - Server-side encryption: unchecked
   - Amazon Cloudwatch error logging: Enabled
   - Permissions: Create or update IAM role KinesisFirehoseServiceRole-xxxx
   - Optionally add Tags, e.g.:
   - Key: workshop
   - Value: AnalyticsOnAWS

![Data Analytics on AWS](/images/2/0005.png?featherlight=false&width=90pc)

6. Review cấu hình và đảm bảo rằng nó như đã đề cập ở trên. Chọn **Create delivery stream**

![Data Analytics on AWS](/images/2/0006.png?featherlight=false&width=90pc)

7. Tạo delivery stream thành công.

![Data Analytics on AWS](/images/2/0007.png?featherlight=false&width=90pc)
