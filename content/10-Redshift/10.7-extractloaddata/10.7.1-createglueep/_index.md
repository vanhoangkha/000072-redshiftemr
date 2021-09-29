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
  + Development endpoints name: ```analyticsworkshopEndpoint2```.
  + IAM role: **AnalyticsworkshopGlueRole**.
  + Mở rộng **Security configuration.. parameters**.
    + Data processing unit (DPUs): ```2``` (Điều này sẽ giảm chi phí chạy lab).
  + Tuỳ chọn thêm tags:.
    + workshop: AnalyticsOnAWS.
  + Click **Next**.

![Architect](/images/10/18.png?width=90pc)

2. Tại trang **Networking**:
    + Chọn **Choose a connection**.
    + Chọn **analytics_workshop**.
    + Click **Next**.

![Architect](/images/10/19.png?width=90pc)

3. Tại trang **SSH public key**.
  + Thêm SSH public key (TUỳ chọn):
    + Để mặc định.
    + Click **Next**.

4. Tại trang **Review**
  + Xem lại các cấu hình.
  + Click **Finish**.

Việc này sẽ mất tầm 10 phút để một Glue development endpoint mới được tạo ra.

**Bạn cần phải đợi bước này hoàn thành trước khi qua bước tiếp theo**.
