+++
title = "Join dataset"
date = 2020
weight = 3
chapter = false
pre = "<b>5.3 </b>"
+++


#### Join dataset trong DataBrew

1.  Click **GRID** tab để trở về chế độ hiển thị dạng lưới.
  + Click **JOIN**.


![Data Analysis on AWS](/images/5/13.png?featherlight=false&width=90pc)


2. Click **Connect new dataset**.

![Data Analysis on AWS](/images/5/14.png?featherlight=false&width=90pc)

3. Click **All AWS Glue table**, và click **analyticsworkshopdb**.


![Data Analysis on AWS](/images/5/15.png?featherlight=false&width=90pc)


4.  Click **reference_data**.
  + Dataset name - **reference-data-dataset**.

![Data Analysis on AWS](/images/5/16.png?featherlight=false&width=90pc)

5. Tại trang **Join**.
  + Chọn **track_id** từ **raw-dataset**.
  + Chọn **track_id** từ **reference-data-set**.
  + Bỏ chọn **track_id** từ **Table B**.
  + Click **Finish**.

![Data Analysis on AWS](/images/5/18.png?featherlight=false&width=90pc)

6. Bạn sẽ thấy kết quả như bên dưới.
  + Ở bên tay phải , mục **Recipe**, bạn sẽ thấy các bước transform mà bạn đã thực hiện, bao gồm đổi kiểu dữ liệu sang String và thực hiện **inner join** với **reference-data-dataset**.

![Data Analysis on AWS](/images/5/19.png?featherlight=false&width=90pc)

