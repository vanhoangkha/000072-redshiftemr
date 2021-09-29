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
    + Notebook name: AnalyticsworkshopNotebook.
    + Attach to development endpoint: analyticsworkshopEndpoint1.
    + Chọn: Create an IAM role.
      + IAM Role: Workshop.
    + VPC (optional): Để Trống.
    + Encryption key (optional): Để Trống.
    + Tuỳ chọn thêm Tags, e.g.:
      + workshop: AnalyticsOnAWS.
    + Click **Create Notebook**.

![Architect](/images/3/7.png?width=90pc)

Quá trình tạo SageMaker notebook sẽ tốn một ít phút (4 - 5 phút). Đợi cho trạng thái của Notebook khởi tạo từ Starting thành Privisioned.
