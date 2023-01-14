+++
title = "Tạo Redshift connection"
date = 2021
weight = 5
chapter = false
pre = "<b>10.5 </b>"
+++

#### Tạo Redshift connection thông qua Glue connection.

Ở bước này, chúng ta sẽ tạo một Redshift Connection thông qua Glue connection. Bạn sẽ sử dụng Redshift connection trong Development Endpoint để tạo ra  kết nối đến Redshift.

1. Truy cập đến [giao diện quản trị dịch vụ Glue](https://us-east-1.console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=connections).
  + Click **Add Connection**.

![Data Analysis on AWS](/images/10/23.png?featherlight=false&width=90pc)

2. Cho **Connection name** là ```analytics_workshop```.
    + Chọn **Connection type** là **Amazon Redshift**.
    + Click **Next**.

![Data Analysis on AWS](/images/10/24.png?featherlight=false&width=90pc)

3. Thiết lập kết nối vào data store:
    + Chọn **Cluster** là **redshift-cluster-1**.
    + Database name và Username sẽ được tự động tạo là dev và admin.
    + **Password**: Nhập password mà bạn cấp khi tạo Redshift cluster.
    + Click **Next**.
  

![Data Analysis on AWS](/images/10/25.png?featherlight=false&width=90pc)

4. Sau đó xem lại các thông tin chi tiết của kết nối và Click **Finish**.

![Data Analysis on AWS](/images/10/26.png?featherlight=false&width=90pc)

5. Chúng ta sẽ test kết nối này:
    + Chọn kết nối **analytics_workshop**.
    + Click **Test Connection**.

![Data Analysis on AWS](/images/10/27.png?featherlight=false&width=90pc)

6. Chọn Glue role tạo trong phần **Catalog dữ liệu** là **AnalyticsworkshopGlueRole**.
  + Click **Test Connection**.

![Data Analysis on AWS](/images/10/28.png?featherlight=false&width=90pc)

Việc này sẽ tốn một ít thời gian. Kết nối thành công sẽ hiện lên màn hình thông báo: **analytics_workshop connected successfully to your instance**.
Tiếp theo chúng ta sẽ tiến hành tạo schema và các tables trên Redshift.

