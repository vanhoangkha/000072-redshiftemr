+++
title = "Configure transform"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++

#### Configure transform

1. Click on any of the S3 nodes in the 2 nodes
+ Click **Transform** and select **Join**

![Data Analysis on AWS](/images/4/5.png?featherlight=false&width=90pc)

2. Click **Transform - Join** node and select **Node properties** in the right configuration window, select the drop-down list and select all S3 data sources as shown below screen:

![Data Analysis on AWS](/images/4/6.png?featherlight=false&width=90pc)

3. Switch to **Transform** tab.
  + Click **Add condition**.
  + Select **track_id** column as the column will join as shown below.

![Data Analysis on AWS](/images/4/8.png?featherlight=false&width=90pc)

4. With **Join** node selected, Click **Transform** and select **ApplyMapping**.

![Data Analysis on AWS](/images/4/9.png?featherlight=false&width=90pc)

5. We will remove the unused columns and map the new data type to the following column:
  + drop Columns
    + .track_id
    + parition_0
    + parition_1
    + parition_2
    + parition_3
  + Map New Data Type
    + track_id **string**
  + Your selection should look like the image below


![Data Analysis on AWS](/images/4/10.png?featherlight=false&width=90pc)

6. Click **Transform - ApplyMapping** node on the screen.
  + Then Click **Target** and select **S3** as shown below.

![Data Analysis on AWS](/images/4/13.png?featherlight=false&width=90pc)

6. Click **Transform - ApplyMapping** node on the screen.
  + Then Click **Target** and select **S3** as shown below.

![Data Analysis on AWS](/images/4/13.png?featherlight=false&width=90pc)

7. In the **Data target properties - S3** tab, provide the following values:
  + Format: **Glue Parquet**.
  + Compression Type: **Snappy**.
  + S3 Target Location: **s3://yourname-analytics-workshop-bucket/data/processed-data2/**.
  + Data Catalog update options
    + Select **Create a table in the Data Catalog and on subsequent runs, update the schema and add new partitions**.
  + Database: **analyticsworkshopdb**.
  + Table name: **processed-data2**.


![Data Analysis on AWS](/images/4/00015.png?featherlight=false&width=90pc)

7. Click **Job details** and configure as below.
  + Name: **AnalyticsOnAWS-GlueStudio**.
  + IAM Role: **AnalyticsWorkshopGlueRole**.
  + Number of workers: **2**.
  + Job bookmark: **Disable**.
  + Number of retries: **1**.
  + Job timeout (minutes): **10**.
  + The remaining values ​​are left to default.
  + Click **Save**.

![Data Analysis on AWS](/images/4/16.png?featherlight=false&width=90pc)

8. Click **Save** and you should see **“Successfully created job”**.

![Data Analysis on AWS](/images/4/17.png?featherlight=false&width=90pc)