+++
title = "Tạo dữ liệu giả lập"
date = 2021
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Tạo dữ liệu giả lập

Ở bước này chúng ta sẽ cấu hình Kinesis Data Generator để tạo ra những dữ liệu giả lập và lấy chúng vào Kinesis Firehose

1. **Cấu hình Amazon Cognito** cho Kinesis Data Generator - Ở bước này chúng ta sẽ chạy 1 cloud formation stack mà sẽ cấu hình Cognito. Cloudformation scripts chạy ở region **N.Virgina**.
     + Đi đến [CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Kinesis-Data-Generator-Cognito-User&templateURL=https://aws-kdg-tools-us-east-1.s3.amazonaws.com/cognito-setup.json)
     + Click **Next**.

![Data Analysis on AWS](/images/1/9.png?featherlight=false&width=90pc)

2. Tại trang Specify stack details:
   - **Username**: **admin**.
   - **Password**: chọn một mật khẩu bao gồm chữ và số.
   - Click **Next**.

![Data Analysis on AWS](/images/1/10.png?featherlight=false&width=90pc)

3. Tại trang **Configure stack options**:
- Tuỳ chọn thêm Tags, e.g.:
  - workshop: **AnalyticsOnAWS**
  - Click **Next**


![Data Analysis on AWS](/images/1/11.png?featherlight=false&width=90pc)

4. Chọn **Next**

![Data Analysis on AWS](/images/1/11.1.png?featherlight=false&width=90pc)

5. Tại trang **Review**:
   - Kéo chuột xuống phía dưới.
   - Click chọn **I acknowledge that AWS CloudFormation might create IAM resources**.
   - Click **Create stack**.

![Data Analysis on AWS](/images/1/12.png?featherlight=false&width=90pc)

6. Đợi khoảng 20 phút, stack tạo thành công.

   - Refresh **AWS Cloudformation Console** của bạn. ( Ấn F5 trong trình duyệt )
   - Đợi đến khi **stack status** đổi thành **Create_Complete**.
   - Chọn **Kinesis-Data-Generator-Cognito-User stack.**
   - Đi đến outputs tab: Click vào đường link có tên: **KinesisDataGeneratorUrl** - Việc này sẽ mở Kinesis Data Generator tool của bạn.


![Data Analysis on AWS](/images/1/13.png?featherlight=false&width=90pc)

7. Ở trang chủ **Amazon Kinesis Data Generator**.
   - Đăng nhập với **username** và **password** từ bước trước.

![Data Analysis on AWS](/images/1/13.1.png?featherlight=false&width=90pc)

8.  Ở trang chủ **Amazon Kinesis Data Generator**.
    - Region: **ap-southeast-1**.
    - Stream/delivery stream: **analytics-workshop-stream**.
    - Records per second: **2000**.
    - Record template (Template 1): Trong khoảng trống nhập văn bản, thêm json template dưới đây vào và Click **Send Data**:

```
{
  "uuid": "{{random.uuid}}",
  "device_ts": "{{date.utc("YYYY-MM-DD HH:mm:ss.SSS")}}",
  "device_id": {{random.number(50)}},
  "device_temp": {{random.weightedArrayElement(
    {"weights":[0.30, 0.30, 0.20, 0.20],"data":[32, 34, 28, 40]}
  )}},
  "track_id": {{random.number(30)}},  
  "activity_type": {{random.weightedArrayElement(
        {
            "weights": [0.1, 0.2, 0.2, 0.3, 0.2],
            "data": ["\"Running\"", "\"Working\"", "\"Walking\"", "\"Traveling\"", "\"Sitting\""]
        }
    )}}
}
```

![Data Analysis on AWS](/images/1/14.png?featherlight=false&width=90pc)

9. Khi tool gửi ~100.000 tin nhắn, bạn có thể click - **Stop sending data to Kinesis**.

![Data Analysis on AWS](/images/1/14.1.png?featherlight=false&width=90pc)

10. Sau một lát bạn hãy đến S3 Console Click vào đây

    - Đi đến: **yourname-analytics-workshop-bucket** > **data**.
    - Trong này sẽ có 1 folder raw được tạo ra > Tiếp tục mở, bạn sẽ thấy firehose đẩy data vào S3 sử dụng **yyyy/mm/dd/hh**

![Data Analysis on AWS](/images/1/21.png?featherlight=false&width=90pc)


