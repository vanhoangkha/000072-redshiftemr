+++
title = "Tạo Development Endpoint"
date = 2020
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++

#### Tạo Glue Development Endpoint

Ở bước này chúng ta sẽ tạo AWS Glue Dev Endpoint để phát triển các Glue ETL scripts sử dụng PySpark.


1. Truy cập [giao diện quản trị Glue Development Endpoint](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints)
+ Click - **Add endpoint**.

2. Tại trang **Set up your development endpoint**.
  + Development endpoint name: ```analyticsworkshopEndpoint1```
  + IAM role **AnalyticsworkshopGlueRole**
  + Mở rộng phần **Security configuration.. parameters**
    + Data processing units (DPUs): 2 (việc này sẽ làm giảm chi phí chạy bài lab)
  + Tuỳ chọn thêm Tags:
    + workshop: AnalyticsOnAWS
  + Click **Next**
![Architect](/images/3/1.png?width=90pc)

3. Tại trang **Networking**.
    + Click chọn **Skip networking information**.
    + Click **Next**.

![Architect](/images/3/2.png?width=90pc)

4. Tại trang **SSH public key**.
  + Để nguyên cấu hình mặc định.
  + Click **Next**.

5. Tại trang **Reviews**.
  + Kiểm tra lại cấu hình.
  + Click **Finish**

Việc này sẽ tốn vài phút (6 - 10 phút) để tạo 1 Glue Development Endpoint mới. Bạn sẽ thấy trạng thái chuyển từ PROVISIONING sang READY

Bạn phải đợi bước này thành công trước khi sang bước tiếp theo
