---
title : "Create S3 bucket"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 1.1 </b> "
---

#### Create S3 bucket

1. In this step, we will go to the S3 console and create an S3 bucket that we will use throughout the lab.

   - Login to **AWS Console**
   - Go to **S3 Console** and create new **bucket** in **Region ap-southeast-1**:
   - Access to admin interface **S3**
   - Click - **Create Bucket**.
   - Bucket Name: **```yourname-analytics-workshop-bucket```**.
   - Region : **Asia Pacific (Singapore)**.

![Data Analysis on AWS](/images/1/1.png?featherlight=false&width=90pc)

2. Keep the default parameters.

![Data Analysis on AWS](/images/1/1.1.png?featherlight=false&width=90pc)

3. Optionally add Tags, e.g.:
   - workshop: **```AnalyticsOnAWS```**.
   - Click **Create Bucket**.

![Data Analysis on AWS](/images/1/1.2.png?featherlight=false&width=90pc)

4. Add **reference** data.
   - Open - **yourname-analytics-workshop-bucket**.
   - Click - **Create folder**.
   - New folder name: **data**.
   - Click - **Save**.

![Data Analysis on AWS](/images/1/2.png?featherlight=false&width=90pc)

5. Open the **data** folder.
   - Click - **Create folder** (in data folder).
   - New folder: **reference_data**.
   - Click - **Save**.

![Data Analysis on AWS](/images/1/3.png?featherlight=false&width=90pc)

6. Open the **reference_data** folder.
   - Download this file to your computer: tracks_list.json
   - You can also download the tracks_list.json file from the download section here [https://static.us-east-1.prod.workshops.aws/public/97563182-1cb0-4843-b5be-caee2083e9e7/static /data/tracks_list.json)
   - In **S3 Console** - Click on **Upload**.
   - Click **Add files** and upload the file **tracks_list.json**.
   - Click **Upload**.

![Data Analysis on AWS](/images/1/4.png?featherlight=false&width=90pc)