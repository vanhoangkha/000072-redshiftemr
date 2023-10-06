---
title : "Generate Dummy Data"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Generate Dummy Data


In this step, we will configure the Kinesis Data Generator to generate dummy data and feed it to Kinesis Firehose.

Configure Amazon Cognito for Kinesis Data Generator - In this step, we will launch a stack cloud formation to configure Cognito. These cloudformation script files will be launched in the N.Virginia region (No need to change this region).

1. Go to [CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Kinesis-Data-Generator-Cognito-User&templateURL=https://aws-kdg-tools-us-east-1.s3.amazonaws.com/cognito-setup.json)

   - Click Next

![Data Analytics on AWS](/images/3/0001.png?featherlight=false&width=90pc)

2. Specify the details:
   - Username: admin
   - Password: choose a password consisting of letters and numbers
   - Click on **Next**

![Data Analytics on AWS](/images/3/0002.png?featherlight=false&width=90pc)

3. Options:
   - Option to add Tags (labels) if desired, for example: workshop: AnalyticsOnAWS
   - Click on **Next**

![Data Analytics on AWS](/images/3/0003.png?featherlight=false&width=90pc)

4. I acknowledge that AWS CloudFormation might create IAM resources: choose
- Click Create stack

![Data Analytics on AWS](/images/3/0004.png?featherlight=false&width=90pc)

5. Refresh your AWS CloudFormation console


![Data Analytics on AWS](/images/3/0005.png?featherlight=false&width=90pc)

6. Wait until the status of the stack changes to Create_Complete


![Data Analytics on AWS](/images/3/0006.png?featherlight=false&width=90pc)

7. Select Kinesis-Data-Generator-Cognito-User stack
Go to the outputs tab: Click on the link called: KinesisDataGeneratorUrl - This will open your Kinesis Data Generator tool.

![Data Analytics on AWS](/images/3/0007.png?featherlight=false&width=90pc)


8. On the Amazon Kinesis Data Generator homepage

Log in with the username and password from the previous step
Region: us-east-1
Stream/delivery stream: analytics-workshop-stream
Records per second: 2000
Record Template (Sample 1): In the large text area, insert the following json template:

```
{
    "uuid": "{{random.uuid}}",
    "device_ts": "{{date.utc("YYYY-MM-DD HH:mm:ss.SSS")}}",
    "device_id": {{random.number(50)}},
    "device_temp": {{random.weightedArrayElement(
    {"weights":[0.30, 0.30, 0.20, 0.20],"data":[32, 34, 28, 40]}
    )}},
    "track_id": {{random.number(30)}},
    "activity_type": {{random.weightedArrayElement(
        {
            "weights": [0.1, 0.2, 0.2, 0.3, 0.2],
            "data": ["\"Running\"", "\"Working\"", "\"Walking\"", "\"Traveling\"", "\"Sitting\""]
        }
    )}}
}

```

![Data Analytics on AWS](/images/3/0008.png?featherlight=false&width=90pc)

9. Click - Send Data. Once the tool has sent about ~10,000 messages, you can Select - Stop sending data to Kinesis.

![Data Analytics on AWS](/images/3/0009.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/3/00010.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/3/00011.png?featherlight=false&width=90pc)

10. Verify that data has been sent to S3
- After some time, go to the S3 . console
- Go to: yourname-analytics-workshop-bucket > data
- There should be a folder called "raw" > Open it and keep navigating, you will notice that firehose dumped the data into S3 using the partition in the format yyyy/mm/dd/hh
- If you have received dummy data in your S3 buckets, we can continue to the Next step!

![Data Analytics on AWS](/images/3/00012.png?featherlight=false&width=90pc)