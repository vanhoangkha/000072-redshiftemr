---
title : "Transform Data with AWS Glue DataBrew"
date: 2024-01-01
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Transform Data with AWS Glue DataBrew
AWS Glue DataBrew is a new visual data preparation tool that makes it easy for data analysts and data scientists to clean and normalize data in preparation for analytics and machine learning. You can choose from over 250 built-in transformations to automate data preparation tasks, without writing code. You can automate outlier filtering, convert data to standard format, fix invalid values, and other tasks. Once your data is ready, you can immediately use it for analytics and machine learning projects. You only pay for what you use - no upfront commitments.

In this lab, we will be doing an ETL process similar to "Data Transformation with AWS Glue" (interactive session) but this time we will be using AWS Glue DataBrew.

What are the learnings from this module?
Get hands-on with AWS Glue DataBrew, a visual data preparation tool that makes it easy for data analysts and data scientists to clean and normalize data in preparation for analytics and machine learning.

1. Go to the Glue Databrew Console. Select **Create project**

![Data Analytics on AWS](/images/7/0001.png?featherlight=false&width=90pc)

2. Enter the project name: AnalyticsOnAWS-GlueDataBrew as shown in the screenshot below.

- Under Select a dataset, select New dataset
- In New dataset details, enter raw-dataset in the Dataset name box as shown in the image below.

![Data Analytics on AWS](/images/7/0002.png?featherlight=false&width=90pc)

3. Under Connect to new dataset

- Select All AWS Glue tables, you will see all the databases in the AWS Glue Catalog as shown in the screenshot below.

![Data Analytics on AWS](/images/7/0003.png?featherlight=false&width=90pc)

4. Select analyticsworkshopdb. Select raw table

![Data Analytics on AWS](/images/7/0004.png?featherlight=false&width=90pc)

5. Under Permissions

- Select Role name as Create new IAM role
- Import AnalyticsOnAWS-GlueDataBrew into New IAM role suffix
- Click Create project

![Data Analytics on AWS](/images/7/0005.png?featherlight=false&width=90pc)

6. Once the Glue DataBrew session has been created, you will see as shown in the screenshot below:

![Data Analytics on AWS](/images/7/0006.png?featherlight=false&width=90pc)

7. Select the SCHEMA tab in the top right corner of the screen to explore the table's schema and its properties such as column names, data types, data quality, value distribution, and a box chart for the values. value.

![Data Analytics on AWS](/images/7/0007.png?featherlight=false&width=90pc)

8. Select the GRID tab to return to the grid view.

- We will change the track_id data type by selecting # in the track_id column, and select the string type as shown in the following screenshot.

![Data Analytics on AWS](/images/7/0008.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/7/0009.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/7/00010.png?featherlight=false&width=90pc)

11. Now, analyze the data to find out useful statistics such as correlations between attributes. Select the PROFILE tab in the top right corner of the screen, then Select Run data profile.

![Data Analytics on AWS](/images/7/00011.png?featherlight=false&width=90pc)

12. Keep the Job name and Job run sample as default options.

![Data Analytics on AWS](/images/7/00012.png?featherlight=false&width=90pc)

13. Specify the S3 location as your bucket name: s3://<your-bucket-name>-analytics-workshop-bucket/ to save the job results. Don't forget to replace the part in the S3 path. Leave the option Open Encrypted for the job result file unchecked.

- Under Permissions, select the Role name created
- Select **Create and run job**

![Data Analytics on AWS](/images/7/00013.png?featherlight=false&width=90pc)

14. You should get a result similar to the image shown below, that means Glue Databrew has started analyzing your data.

![Data Analytics on AWS](/images/7/00014.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/7/00015.png?featherlight=false&width=90pc)

15. Select the GRID tab to return to the grid view.

- Select Join.

![Data Analytics on AWS](/images/7/00016.png?featherlight=false&width=90pc)

16. Click Connect new dataset

![Data Analytics on AWS](/images/7/00017.png?featherlight=false&width=90pc)

17. Click All AWS Glue tables, and click analyticsworkshopdb

- Click reference_data

- Dataset name - reference-data-dataset

![Data Analytics on AWS](/images/7/00018.png?featherlight=false&width=90pc)

18. You should see a screen similar to the image below, Click Next.

![Data Analytics on AWS](/images/7/00019.png?featherlight=false&width=90pc)

19. Select track_id from raw-dataset

- Select track_id from reference-data-set

- Uncheck track_id from Table REMOVE

- Select Finish

![Data Analytics on AWS](/images/7/00020.png?featherlight=false&width=90pc)

20. You should see the results as shown in the screenshot below:

![Data Analytics on AWS](/images/7/00021.png?featherlight=false&width=90pc)

21. Select "PROFILE" to see the results of your original data analysis such as overview, blanks, duplicate rows, correlation, value distribution and column statistics. This will give you a closer look at your data.

![Data Analytics on AWS](/images/7/00022.png?featherlight=false&width=90pc)

22. Select LINEAGE in the top right corner.
You should be able to see the data lineage, represented graphically to provide an understanding of the data flow with the transformations involved at all steps from source to destination.

![Data Analytics on AWS](/images/7/00023.png?featherlight=false&width=90pc)

23. Go back to GRID view, and Select Create job.


![Data Analytics on AWS](/images/7/00024.png?featherlight=false&width=90pc)

24. Fill in the following values:
- Under Job details
- Job name: AnalyticsOnAWS-GlueDataBrew-Job
- Under Job output settings
- File type: GlueParquet
- S3 location: s3://<yourname>-analytics-workshop-bucket/data/processed-data/


![Data Analytics on AWS](/images/7/00025.png?featherlight=false&width=90pc)

25. Scroll down to the "Permission" section and select the role name you created in the first step, then Click on "Create and run job".

![Data Analytics on AWS](/images/7/00026.png?featherlight=false&width=90pc)

26. You should see a job in progress

![Data Analytics on AWS](/images/7/00027.png?featherlight=false&width=90pc)

27. Select "Jobs" on the left menu, you will see below screenshot, then Select Job name (link). Here, you can explore the job run history, job details and data flow like in the screenshot below:

![Data Analytics on AWS](/images/7/00028.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/7/00029.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/7/00030.png?featherlight=false&width=90pc)

28. This job should take about 4-5 minutes to complete, you should see Succeeded status and Select 1 result under Output column.

![Data Analytics on AWS](/images/7/00031.png?featherlight=false&width=90pc)