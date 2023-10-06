---
title : "Hiển thị dữ liệu trong Quicksight"
date :  "`r Sys.Date()`" 
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

#### Hiển thị dữ liệu trong Quicksight

Trong module này, chúng ta sẽ sử dụng Amazon Quicksight để xây dựng một số biểu đồ trực quan dựa trên dữ liệu đã được thu thập và lưu trữ trên S3.

Hãy thoải mái khám phá các tùy chọn trực quan hóa khác nhau có sẵn trong Quicksight!

#### Thiết lập QuickSight

1. Trong bước này, chúng ta sẽ trực quan hóa dữ liệu đã được xử lý bằng cách sử dụng QuickSight.

- Truy cập: Bảng điều khiển QuickSight
- Chọn  vào Sign up for QuickSight


![Data Analytics on AWS](/images/10/0001.png?featherlight=false&width=90pc)

2. Đảm bảo chọn Enterprise và Chọn  vào Continue


![Data Analytics on AWS](/images/10/0002.png?featherlight=false&width=90pc)

3. Tên tài khoản QuickSight: yournameanalyticsworkshop


![Data Analytics on AWS](/images/10/0003.png?featherlight=false&width=90pc)


4. Địa chỉ email thông báo: you@youremail.com
Chọn Amazon Athena - điều này cho phép QuickSight truy cập vào cơ sở dữ liệu Amazon Athena


![Data Analytics on AWS](/images/10/0004.png?featherlight=false&width=90pc)

5. Chọn Amazon S3
Chọn yourname-analytics-workshop-bucket
Chọn  vào Finish


![Data Analytics on AWS](/images/10/0005.png?featherlight=false&width=90pc)

6. Chọn  vào Finish
Chờ đợi tài khoản QuickSight của bạn được tạo

![Data Analytics on AWS](/images/10/0006.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/10/0007.png?featherlight=false&width=90pc)

7. Thêm một New Dataset


![Data Analytics on AWS](/images/10/0008.png?featherlight=false&width=90pc)

8. Truy cập: 
- Ở phía trên bên phải, Chọn  vào New Dataset
- Chọn  vào Athena
- New Athena data source
- Data source name: analyticsworkshop



![Data Analytics on AWS](/images/10/0009.png?featherlight=false&width=90pc)

9. Chọn  vào Validate connection
- Điều này sẽ kiểm tra xem QuickSight của bạn có thể truy cập Athena hay không
- Chọn  vào Create data source

![Data Analytics on AWS](/images/10/00010.png?featherlight=false&width=90pc)

10. Chọn bảng của bạn:
- Database: chứa các bộ bảng - chọn analyticsworkshopdb
- Tables:  chứa dữ liệu bạn có thể trực quan hóa - chọn processed_data
- Chọn  vào Select

![Data Analytics on AWS](/images/10/00011.png?featherlight=false&width=90pc)

11. Hoàn thành việc data set creation:
- Chọn Directly query your data
- Chọn  vào Visualize

![Data Analytics on AWS](/images/10/00012.png?featherlight=false&width=90pc)

12. Sử dụng Amazon Quick Sight để Visualize Our Processed Data
Trực quan hóa 1: Heat map  của người dùng và các bài hát mà họ đang nghe


![Data Analytics on AWS](/images/10/00013.png?featherlight=false&width=90pc)

13. Trong bước này, chúng ta sẽ tạo một trực quan hóa để xem người dùng nào đang nghe các bài hát lặp đi lặp lại.

- Trên bảng điều khiển phía dưới bên trái ((Visual types):
- Di chuột lên các biểu tượng để xem tên của các trực quan hóa có sẵn
- Chọn  vào Heat Map
- Trên bảng điều khiển phía trên bên trái (Fields list)
- Chọn  vào device_id
- Chọn  vào track_name
- Ngay phía trên trực quan hóa, bạn sẽ thấy Field wells: Rows: device_id | Columns: track_name
- Nếu bạn di chuột lên các vùng màu xanh đậm trên bản đồ nhiệt, bạn sẽ thấy rằng những người dùng cụ thể đó đang nghe cùng một bài hát nhiều lần.

![Data Analytics on AWS](/images/10/00014.png?featherlight=false&width=90pc)

#### Hình minh họa 2: Tree map  về các nghệ sĩ được phát nhiều nhất
14. Trong bước này, chúng ta sẽ tạo một hình minh họa hiển thị các nghệ sĩ được phát nhiều nhất.

- Ở góc trên bên trái, Chọn  vào '+  Add' > Add Visual. Điều này sẽ thêm một bảng điều khiển mới vào bảng bên phải.
- Ở bảng dưới bên trái (Visual types):
- Di chuột lên các biểu tượng để xem tên của các hình minh họa
- Chọn  vào Tree Map
- Ở bảng trên bên trái (Fields list):
- Chọn  vào artist_name
- Thử nghiệm và khám phá Bảng điều khiển Amazon QuickSight. Bạn có thể thử các bộ lọc, các loại hình minh họa khác, v.v.
- Cho đến nay, chúng ta đã thể hiện dữ liệu bằng cách sử dụng Kinesis firehose, lưu trữ dữ liệu trong S3, đăng ký các bảng trong AWS Glue data catalog, biến đổi dữ liệu bằng cách sử dụng Glue ETL/EMR và truy vấn và hiển thị dữ liệu bằng cách sử dụng Athena và Quicksight.
- Điều này cung cấp một kiến trúc end-to-end, từ nguồn đến bảng điều khiển doanh nghiệp, trong một mô hình triển khai phân tích serverless.
- Hai module Next giới thiệu Lambda và Redshift và bao gồm các cải tiến Next cho kiến trúc này, để đáp ứng các yêu cầu bổ sung khác nhau để cung cấp dữ liệu theo yêu cầu cho phân tích.

![Data Analytics on AWS](/images/10/00015.png?featherlight=false&width=90pc)


