+++
title = "Initialize and run the job"
date = 2021
weight = 4
chapter = false
pre = "<b>5.4 </b>"
+++


#### Create and run an AWS Glue DataBrew job

1. Click **PROFILE** to review the profiling results of the raw dataset like summary, missing cells, duplicate rows, value distribution, and columns statistics, which will give you insights about your data.

![Data Analysis on AWS](/images/5/20.png?featherlight=false&width=90pc)

2. Click **LINEAGE** in the right corner.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)

3. You can see your data flow, presented to provide data flow with transition through all steps.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)

4. Go back to **GRID**, and Click **Create job**

![Data Analysis on AWS](/images/5/22.png?featherlight=false&width=90pc)

5. Fill in the values ​​below:
  + Section **Job details**.
    + Job Name: **AnalyticsOnAWS-GlueDataBrew-Job**.
  + Section **Job output settings**.
    + File type: **GlueParquet**.
    + S3 location: **s3://yourname-analytics-workshop-bucket/data/processed-data/**.


![Data Analysis on AWS](/images/5/23.png?featherlight=false&width=90pc)

6. Scroll down under **Permission**, and select the role name you created in the first step, and Click **Create and run job**.

![Data Analysis on AWS](/images/5/24.png?featherlight=false&width=90pc)

7. You will see a job in progress.

8. Click **Jobs** in the left menu, you will see the screen below.
  Click on the job name.

![Data Analysis on AWS](/images/5/26.png?featherlight=false&width=90pc)

9. Here you can view run history, job details, and data flow.
  + Running history.

![Data Analysis on AWS](/images/5/27.png?featherlight=false&width=90pc)
  + Details of the job.
  
![Data Analysis on AWS](/images/5/28.png?featherlight=false&width=90pc)

  + Data flow.

![Data Analysis on AWS](/images/5/21.png?featherlight=false&width=90pc)