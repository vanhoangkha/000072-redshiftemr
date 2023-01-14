+++
title = "Create Kinesis Firehose"
date = 2021
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++


#### Create Kinesis Firehose to collect data and save to S3 bucket.

In this step we will go to Kinesis Console and create a Kinesis Firehose deliver stream to get the data and save it to S3:

1. Go to: Kinesis Firehose Console click [Get Started](https://console.aws.amazon.com/kinesis/home?region=ap-southeast-1#/get-started).
+ Click **Create delivery stream**.
  + In the section: Name and source.
    + Delivery stream name : ```analytics-workshop-stream```.
    + Source : **Direct PUT or other sources**.
    + Click **Next**.

![Data Analysis on AWS](/images/1/5.png?featherlight=false&width=90pc)

2. At the **Process records** page.
   - Data transformation: **Disabled**.
   - Record format conversion: **Disabled**.
   - Click **Next**.

![Data Analysis on AWS](/images/1/6.png?featherlight=false&width=90pc)

3. At the Choose destination page.
   - Destination: **Amazon S3**.
   - S3 bucket: **yourname-analytics-workshop-bucket**.
   - Prefix: **data/raw/**. (Note: The / after raw is very important. If we don't have it Firehose will copy the data to the wrong place)
   - Error prefix: **Leave blank**.
   - Click **Next**.

![Data Analysis on AWS](/images/1/7.png?featherlight=false&width=90pc)

4. At the Configure settings page.
   - S3 buffer conditions: **Buffer size: 1 (MB)**.
   - S3 buffer conditions: **Buffer interval: 60 (sec)**.
   - S3 compression: **Disabled**.
   - S3 encryption: **Disabled**.
   - Error logging: **Enabled**.
   - Optionally add Tags, e.g.:
     - workshop: **AnalyticsOnAWS**
     - **IAM role** : Leave default Create or update IAM role KinesisFirehoseServiceRole-xxxx.
   - Click - **Next**.

![Data Analysis on AWS](/images/1/8.png?featherlight=false&width=90pc)

5. At the **Review** page.
   - Review the configuration and make sure it is the same as stated above.
   - Click - **Create delivery stream**.

![Data Analysis on AWS](/images/1/8.1.png?featherlight=false&width=90pc)

6. Finish creating **Delivery streams**

![Data Analysis on AWS](/images/1/8.2.png?featherlight=false&width=90pc)