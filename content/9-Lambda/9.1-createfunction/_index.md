+++
title = "Create Lambda Function"
date = 2021
weight = 1
chapter = false
pre = "<b>9.1 </b>"
+++

#### Create Lambda Function

1. Go to [Lambda service admin interface](https://console.aws.amazon.com/lambda/home?region=ap-southeast-1).
  + **Note**: Make sure the Region selected is Singapore ap-southeast-1

![Data Analysis on AWS](/images/9/1.png?featherlight=false&width=90pc)

2. Click **Create function** (If you are using Lambda for the first time, you should click Get Started to proceed).
  + Select **Author from scratch**.
  + In the **Basic Information** section:
  + Let the Function name be ```Analyticsworkshop_top5Songs```.
  + Select Runtime as **Python 3.8**.


![Data Analysis on AWS](/images/9/2.png?featherlight=false&width=90pc)

3. Expand **Choose or create an execution role** under Permissions, make sure **Create a new role with basic Lambda permissions** is checked.
  + Click **Create Function**.


![Data Analysis on AWS](/images/9/3.png?featherlight=false&width=90pc)