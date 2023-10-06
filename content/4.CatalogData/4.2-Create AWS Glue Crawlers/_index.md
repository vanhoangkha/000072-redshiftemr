---
title : "Creating AWS Glue Crawlers"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Create AWS Glue Crawlers

In this step, we will navigate to the AWS Glue Console and create glue crawlers to explore the schema of newly imported data in S3.

1. Go to: Select [here](https://console.aws.amazon.com/glue/home?region=us-east-1)
- On the left panel, Select Crawlers
- Select Create crawler

![Data Analytics on AWS](/images/4/0007.png?featherlight=false&width=90pc)

2. Information about crawler
- Crawler name: AnalyticsworkshopCrawler
- Option to add Tags (labels), for example: workshop: AnalyticsOnAWS
- Select Next

![Data Analytics on AWS](/images/4/0008.png?featherlight=false&width=90pc)

3. Select Add a data source. Select a data source.


![Data Analytics on AWS](/images/4/0009.png?featherlight=false&width=90pc)

4. - Data source: S3

- Let the network connect - options as is
- Select In this account (in this account) in the Location of S3 data section.
- Include S3 path: s3://yourname-analytics-workshop-bucket/data/
- Leave Subsequent crawler runs at default Crawl all sub-folders (Crawl all subfolders)
- Select Add an S3 data source

![Data Analytics on AWS](/images/4/00010.png?featherlight=false&width=90pc)

5. Select the recently added S3 data source under Data Sources. Select Next

![Data Analytics on AWS](/images/4/00011.png?featherlight=false&width=90pc)

6. IAM Role (IAM role)
- Under Existing IAM role (existing IAM role), select AnalyticsworkshopGlueRole
- Leave everything else as it is.
- Select Next

![Data Analytics on AWS](/images/4/00012.png?featherlight=false&width=90pc)

7. Output configuration:
Select Add database to open a new window to create a database.


![Data Analytics on AWS](/images/4/00013.png?featherlight=false&width=90pc)

8. Database Information
- Name: analyticsworkshopdb
- Select Create database

![Data Analytics on AWS](/images/4/00014.png?featherlight=false&width=90pc)

9. Close the current window and return to the previous window.



![Data Analytics on AWS](/images/4/00015.png?featherlight=false&width=90pc)

10. Refresh by Clicking on the refresh icon to the right of the Target database.
- Select analyticsworkshopdb under Target database
- Under Crawler schedule (Crawler schedule)
- Frequency: On demand (On demand)
- Select Next

![Data Analytics on AWS](/images/4/00016.png?featherlight=false&width=90pc)

11. Review all settings under Review and create. Select Create crawler

![Data Analytics on AWS](/images/4/00017.png?featherlight=false&width=90pc)

12. You will see this message: The following Crawler has been created: "AnalyticsworkshopCrawler"


![Data Analytics on AWS](/images/4/00018.png?featherlight=false&width=90pc)

13. Select Run crawler to run the crawler for the first time


![Data Analytics on AWS](/images/4/00019.png?featherlight=false&width=90pc)

14. Wait for a few minutes.

![Data Analytics on AWS](/images/4/00020.png?featherlight=false&width=90pc)