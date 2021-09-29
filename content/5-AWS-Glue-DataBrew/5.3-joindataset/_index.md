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

![Architect](/images/5/9.png?width=90pc)

2. Click **Connect new dataset**.

![Architect](/images/5/27.png?width=90pc)

3. Click **All AWS Glue table**, và click **analyticsworkshopdb**.
  + Click **reference_data**.
  + Dataset name - **reference-data-dataset**.

![Architect](/images/5/10.png?width=90pc)

4. Bạn sẽ thấy màn hình như bên dứoi, Click **Next**.

![Architect](/images/5/11.png?width=90pc)

5. Tại trang **Join**.
  + Chọn **track_id** từ **raw-dataset**.
  + Chọn **track_id** từ **reference-data-set**.
  + Bỏ chọn **track_id** từ **Table B**.
  + Click **Finish**.

![Architect](/images/5/12.png?width=90pc)

6. Bạn sẽ thấy kết quả như bên dưới.
  + Ở bên tay phải , mục **Recipe**, bạn sẽ thấy các bước transform mà bạn đã thực hiện, bao gồm đổi kiểu dữ liệu sang String và thực hiện **inner join** với **reference-data-dataset**.

![Architect](/images/5/13.png?width=90pc)
