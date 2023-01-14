+++
title = "Chạy Jupyter Notebook"
date = 2021
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

#### Chạy Jupyter Notebook


1. Tải xuống và lưu file ở dưới máy của bạn: [analytics-workshop-notebook.ipynb](https://intro-to-analytics-on-aws.workshop.aws/notebooks/analytics-workshop-notebook.ipynb).
  + Bạn cũng có thể tải file notebook được đính kèm [tại đây](https://000072.awsstudygroup.com/download/analytics-workshop-notebook.ipynb).


2. Truy cập [giao diện quản trị Notebooks](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks)
  + Click **aws-glue-AnalyticsworkshopNotebook** và click **Open Jupyter**, Jupyter Notebook sẽ được tự động mở ở tab mới.

![Data Analysis on AWS](/images/3/00014.png?featherlight=false&width=90pc)

3. Click **Upload** (góc phải trên của màn hình)
  + Tìm và tải lên file **analytics-workshop-notebook.ipynb** đã tải xuống trước đó.
  + Click **Upload** để xác nhận tải lên.

![Data Analysis on AWS](/images/3/00015.png?featherlight=false&width=90pc)

4. Click  **analytics-workshop-notebook.ipynb** để mở notebook.

![Data Analysis on AWS](/images/3/00016.png?featherlight=false&width=90pc)

5. Hãy chắc rằng ‘Sparkmagic (PySpark)' được ghi ở góc phải của notebook; đây là tên của kernel Jupyter sẽ sử dụng để chạy các code block trong notebook.

6. Hãy đọc và làm theo hướng dẫn để hiểu rõ các khái niệm về Glue.

{{%notice tip%}}
Khi thực hiện các bước trong notebook, bạn cũng sẽ cần thay đôi 1 số thông tin ví dụ như tên S3 bucket của bạn.
{{%/notice%}}

![Data Analysis on AWS](/images/3/00017.png?featherlight=false&width=90pc)

7. Thực hiện chạy lệnh.

![Data Analysis on AWS](/images/3/00018.png?featherlight=false&width=90pc)

8. Tạo dynamic frame từ **Glue catalog**

![Data Analysis on AWS](/images/3/00019.png?featherlight=false&width=90pc)

9. Xem schema.

![Data Analysis on AWS](/images/3/00020.png?featherlight=false&width=90pc)

10. Xem số record

![Data Analysis on AWS](/images/3/00021.png?featherlight=false&width=90pc)

11. Xem chi tiết record từ **Dataframe**

![Data Analysis on AWS](/images/3/00022.png?featherlight=false&width=90pc)

12. Sử dụng **Spark SQL**

![Data Analysis on AWS](/images/3/00023.png?featherlight=false&width=90pc)

13. Thực hiện **Count** và **Filter**

![Data Analysis on AWS](/images/3/00024.png?featherlight=false&width=90pc)

14. Thực hiện **Glue Transforms**

![Data Analysis on AWS](/images/3/00025.png?featherlight=false&width=90pc)

15. Ghi vào **S3**

![Data Analysis on AWS](/images/3/00026.png?featherlight=false&width=90pc)

16. Sử dụng **boto3**

![Data Analysis on AWS](/images/3/00027.png?featherlight=false&width=90pc)

17. Kiểm tra table

![Data Analysis on AWS](/images/3/00028.png?featherlight=false&width=90pc)

18. Kiểm tra từ giao diện **S3**

![Data Analysis on AWS](/images/3/00029.png?featherlight=false&width=90pc)
