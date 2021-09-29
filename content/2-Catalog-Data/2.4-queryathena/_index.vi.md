+++
title = "Query dữ liệu với Athena"
date = 2020
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++


#### Query dữ liệu sử dụng Amazon Athena

Giờ chúng ta sẽ query dữ liệu giả lập đã được catalog sử dụng Amazon Athena.

1. Truy cập [giao diện quản trị dịch vụ Athena](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query)
  + Nếu cần thiết, chọn **set up a query result location in Amazon S3** ở cảnh báo mua xanh gần phía trên Athena console.
    + Nhập ```s3://yourname-analytics-workshop-bucket/query_results/```.
    + Click **Save**.

![Architect](/images/2/11.png?width=90pc)

2. Ở bảng sổ xuống bên trái (**Database**), chọn **analyticsworkshopdb** > chọn table **raw**.
  + Click vào **3 dots** (3 chấm dọc) > chọn **Preview Table**.
  + Xem phần output.
  + ở query editor, dán nội dung query dưới đây và Click **Run Query**.

```
SELECT activity_type,
         count(activity_type)
FROM raw
GROUP BY  activity_type
ORDER BY  activity_type
```

![Architect](/images/2/13.png?width=90pc)

Chúc mừng bạn đã hoàn thành bước catalog dữ liệu, hãy tiếp tục với bước tiếp theo là chuyển đổi dữ liệu sử dụng AWS Glue ETL.

