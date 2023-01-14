+++
title = "Create AWS Glue Crawlers"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

#### Create AWS Glue Crawlers

In this step, we'll go to the AWS Glue Console and create a glue crawlers to explore the schema of the newly pulled data into S3.

1. Access the admin interface of the [AWS Glue] service(https://console.aws.amazon.com/glue/home?region=ap-southeast-1)
+ In the left pane, select **Crawlers** > Click **Add Crawler**

![Data Analysis on AWS](/images/2/4.png?featherlight=false&width=90pc)

2. At the **Crawler info** page.
    + Crawler name: ```AnalyticsworkshopCrawler```.
    + Option to add tags:.
      + workshop: AnalyticsOnAWS.
    + Click **Next**.

![Data Analysis on AWS](/images/2/5.png?featherlight=false&width=90pc)

3. For **Choose data source and classifiers**

   - Select **Not yet**
   - Select **Add a data source**

![Data Analysis on AWS](/images/2/6.png?featherlight=false&width=90pc)

4. At the Add a data store page.
   - Choose a data store: **S3**.
   - Crawl data in: **Specified path in my account**.
   - Include path: **s3://yourname-analytics-workshop-bucket/data/**.
   - Click **Next**.
   - Add another data store: **No**.
   - Click **Next**.

![Data Analysis on AWS](/images/2/7.png?featherlight=false&width=90pc)

5. Complete adding data source and select **Next**

![Data Analysis on AWS](/images/2/8.png?featherlight=false&width=90pc)

6. At the **Choose an IAM Role** page.
   - Select: **Choose an existing IAM role**.
   - Selected IAM role: **AnalyticsworkshopGlueRole**.
   - Click **Next**.

![Data Analysis on AWS](/images/2/9.png?featherlight=false&width=90pc)

7. Then we create **Database**

   - Enter name: **```analyticsworkshopdb```**
   - Select **Create database**

![Data Analysis on AWS](/images/2/10.png?featherlight=false&width=90pc)

8. Complete database creation.

![Data Analysis on AWS](/images/2/11.png?featherlight=false&width=90pc)

9. For **Set output and scheduling**

   - Click **Add database**.
   - Database name: **analyticsworkshopdb**.
   - Click **Create**.
   - Frequency: **Run on demand**.
   - Click Next.

![Data Analysis on AWS](/images/2/12.png?featherlight=false&width=90pc)

10. At **Review all steps** page.

    - Double check all your configurations.
    - Click **Create crawler**.

![Data Analysis on AWS](/images/2/13.png?featherlight=false&width=90pc)

11. Finish creating **crawler**

![Data Analysis on AWS](/images/2/14.png?featherlight=false&width=90pc)

12. You test by **Run**

![Data Analysis on AWS](/images/2/00016.png?featherlight=false&width=90pc)

13. **Run** successful.

![Data Analysis on AWS](/images/2/00017.png?featherlight=false&width=90pc)