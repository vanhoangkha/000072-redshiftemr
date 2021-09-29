+++
title = "Tạo Notebooks"
date = 2021
weight = 2
chapter = false
pre = "<b>10.7.2 </b>"
+++


#### Tạo SageMaker Notebooks (Jupyter) cho Glue Dev Endpoints

1. Truy cập đến [giao diện Notebooks của dịch vụ Glue](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks).
  + Chọn tab **Sagemaker notebooks**.
  + Click **Create notebook**.
    + Notebook name: ```AnalyticsworkshopRedshiftNotebook```.
    + Attach to development endpoint: **analyticsworkshopEndpoint2**.
    + Chọn **Choose an existing role**.
    + IAM Role: **AnalyticsworkshopNotebookRole**.
    + VPC (optional): Để trống.
    + Encryption key (optional): Để trống.
    + Tuỳ chọn thêm Tags:
      + workshop: AnalyticsOnAWS.
  + Click: **Create Notebook**.

![Architect](/images/10/20.png?width=90pc)

Đợi vài phút để khởi tạo thành công, tiếp theo chúng ta sẽ chạy 1 notebook để tiến hành load dữ liệu vào Redshift.
