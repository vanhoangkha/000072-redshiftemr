+++
title = "Tạo QuickSight Visual"
date = 2021
weight = 3
chapter = false
pre = "<b>8.3 </b>"
+++


#### Sử dụng Amazon QuickSight để biểu diễn dữ liệu đã xử lí

**Visual 1: Biểu đồ Heatmap của users và track mà họ nghe**

Ở bước này, chúng ta tạo visual cho chúng ta biết được người dùng nào đang nghe các bản nhạc lặp đi lặp lại.

+ Ở góc dưới bên trái (Visual types):
  + Để chuột vào các icon để có thể thấy tên các loại visual có thể sử dụng.
  + Click chọn **Heat Map**.
+ Ở góc trên bên trái (Fields list).
  + Click **device_id**.
  + Click **track_name**.
+ Ở trên đầu biểu đồ bạn sẽ thấy **Field wells: Rows: device_id | Columns: track_name**.

![Architect](/images/8/7.png?width=90pc)

**Visual 2: Biểu đồ Tree Map của Nghệ Sĩ được nghe nhiều nhất**

Ở bước này, chúng ta sẽ tạo visual thể hiện nghệ sĩ nào được lắng nghe nhiều nhất.

+ Ở góc trên bên trái, Click **‘+ Add’ > Add Visual**. 
+ Ở góc dưới bên trái (Visual types):
  + Để chuột vào các icon để có thể thấy tên các loại visual có thể sử dụng.
  + Click **Tree Map**.
+ Ở góc trên bên trái (Fields list):
  + Click **artist_name**.

![Architect](/images/8/8.png?width=90pc)


Đến lúc này, bạn đã có thể lấy dữ liệu sử dụng Kinesis firehose, lưu dữ liệu ở S3, catalog table trong AWS Glue data catalog, chuyển đổi dữ liệu sử dụng Glue ETL/EMR và query và visual dữ liệu sử dụng Athena và QuickSight.

Bài lab này cung cấp cấu trúc end to end, từ source của dữ liệu đến business dashboard trong mô hình triển khai serverless analytics.

Hai phần tiếp theo sẽ giới thiệu Lambda và Redshift và những cải tiến cho kiến trúc này, để đáp ứng cho các nhu cầu nâng cao cho việc phân tích.