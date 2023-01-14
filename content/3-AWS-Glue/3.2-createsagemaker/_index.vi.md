+++
title = "Tạo SageMaker Notebooks"
date = 2020
weight = 2
chapter = false
pre = "<b>3.2 </b>"
+++


#### Tạo SageMaker Notebooks (Jupyter) cho Glue Dev Endpoints


1. Truy cập đến [giao diện quản trị Glue devevelopment endpoin nodebooks](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks).
  + Chọn tab: **Sagemaker notebooks**.
  + Click - **Create notebook**.

![Data Analysis on AWS](/images/3/9.png?featherlight=false&width=90pc)


2. Notebook name: AnalyticsworkshopNotebook.
+ Attach to development endpoint: analyticsworkshopEndpoint1.
+ Chọn: Create an IAM role.
+ IAM Role: Workshop.
+ VPC (optional): Để Trống.

![Data Analysis on AWS](/images/3/10.png?featherlight=false&width=90pc)


3. Encryption key (optional): Để Trống.
+ Tuỳ chọn thêm Tags, e.g.:
+ workshop: AnalyticsOnAWS.
+ Click **Create Notebook**.

![Data Analysis on AWS](/images/3/11.png?featherlight=false&width=90pc)

4. Quá trình tạo SageMaker notebook sẽ tốn một ít phút (4 - 5 phút). 

![Data Analysis on AWS](/images/3/12.png?featherlight=false&width=90pc)

5. Đợi cho trạng thái của Notebook khởi tạo từ Starting thành Ready.

![Data Analysis on AWS](/images/3/13.png?featherlight=false&width=90pc)



