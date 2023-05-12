---
title : "Tạo S3 bucket"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 1.1 </b> "
---

#### Tạo S3 bucket

1. Ở bước này, chúng ta sẽ đi đến console của S3 và tạo S3 bucket mà sẽ sử dụng xuyên suốt bài lab.

   - Đăng nhập vào **AWS Console**
   - Đi đến **S3 Console** và tạo **bucket** mới ở **Region ap-southeast-1**:
   - Truy cập đến giao diện quản trị **S3**
   - Click - **Create Bucket**.
   - Bucket Name: **```yourname-analytics-workshop-bucket```**.
   - Region : **Asia Pacific (Singapore)**.

![Data Analysis on AWS](/images/1/1.png?featherlight=false&width=90pc)

2. Giữ mặc định các thông số.

![Data Analysis on AWS](/images/1/1.1.png?featherlight=false&width=90pc)

3. Tuỳ chọn thêm Tags, e.g.:
   - workshop: **```AnalyticsOnAWS```**.
   - Click **Create Bucket**.

![Data Analysis on AWS](/images/1/1.2.png?featherlight=false&width=90pc)

4. Thêm dữ liệu **reference**.
   - Mở - **yourname-analytics-workshop-bucket**.
   - Click - **Create folder**.
   - Folder mới tên : **data**.
   - Click - **Save**.

![Data Analysis on AWS](/images/1/2.png?featherlight=false&width=90pc)

5. Mở folder **data**.
   - Click - **Create folder** (trong data folder).
   - Folder mới : **reference_data**.
   - Click - **Save**.

![Data Analysis on AWS](/images/1/3.png?featherlight=false&width=90pc)

6. Mở folder **reference_data**.
   - Tải file này xuống máy của bạn: tracks_list.json. [Github](https://github.com/AWS-First-Cloud-Journey/Workshop-72-Datasets)
   - Bạn cũng có thể tải file tracks_list.json ở phần tải về tại [đây](https://static.us-east-1.prod.workshops.aws/public/7072e03f-04ad-4825-87ca-0eab704a7e83/static/data/tracks_list.json)
   - Trong **S3 Console** - Click chọn **Upload**.
   - Click **Add files** và tải lên file **tracks_list.json**.
   - Click **Upload**.

![Data Analysis on AWS](/images/1/4.png?featherlight=false&width=90pc)



