+++
title = "Create Notebooks"
date = 2021
weight = 2
chapter = false
pre = "<b>10.7.2 </b>"
+++


#### Create SageMaker Notebooks (Jupyter) for Glue Dev Endpoints

1. Go to [Glue service Notebooks interface](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks).
  + Select tab **Sagemaker notebooks**
  + Click **Create notebook**.

![Data Analysis on AWS](/images/10/44.png?featherlight=false&width=90pc)

2. Notebook name: ```AnalyticsworkshopRedshiftNotebook```.
    + Attach to development endpoint: **analyticsworkshopEndpoint2**.

3. Select **Choose an existing role**.
    + IAM Role: **AnalyticsworkshopNotebookRole**.
    + VPC (optional): Leave blank.
![Data Analysis on AWS](/images/10/45.png?featherlight=false&width=90pc)

    + Encryption key (optional): Leave blank.
    + Optional extra Tags:
      + workshop: AnalyticsOnAWS.
  + Click: **Create Notebook**.

![Data Analysis on AWS](/images/10/46.png?featherlight=false&width=90pc)

Wait a few minutes for successful initialization, next we will run a notebook to load data into Redshift.