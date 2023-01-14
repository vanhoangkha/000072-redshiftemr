+++
title = "Create SageMaker Notebooks"
date = 2020
weight = 2
chapter = false
pre = "<b>3.2 </b>"
+++


#### Create SageMaker Notebooks (Jupyter) for Glue Dev Endpoints


1. Go to [Glue devevelopment endpoin nodebooks admin interface](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks).
  + Select tab: **Sagemaker notebooks**.
  + Click - **Create notebook**.

![Data Analysis on AWS](/images/3/9.png?featherlight=false&width=90pc)


2. Notebook name: AnalyticsworkshopNotebook.
+ Attach to development endpoint: analyticsworkshopEndpoint1.
+ Select: Create an IAM role.
+ IAM Role: Workshop.
+ VPC (optional): Leave blank.

![Data Analysis on AWS](/images/3/10.png?featherlight=false&width=90pc)


3. Encryption key (optional): Leave blank.
+ Optionally add Tags, e.g.:
+ workshop: AnalyticsOnAWS.
+ Click **Create Notebook**.

![Data Analysis on AWS](/images/3/11.png?featherlight=false&width=90pc)

4. Creating a SageMaker notebook will take a few minutes (4 - 5 minutes).

![Data Analysis on AWS](/images/3/12.png?featherlight=false&width=90pc)

5. Wait for the Notebook's state to initialize from Starting to Ready.

![Data Analysis on AWS](/images/3/13.png?featherlight=false&width=90pc)