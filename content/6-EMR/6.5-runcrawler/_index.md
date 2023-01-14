+++
title = "Rerun Glue Crawler"
date = 2021
weight = 5
chapter = false
pre = "<b>6.5 </b>"
+++

#### Rerun Glue Crawler

1. Go to [AWS Glue service admin interface](https://console.aws.amazon.com/glue/home?region=ap-southeast-1)
  + In the left pane, click **Crawlers**.
  + Select the crawler created in the previous section: **AnalyticsworkshopCrawler**.
  + Click **Run Crawler**.


![Data Analysis on AWS](/images/6/15.png?featherlight=false&width=90pc)

2. You will see the status change to **Starting**.
  + Wait a few minutes for the crawler to complete.
  + Crawler will show **Tables added** as 1.

![Data Analysis on AWS](/images/6/16.png?featherlight=false&width=90pc)

3. You can go to the databases section on the left and confirm that the **emr_processed_data** table has been added.

![Data Analysis on AWS](/images/6/17.png?featherlight=false&width=90pc)

Congratulations on completing the data transformation using EMR, we are ready to perform the data query using Amazon Athena in the next step.


![Data Analysis on AWS](/images/6/18.png?featherlight=false&width=90pc)


![Data Analysis on AWS](/images/6/19.png?featherlight=false&width=90pc)