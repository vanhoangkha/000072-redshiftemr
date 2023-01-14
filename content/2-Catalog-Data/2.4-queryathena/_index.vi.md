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

![Data Analysis on AWS](/images/2/00020.png?featherlight=false&width=90pc)

2. Chọn **Manage**

![Data Analysis on AWS](/images/2/00021.png?featherlight=false&width=90pc)

3. Chọn **Location of query result**. Chọn **Save**

![Data Analysis on AWS](/images/2/00022.png?featherlight=false&width=90pc)

4. Ở bảng sổ xuống bên trái (**Database**), chọn **analyticsworkshopdb** > chọn table **raw**.
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

![Data Analysis on AWS](/images/2/00023.png?featherlight=false&width=90pc)

Chúc mừng bạn đã hoàn thành bước catalog dữ liệu, hãy tiếp tục với bước tiếp theo là chuyển đổi dữ liệu sử dụng AWS Glue ETL.



