---
title : "Generate Dummy Data"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Generate Dummy Data 



Trong bước này, chúng ta sẽ cấu hình Kinesis Data Generator để tạo ra dữ liệu giả và đưa nó vào Kinesis Firehose.

Cấu hình Amazon Cognito cho Kinesis Data Generator - Trong bước này, chúng ta sẽ khởi chạy một stack cloud formation để cấu hình Cognito. Những tệp script cloudformation này sẽ được khởi chạy trong khu vực N.Virginia (Không cần thay đổi khu vực này).

1. Đi tới [CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Kinesis-Data-Generator-Cognito-User&templateURL=https://aws-kdg-tools-us-east-1.s3.amazonaws.com/cognito-setup.json)

   - Click Next

![Data Analytics on AWS](/images/3/0001.png?featherlight=false&width=90pc)

2. Chỉ định các chi tiết:
   - Username: admin
   - Password: chọn một mật khẩu bao gồm chữ và số
   - Chọn  vào **Next**

![Data Analytics on AWS](/images/3/0002.png?featherlight=false&width=90pc)

3. Các tùy chọn:
   - Tùy chọn thêm Tags (nhãn) nếu muốn, ví dụ: workshop: AnalyticsOnAWS
   - Chọn  vào **Next**

![Data Analytics on AWS](/images/3/0003.png?featherlight=false&width=90pc)

4. I acknowledge that AWS CloudFormation might create IAM resources: chọn
- Click Create stack

![Data Analytics on AWS](/images/3/0004.png?featherlight=false&width=90pc)

5. Làm mới bảng điều khiển AWS CloudFormation của bạn


![Data Analytics on AWS](/images/3/0005.png?featherlight=false&width=90pc)

6. Chờ đến khi trạng thái của stack thay đổi thành Create_Complete


![Data Analytics on AWS](/images/3/0006.png?featherlight=false&width=90pc)

7. Chọn stack Kinesis-Data-Generator-Cognito-User
Chuyển đến tab outputs: Chọn  vào liên kết có tên là: KinesisDataGeneratorUrl - Điều này sẽ mở công cụ Kinesis Data Generator của bạn.

![Data Analytics on AWS](/images/3/0007.png?featherlight=false&width=90pc)

8. Trên trang chủ Amazon Kinesis Data Generator

Đăng nhập bằng tên người dùng và mật khẩu từ bước trước đó
Region: us-east-1
Stream/delivery stream: analytics-workshop-stream
Records per second: 2000
Mẫu bản ghi (Mẫu 1): Trong khu vực văn bản lớn, chèn mẫu json sau đây:

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

![Data Analytics on AWS](/images/3/0008.png?featherlight=false&width=90pc)

9. Click - Send Data. Khi công cụ đã gửi khoảng ~10.000 tin nhắn, bạn có thể Chọn  vào - Stop sending data to Kinesis.

![Data Analytics on AWS](/images/3/0009.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/3/00010.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/3/00011.png?featherlight=false&width=90pc)

10.  Xác minh rằng dữ liệu đã được gửi đến S3
- Sau một vài khoảng thời gian, hãy truy cập vào bảng điều khiển S3 
- Chuyển đến: yourname-analytics-workshop-bucket > data
- Nên có một thư mục có tên là "raw" > Mở nó và tiếp tục điều hướng, bạn sẽ nhận thấy rằng firehose đã đổ dữ liệu vào S3 bằng cách sử dụng phân vùng theo định dạng yyyy/mm/dd/hh
- Nếu bạn đã nhận được dữ liệu giả trong các S3 bucket của mình, chúng ta có thể tiếp tục sang bước Next!

![Data Analytics on AWS](/images/3/00012.png?featherlight=false&width=90pc)
