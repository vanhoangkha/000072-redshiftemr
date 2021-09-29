+++
title = "Chạy lại Glue Crawler"
date = 2021
weight = 5
chapter = false
pre = "<b>6.5 </b>"
+++

#### Chạy lại Glue Crawler

1. Truy cập đến [giao diện quản trị của dịch vụ AWS Glue](https://console.aws.amazon.com/glue/home?region=ap-southeast-1)
  + Ở khung bên trái, click **Crawlers**.
  + Chọn crawler đã được tạo ở phần trước: **AnalyticsworkshopCrawler**.
  + Click **Run Crawler**.

![Architect](/images/6/9.png?width=90pc)

2. Bạn sẽ thấy trạng thái đổi thành **Starting**.
  + Đợi 1 vài phút để crawler chạy hoàn tất.
  + Crawler sẽ hiển thị **Tables added** là 1.

3. Bạn có thể đi đến phần databases ở bên trái và xác nhận là table **emr_processed_data** đã được thêm vào.

![Architect](/images/6/10.png?width=90pc)

Chúc mừng bạn đã hoàn tất việc transform dữ liệu bằng EMR, chúng ta đã sẵn sàng để thực hiện truy vấn dữ liệu bằng Amazon Athena ở bước tiếp theo.

