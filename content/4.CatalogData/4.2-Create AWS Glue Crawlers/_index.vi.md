---
title : "Tạo AWS Glue Crawlers"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Tạo AWS Glue Crawlers

Trong bước này, chúng ta sẽ điều hướng đến AWS Glue Console và tạo các glue crawler để khám phá schema của dữ liệu mới được nhập vào trong S3.

1. Đi đến: Chọn  vào [đây](https://console.aws.amazon.com/glue/home?region=us-east-1)
- Trên bảng điều khiển bên trái, Chọn  vào Crawlers
- Chọn  vào Create crawler

![Data Analytics on AWS](/images/4/0007.png?featherlight=false&width=90pc)

2. Thông tin về crawler
- Tên crawler: AnalyticsworkshopCrawler
- Tùy chọn thêm các Tags (nhãn), ví dụ: workshop: AnalyticsOnAWS
- Chọn  Next

![Data Analytics on AWS](/images/4/0008.png?featherlight=false&width=90pc)

3. Chọn  Add a data source. Chọn một nguồn dữ liệu.


![Data Analytics on AWS](/images/4/0009.png?featherlight=false&width=90pc)

4. - Data source: S3

- Để mạng kết nối - tùy chọn như hiện tại
- Chọn In this account (trong tài khoản này) ở phần Location of S3 data (Vị trí dữ liệu S3)
- Bao gồm đường dẫn S3: s3://yourname-analytics-workshop-bucket/data/
- Để Subsequent crawler runs (Các lần chạy crawler sau) ở mặc định là Crawl all sub-folders (Crawl tất cả các thư mục con)
- Chọn  Add an S3 data source

![Data Analytics on AWS](/images/4/00010.png?featherlight=false&width=90pc)

5. Chọn nguồn dữ liệu S3 vừa thêm gần đây dưới Data Sources (Nguồn dữ liệu). Chọn  Next

![Data Analytics on AWS](/images/4/00011.png?featherlight=false&width=90pc)

6. IAM Role (role IAM)
- Dưới Existing IAM role (role IAM hiện có), chọn AnalyticsworkshopGlueRole
- Để tất cả mọi thứ khác như hiện tại.
- Chọn  Next

![Data Analytics on AWS](/images/4/00012.png?featherlight=false&width=90pc)

7. Cấu hình đầu ra:
Chọn  Add database để mở cửa sổ mới để tạo cơ sở dữ liệu.


![Data Analytics on AWS](/images/4/00013.png?featherlight=false&width=90pc)

8. Thông tin cơ sở dữ liệu
- Tên: analyticsworkshopdb
- Chọn  Create database

![Data Analytics on AWS](/images/4/00014.png?featherlight=false&width=90pc)

9. Đóng cửa sổ hiện tại và quay trở lại cửa sổ trước đó.



![Data Analytics on AWS](/images/4/00015.png?featherlight=false&width=90pc)

10. Làm mới bằng cách Chọn  vào biểu tượng làm mới bên phải của Target database (Cơ sở dữ liệu đích)
- Chọn analyticsworkshopdb dưới Target database (Cơ sở dữ liệu đích)
- Dưới Crawler schedule (Lịch crawler)
- Tần suất: On demand (Theo yêu cầu)
- Chọn  Next

![Data Analytics on AWS](/images/4/00016.png?featherlight=false&width=90pc)

11. Xem lại tất cả các cài đặt dưới Review and create (Xem và tạo). Chọn  Create crawler

![Data Analytics on AWS](/images/4/00017.png?featherlight=false&width=90pc)

12. Bạn sẽ thấy thông báo này: Crawler sau đây đã được tạo: "AnalyticsworkshopCrawler"


![Data Analytics on AWS](/images/4/00018.png?featherlight=false&width=90pc)

13. Chọn  Run crawler để chạy crawler lần đầu tiên


![Data Analytics on AWS](/images/4/00019.png?featherlight=false&width=90pc)

14. Đợi trong vài phút.

![Data Analytics on AWS](/images/4/00020.png?featherlight=false&width=90pc)
