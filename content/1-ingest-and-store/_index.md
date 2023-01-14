+++
title = "Ingest and Store"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Ingest and Store
---

To start, we'll generate some dummy data near real-time with the Kinesis data generator, and transfer that data to S3 with the Kinesis Firehose delivery stream.

We will also copy some reference data into the Amazon S3 bucket.

![Data Analysis on AWS](/images/1/ingest.png?featherlight=false&width=60pc)

#### Content

1. [Create S3 Bucket](1.1-creates3bucket/)
2. [Create Kinesis Firehose](1.2-createkinesis/)
3. [Generate emulator data](1.3-generatedata/)