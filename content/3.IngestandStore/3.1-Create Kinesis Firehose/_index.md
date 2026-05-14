---
title : "Creating Kinesis Firehose"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

#### Create Kinesis Firehose
In this step, we will navigate to the Kinesis Console and create a Kinesis Firehose data stream to receive the data and store it in S3:

1. Go to: **Kinesis Firehose Console** [Click here](https://console.aws.amazon.com/firehose/home?region=us-east-1)
   - Click on **Create delivery stream** (Create data stream)

![Data Analytics on AWS](/images/2/0001.png?featherlight=false&width=90pc)

2. Select source and destination
   - Source: **Direct PUT**
   - Destination: **Amazon S3**
   - Delivery stream name: **analytics-workshop-stream**

![Data Analytics on AWS](/images/2/0002.png?featherlight=false&width=90pc)

3. Convert and transform records

    - Transform source records using AWS Lambda: **Disabled** (Leave 'Enable data transformation' as unchecked)
    - Convert RecConvert record format: **Disabled** (Leave 'Enable record format conversion' as unchecked)
    - Destination settings
    - S3 bucket: **yourname-analytics-workshop-bucket**
    - Dynamic partitioning: **Not Enabled**
    - S3 bucket prefix: data/raw/ (Note: the slash / after raw is important. If you omit it, Firehose will copy the data to an unexpected location)
    - S3 bucket error output prefix: Leave blank

![Data Analytics on AWS](/images/2/0003.png?featherlight=false&width=90pc)

4. Expand Buffer hints, compression and encryption
   - Buffer size: 1 MiB
   - Buffer interval: 60 seconds
   - Compression for data records: Not Enabled
   - Encryption for data records: Not Enabled

![Data Analytics on AWS](/images/2/0004.png?featherlight=false&width=90pc)

5. Advanced settings
   - Server-side encryption: unchecked
   - Amazon Cloudwatch error logging: Enabled
   - Permissions: Create or update IAM role KinesisFirehoseServiceRole-xxxx
   - Optionally add Tags, e.g.:
   - Key: workshop
   - Value: AnalyticsOnAWS

![Data Analytics on AWS](/images/2/0005.png?featherlight=false&width=90pc)

6. Review the configuration and make sure it is as mentioned above. Select **Create delivery stream**

![Data Analytics on AWS](/images/2/0006.png?featherlight=false&width=90pc)

7. Create a successful delivery stream.

![Data Analytics on AWS](/images/2/0007.png?featherlight=false&width=90pc)