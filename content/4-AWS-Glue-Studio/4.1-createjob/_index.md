+++
title = "Create Glue Studio job"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1 </b>"
+++

#### Create Glue Studio job

1. Go to the [Glue Studio Console] interface(https://console.aws.amazon.com/gluestudio/home?region=ap-southeast-1)
  + Click - icon **3 tiles** in the left corner.

2. Click - **Jobs** and select **Create job from a blank graph**.
  + Click **Create**.

![Data Analysis on AWS](/images/4/1.png?featherlight=false&width=90pc)

3. Click - **Source** and select **S3**

4. Click the **Data source properties - S3** tab in the configuration window on the right side of the screen.
+ Under **S3 source type** select **Data Catalog table**.
+ Select the values ​​as below.
  + Database - **analyticsworkshopdb**.
  + Table - **raw**.

![Data Analysis on AWS](/images/4/2.png?featherlight=false&width=90pc)

5. Continue to do the same step to add reference_data from S3. Click - **Source** and select **S3**.

![Data Analysis on AWS](/images/4/3.png?featherlight=false&width=90pc)

6. Click the **Data source properties - S3** tab in the configuration window on the right side of the screen.
+ Under **S3 source type** select **Data Catalog table**.
+ Select the values ​​as below.
  + Database - **analyticsworkshopdb**.
  + Table - **reference_data**.

![Data Analysis on AWS](/images/4/4.png?featherlight=false&width=90pc)