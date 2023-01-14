+++
title = "Prepare directories and scripts"
date = 2021
weight = 1
chapter = false
pre = "<b>6.1 </b>"
+++

#### Prepare folders and scripts on S3

1. In this step, we will go to the S3 Console and create some folders to use for the data transform step with EMR.

2. Go to [S3 admin interface](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1).

3. Open **yourname-analytics-workshop-bucket**.

![Data Analysis on AWS](/images/6/1.png?featherlight=false&width=90pc)

4. Click: **Create folder**.
      + Create a new folder named ```scripts```.
      + Click **Save**.

![Data Analysis on AWS](/images/6/2.png?featherlight=false&width=90pc)

5. Open **scripts**.
  + Download file: [emr_pyspark.py](https://intro-to-analytics-on-aws.workshop.aws/scripts/emr_pyspark.py)
  + You can download the script file below.

{{%attachments style="orange" title="EMR scripts" pattern=".*(py)"/%}}

  + In S3 console, Click **Upload**:
  + Click **Add files** and upload the downloaded **emr_pyspark.py** file
  + Click **Upload**

![Data Analysis on AWS](/images/6/3.png?featherlight=false&width=90pc)

6. Upload successful.

![Data Analysis on AWS](/images/6/4.png?featherlight=false&width=90pc)

7. Create folder for EMR logs:
  + Open **yourname-analytics-workshop-bucket**.
    + Click: **Create folder**.
      + Create a new folder named ```logs```.
      + Click **Save**.

![Data Analysis on AWS](/images/6/5.png?featherlight=false&width=90pc)

8. Create success.

![Data Analysis on AWS](/images/6/6.png?featherlight=false&width=90pc)