+++
title = "Tạo Glue Dev Endpoint"
date = 2021
weight = 1
chapter = false
pre = "<b>10.7.1 </b>"
+++

#### Tạo Glue Development Endpoint

Ở bước này, chúng ta sẽ tạo Glue Dev Endpoint để tương tác với Glue ETL script sử dụng PySpark.

1. Truy cập đến [giao diện Development Endpoints của dịch vụ Glue](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints).
  + Click **Add endpoint**.

![Data Analysis on AWS](/images/10/36.png?featherlight=false&width=90pc)

2. Development endpoints name: ```analyticsworkshopEndpoint2```.
  + IAM role: **AnalyticsworkshopGlueRole**.
  + Mở rộng **Security configuration.. parameters**.
    + Data processing unit (DPUs): ```2``` (Điều này sẽ giảm chi phí chạy lab).

![Data Analysis on AWS](/images/10/37.png?featherlight=false&width=90pc)

3. Tuỳ chọn thêm tags:.
    + workshop: AnalyticsOnAWS.
  + Click **Next**.

![Data Analysis on AWS](/images/10/38.png?featherlight=false&width=90pc)

4. Tại trang **Networking**:
    + Chọn **Choose a connection**.
    + Chọn **analytics_workshop**.
    + Click **Next**.

![Data Analysis on AWS](/images/10/39.png?featherlight=false&width=90pc)

5. Tại trang **SSH public key**.
  + Thêm SSH public key (TUỳ chọn):
    + Để mặc định.
    + Click **Next**.

![Data Analysis on AWS](/images/10/40.png?featherlight=false&width=90pc)

4. Tại trang **Review**
  + Xem lại các cấu hình.
  + Click **Finish**.

![Data Analysis on AWS](/images/10/41.png?featherlight=false&width=90pc)

5. Việc này sẽ mất tầm 10 phút để một Glue development endpoint mới được tạo ra.

![Data Analysis on AWS](/images/10/42.png?featherlight=false&width=90pc)

6. Hoàn thành tạo Glue development endpoint.

![Data Analysis on AWS](/images/10/43.png?featherlight=false&width=90pc)

**Bạn cần phải đợi bước này hoàn thành trước khi qua bước tiếp theo**.
