+++
title = "Data profile với DataBrew"
date = 2020
weight = 2
chapter = false
pre = "<b>5.2 </b>"
+++


#### Data profile để kiểm tra chất lượng dữ liệu với DataBrew

1. Click **SCHEMA** tab ở phía góc trên bên phải của màn hình để xem table schema và những thuộc tính của nó như column name, data type, data quality, value distribution, và box plot distribution cho dữ liệu số.

![Data Analysis on AWS](/images/5/6.png?featherlight=false&width=90pc)

2. Click **GRID** tab để trở về chế độ hiển thị dạng lưới.

  + Chúng ta sẽ đổi kiểu dữ liệu của cột track_id , bằng cách Click **#** ở **track_id** column, và chọn kiểu **string** như màn hình dưới đây.

![Data Analysis on AWS](/images/5/7.png?featherlight=false&width=90pc)

3. Lập profile data để khám phá các thống kê thông tin về các mối tương quan giữa các thuộc tính.
  + Click **PROFILE** ở tab góc trên bên phải, và 

![Data Analysis on AWS](/images/5/8.png?featherlight=false&width=90pc)

4.  Click **Run data profile**.

![Data Analysis on AWS](/images/5/9.png?featherlight=false&width=90pc)

5. Để **Job name**, và **Job run sample** mặc định.
  + Chỉ đường dẫn đến S3 bucket với tên **s3://<yourname>-analytics-workshop-bucket/** cho output của job. 
  + Không chọn **Enable encryption for job output file**.

![Data Analysis on AWS](/images/5/10.png?featherlight=false&width=90pc)


6. Dưới **Permissions**, chọn role là **Role name** đã tạo lúc tạo Glue DataBrew project.
  + Click **Create and run job**.

![Architect](/images/5/11.png?width=90pc)

7. Bạn sẽ thấy **job đang in progress** nghĩa là Glue Databrew đã bắt đầu quá trình profile data của bạn.

![Data Analysis on AWS](/images/5/12.png?featherlight=false&width=90pc)