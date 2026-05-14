---
title : "Phân tích với Athena"
date: 2024-01-01
weight : 9
chapter : false
pre : " <b> 9. </b> "
---


#### Phân tích với Athena
Cho đến nay, chúng ta đã lưu trữ một số tập dữ liệu trong Amazon S3 và đánh chỉ mục chúng trong AWS Glue data catalog. Với Amazon Athena, chúng ta sẽ có thể khám phá dữ liệu bằng cách sử dụng các truy vấn SQL tiêu chuẩn.

Khám phá dữ liệu đã được chuyển đổi bằng cách sử dụng Athena
1. Trong bước này, chúng ta sẽ phân tích dữ liệu đã được chuyển đổi bằng cách sử dụng Amazon Athena.
- Đăng nhập vào Bảng điều khiển Amazon Athena.
- Nếu bạn nhìn thấy thông báo yêu cầu bạn tạo một bucket S3 trước để lưu kết quả của các truy vấn của bạn, làm theo các bước sau:
- Truy cập vào bảng điều khiển S3 và tạo một bucket bằng cách sử dụng tên ưu tiên của bạn, ví dụ: yourname-query-results
- Sau khi tạo bucket, quay lại bảng điều khiển Athena và Chọn  vào 'Settings' ở góc trên bên phải của bảng điều khiển.
- Nhập tên bucket bạn vừa tạo, đảm bảo bạn bao gồm một dấu gạch chéo cuối cùng: s3://yourname-query-results/
- Bấm Save
- Vì Athena sử dụng bộ sưu tập AWS Glue để theo dõi nguồn dữ liệu, bất kỳ bảng dựa trên S3 nào trong Glue đều có thể nhìn thấy được bởi Athena.
- Trên bảng điều khiển bên trái, chọn 'analyticsworkshopdb' từ danh sách thả xuống
- Chạy truy vấn sau đây:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count desc

```

![Data Analytics on AWS](/images/9/0001.png?featherlight=false&width=90pc)

2. Khám phá giao diện Athena và thử chạy một số truy vấn. Hãy thử truy vấn bảng emr_processed_data.
Truy vấn này trả về danh sách các bản nhạc được phát lại lặp lại bởi các thiết bị. Sau này, chúng ta sẽ thể hiện truy vấn này bằng cách sử dụng QuickSight.

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count desc

```

![Data Analytics on AWS](/images/9/0002.png?featherlight=false&width=90pc)

Bạn có thể chạy các truy vấn Athena tương tự và khám phá dữ liệu thêm.

Trong module Next, chúng ta sẽ thực hiện phân tích thời gian thực bằng cách sử dụng Amazon Kinesis Data Analytics.

