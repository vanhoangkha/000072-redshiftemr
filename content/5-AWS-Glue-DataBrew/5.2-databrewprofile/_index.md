+++
title = "Data profile with DataBrew"
date = 2020
weight = 2
chapter = false
pre = "<b>5.2 </b>"
+++


#### Data profile to check data quality with DataBrew

1. Click the **SCHEMA** tab in the upper right corner of the screen to view the table schema and its properties such as column name, data type, data quality, value distribution, and box plot distribution for numerical data.

![Data Analysis on AWS](/images/5/6.png?featherlight=false&width=90pc)

2. Click **GRID** tab to return to grid view.

  + We will change the data type of the track_id column, by Clicking **#** in the **track_id** column, and select the type **string** as shown below.

![Data Analysis on AWS](/images/5/7.png?featherlight=false&width=90pc)

3. Profile data to discover statistical information about correlations between attributes.
  + Click **PROFILE** in the upper right corner tab, and

![Data Analysis on AWS](/images/5/8.png?featherlight=false&width=90pc)

4. Click **Run data profile**.

![Data Analysis on AWS](/images/5/9.png?featherlight=false&width=90pc)

5. Leave **Job name**, and **Job run sample** default.
  + Specify the path to the S3 bucket with the name **s3://<yourname>-analytics-workshop-bucket/** for the output of the job.
  + Do not select **Enable encryption for job output file**.

![Data Analysis on AWS](/images/5/10.png?featherlight=false&width=90pc)


6. Under **Permissions**, select the role **Role name** created when creating the Glue DataBrew project.
  + Click **Create and run job**.

![Architect](/images/5/11.png?width=90pc)

7. You will see **job in progress** which means Glue Databrew has started your profile data process.

![Data Analysis on AWS](/images/5/12.png?featherlight=false&width=90pc)