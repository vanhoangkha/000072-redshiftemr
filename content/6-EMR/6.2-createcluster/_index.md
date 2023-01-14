+++
title = "Create EMR Cluster"
date = 2021
weight = 2
chapter = false
pre = "<b>6.2 </b>"
+++

#### Create EMR Cluster and run the uploaded script to S3

In this step, we will create EMR cluster and add Spark steps

1. Go to the [EMR admin interface](https://console.aws.amazon.com/elasticmapreduce/home?region=ap-southeast-1#).

  + Click **Create cluster**.

![Data Analysis on AWS](/images/6/7.png?featherlight=false&width=90pc)

2. Continue with **Create cluster - Quick options**.
  + Name the cluster: ```analytics-workshop-transformer```.
  + Select **Logging** option and provision the S3 folder:
    + ```s3://yourname-analytics-workshop-bucket/logs/```.
  + Change **Launch mode** to **Step execution**.
  + Under **Add steps** select **Spark application**.

![Data Analysis on AWS](/images/6/8.png?featherlight=false&width=90pc)

3. Click **Configure**.
    + In the pop-up window, leave **Spark-submit options** blank.
    + For the **Application location** section, select the location of the uploaded script - ```s3://yourname-analytics-workshop-bucket/scripts/emr_pyspark.py```.
    + Click **Select**.
    + Under **Arguments**, enter the name s3 bucket ```yourname-analytics-workshop-bucket```.
    + For the **Action on failure** section, select **Terminate cluster** .
    + Click **Add** to complete.

![Data Analysis on AWS](/images/6/9.png?featherlight=false&width=90pc)

4. In the **Software configuration** section.
  + Do not check the Use **AWS Glue Data Catalog for table metadata** option.
  + Release: **emr-x.x**.
  + Applications: Hadoop x.x.x, Spark x.x.x.
  + Version will be defaulted to the latest.

![Data Analysis on AWS](/images/6/10.png?featherlight=false&width=90pc)

5. In the **Hardware configuration** section.
  + Instance type: **m5.xlarge**.
  + Number of Instances: 3 (1 master and 2 core nodes).
  + Leave **Security and access** as default.

![Data Analysis on AWS](/images/6/10.png?featherlight=false&width=90pc)

  + Click **Create cluster**.