+++
title = "Generate Dummy Data"
date = 2021
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Generate emulator data

In this step we will configure Kinesis Data Generator to generate simulation data and get them into Kinesis Firehose.

1. **Configuring Amazon Cognito** for Kinesis Data Generator - In this step we will run a cloud formation stack that will configure Cognito. Cloudformation scripts run in region **N.Virgina**.
     + Go to [CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Kinesis-Data-Generator-Cognito-User&templateURL=https: //aws-kdg-tools-us-east-1.s3.amazonaws.com/cognito-setup.json)
     + Click **Next**.

![Data Analysis on AWS](/images/1/9.png?featherlight=false&width=90pc)

2. On the Specify stack details page:
   - **Username**: **admin**.
   - **Password**: choose a password consisting of letters and numbers.
   - Click **Next**.

![Data Analysis on AWS](/images/1/10.png?featherlight=false&width=90pc)

3. At the **Configure stack options** page:
- Optionally add Tags, e.g.:
  - workshop: **AnalyticsOnAWS**
  - Click **Next**


![Data Analysis on AWS](/images/1/11.png?featherlight=false&width=90pc)

4. Select **Next**

![Data Analysis on AWS](/images/1/11.1.png?featherlight=false&width=90pc)

5. At **Review** page:
   - Drag the mouse to the bottom.
   - Click **I acknowledge that AWS CloudFormation might create IAM resources**.
   - Click **Create stack**.

![Data Analysis on AWS](/images/1/12.png?featherlight=false&width=90pc)

6. Wait about 20 minutes, stack created successfully.

   - Refresh your **AWS Cloudformation Console**. (Press F5 in the browser)
   - Wait until **stack status** changes to **Create_Complete**.
   - Select **Kinesis-Data-Generator-Cognito-User stack.**
   - Go to the outputs tab: Click on the link named: **KinesisDataGeneratorUrl** - This will open your Kinesis Data Generator tool.


![Data Analysis on AWS](/images/1/13.png?featherlight=false&width=90pc)

7. At the **Amazon Kinesis Data Generator** homepage.
   - Login with **username** and **password** from previous step.

![Data Analysis on AWS](/images/1/13.1.png?featherlight=false&width=90pc)

8. At the **Amazon Kinesis Data Generator** homepage.
    - Region: **ap-southeast-1**.
    - Stream/delivery stream: **analytics-workshop-stream**.
    - Records per second: **2000**.
    - Record template (Template 1): In the text input space, add the following json template and Click **Send Data**:

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
![Data Analysis on AWS](/images/1/14.png?featherlight=false&width=90pc)

9. When the tool sends ~100,000 messages, you can click - **Stop sending data to Kinesis**.

![Data Analysis on AWS](/images/1/14.1.png?featherlight=false&width=90pc)

10. After a while go to S3 Console Click here

    - Go to: **yourname-analytics-workshop-bucket** > **data**.
    - In this will have a raw folder created > Keep opening, you will see firehose push data to S3 using **yyyy/mm/dd/hh**

![Data Analysis on AWS](/images/1/21.png?featherlight=false&width=90pc)