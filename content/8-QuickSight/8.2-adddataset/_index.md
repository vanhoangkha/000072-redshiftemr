+++
title = "Add Dataset"
date = 2021
weight = 2
chapter = false
pre = "<b>8.2 </b>"
+++


#### Add Dataset

1. Go to [Quick Sight service interface](https://ap-southeast-1.quicksight.aws.amazon.com/en/start).
  + In the upper right corner, Click **Manage Data**.
  + Click **New Data Set**.

![Data Analysis on AWS](/images/7/4.png?featherlight=false&width=90pc)

2. Click **Athena**.

![Data Analysis on AWS](/images/7/5.png?featherlight=false&width=90pc)


3. New Athena data source.
    + Data source name: ```analyticsworkshop```.
    + Click **Validate connection**.
      + This will check if QuickSight can access Athena.
    + Click **Create data source**.

![Data Analysis on AWS](/images/7/6.png?featherlight=false&width=90pc)

4. Choose your table:
    + Database: select **analyticsworkshopdb**.
    + Tables: select **processed_data**.
    + Click **Select**.
![Data Analysis on AWS](/images/7/7.png?featherlight=false&width=90pc)


5. Finish creating data set:
    + Select **Directly query your data**.
    + Click **Visualize**.


![Data Analysis on AWS](/images/7/8.png?featherlight=false&width=90pc)