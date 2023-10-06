---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

#### Các bước chuẩn bị

#### Tạo S3 bucket 

Trong bước này, chúng ta sẽ điều hướng đến S3 Console và tạo một bucket S3 được sử dụng trong suốt workshop này.

1. Đi đến: S3 Console [Chọn  vào đây](https://s3.console.aws.amazon.com/s3/home?region=us-east-1)
- Chọn  vào - **Create Bucket**
- **Bucket Name**: yourname-analytics-workshop-bucket
- **Region**: US EAST (N. Virginia)

![Data Analytics on AWS](/images/1/0001.png?featherlight=false&width=90pc)

2. Để mặc định các phần còn lại.

![Data Analytics on AWS](/images/1/0002.png?featherlight=false&width=90pc)

3. Tùy chọn thêm Tags (Nhãn), ví dụ:workshop: AnalyticsOnAWS. Chọn  vào **Create bucket**

![Data Analytics on AWS](/images/1/0003.png?featherlight=false&width=90pc)

4. Mở - yourname-analytics-workshop-bucket (của bạn)
- Chọn  - **Create folder** 

![Data Analytics on AWS](/images/1/0004.png?featherlight=false&width=90pc)

5. Thư mục mới được gọi là: data. Chọn - **Create folder**

![Data Analytics on AWS](/images/1/0005.png?featherlight=false&width=90pc)

6. Tạo folder thành công.

![Data Analytics on AWS](/images/1/0006.png?featherlight=false&width=90pc)

7. Mở - data. Chọn - **Create folder** (Từ bên trong thư mục data)

![Data Analytics on AWS](/images/1/0007.png?featherlight=false&width=90pc)

8. Thư mục mới: reference_data. Chọn **Create folder**

- Mở - reference_data

![Data Analytics on AWS](/images/1/0008.png?featherlight=false&width=90pc)


9. Tải tệp này xuống máy: [tracks_list.json](https://static.us-east-1.prod.workshops.aws/public/9b2d1982-fdcf-4207-ba26-71a458796115/static/data/tracks_list.json) hoặc [Github](https://raw.githubusercontent.com/AWS-First-Cloud-Journey/000072-Data-Lab/master/tracks_list.json)
   - Trong Bảng điều khiển S3 - Chọn - **Uplaod**


![Data Analytics on AWS](/images/1/0009.png?featherlight=false&width=90pc)

10. Chọn  **Add files** & **upload** tracks_list.json 
   - Chọn **Upload** (góc dưới bên trái)

![Data Analytics on AWS](/images/1/00010.png?featherlight=false&width=90pc)

11. Tải file thành công.

![Data Analytics on AWS](/images/1/00011.png?featherlight=false&width=90pc)
