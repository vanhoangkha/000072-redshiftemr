---
title : "Visualize in Quicksight"
date : "`r Sys.Date()`"
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

#### Visualize in Quicksight

In this module, we will use Amazon Quicksight to build some visual charts based on data that has been collected and stored on S3.

Feel free to explore the different visualization options available in Quicksight!

#### QuickSight Setup

1. In this step, we will visualize the processed data using QuickSight.

- Access: QuickSight Dashboard
- Select Sign up for QuickSight


![Data Analytics on AWS](/images/10/0001.png?featherlight=false&width=90pc)

2. Make sure Enterprise is selected and Click Continue


![Data Analytics on AWS](/images/10/0002.png?featherlight=false&width=90pc)

3. QuickSight account name: yournameanalyticsworkshop


![Data Analytics on AWS](/images/10/0003.png?featherlight=false&width=90pc)


4. Notification email address: you@youremail.com
Select Amazon Athena - this allows QuickSight to access the Amazon Athena database


![Data Analytics on AWS](/images/10/0004.png?featherlight=false&width=90pc)

5. Choose Amazon S3
Select yourname-analytics-workshop-bucket
Select Finish


![Data Analytics on AWS](/images/10/0005.png?featherlight=false&width=90pc)

6. Select Finish
Wait for your QuickSight account to be created

![Data Analytics on AWS](/images/10/0006.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/10/0007.png?featherlight=false&width=90pc)

7. Add a New Dataset


![Data Analytics on AWS](/images/10/0008.png?featherlight=false&width=90pc)

8. Access:
- In the upper right, Select New Dataset
- Select Athena
- New Athena data source
- Data source name: analyticsworkshop



![Data Analytics on AWS](/images/10/0009.png?featherlight=false&width=90pc)

9. Select Validate connection
- This will check if your QuickSight can access Athena
- Select Create data source

![Data Analytics on AWS](/images/10/00010.png?featherlight=false&width=90pc)

10. Choose your board:
- Database: contains sets of tables - choose analyticsworkshopdb
- Tables: contains data you can visualize - choose processed_data
- Select on Select

![Data Analytics on AWS](/images/10/00011.png?featherlight=false&width=90pc)

11. Complete data set creation:
- Select Directly query your data
- Select Visualize

![Data Analytics on AWS](/images/10/00012.png?featherlight=false&width=90pc)

12. Use Amazon Quick Sight to Visualize Our Processed Data
Visualization 1: User's heat map and the songs they're listening to


![Data Analytics on AWS](/images/10/00013.png?featherlight=false&width=90pc)

13. In this step, we will create a visualization to see which users are listening to songs over and over again.

- On the bottom left panel ((Visual types):
- Hover over icons to see the names of available visualizations
- Select on Heat Map
- On the upper left panel (Fields list)
- Select device_id
- Select track_name
- Right above the visualization you will see Field wells: Rows: device_id | Columns: track_name
- If you hover over the dark blue areas on the heatmap, you'll see that those particular users are listening to the same song over and over again.

![Data Analytics on AWS](/images/10/00014.png?featherlight=false&width=90pc)

#### Illustration 2: Tree map of the most played artists
14. In this step, we will create an illustration showing the most played artists.

- In the upper left corner, Select '+ Add' > Add Visual. This will add a new panel to the right panel.
- In the lower left panel (Visual types):
- Hover over the icons to see the names of the illustrations
- Select on Tree Map
- In the upper left panel (Fields list):
- Select artist_name
- Experiment and explore the Amazon QuickSight Console. You can try filters, other types of illustrations, and more.
- So far, we have represented data using Kinesis firehose, stored data in S3, subscribed to tables in AWS Glue data catalog, transformed data using Glue ETL/EMR, and accessed query and visualize data using Athena and Quicksight.
This provides an end-to-end architecture, from source to enterprise dashboard, in a serverless analytics deployment model.
- The two Next modules introduce Lambda and Redshift and include Next enhancements to this architecture, to meet the various additional requirements to deliver on-demand data for analytics.

![Data Analytics on AWS](/images/10/00015.png?featherlight=false&width=90pc)