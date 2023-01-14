+++
title = "Thu thập và Lưu trữ dữ liệu"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

---

Để bắt đầu, chúng ta sẽ tạo ra một số dữ liệu dummy near real-time với Kinesis data generator, và chuyển dữ liệu đó đến S3 với Kinesis Firehose delivery stream.

Chúng ta cũng sẽ copy 1 số dữ liệu reference vào trong Amazon S3 bucket.

![Data Analysis on AWS](/images/1/ingest.png?featherlight=false&width=60pc)

#### Nội dung

1. [Tạo S3 Bucket](1.1-creates3bucket/)
2. [Tạo Kinesis Firehose](1.2-createkinesis/)
3. [Tạo dữ liệu giả lập](1.3-generatedata/)

