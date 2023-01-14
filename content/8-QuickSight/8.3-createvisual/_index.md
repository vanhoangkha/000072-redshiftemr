+++
title = "Create QuickSight Visual"
date = 2021
weight = 3
chapter = false
pre = "<b>8.3 </b>"
+++


#### Using Amazon QuickSight to represent processed data

**Visual 1: Heatmap of users and the track they listen to**

In this step, we create a visual that tells us which user is listening to the music on repeat.

+ In the lower left corner (Visual types):
  + Click on the icons to see the names of the types of visuals that can be used.
  + Click on **Heat Map**.
+ In the upper left corner (Fields list).
  + Click **device_id**.
  + Click **track_name**.
+ At the top of the graph you will see **Field wells: Rows: device_id | Columns: track_name**.

![Architect](/images/8/7.png?width=90pc)

**Visual 2: Most Listened Artist's Tree Map**

In this step, we will create a visual showing which artists are listened to the most.

+ In the upper left corner, Click **'+ Add' > Add Visual**.
+ In the lower left corner (Visual types):
  + Click on the icons to see the names of the types of visuals that can be used.
  + Click **Tree Map**.
+ In the upper left corner (Fields list):
  + Click **artist_name**.

![Architect](/images/8/8.png?width=90pc)


By now, you should be able to retrieve data using Kinesis firehose, save data in S3, catalog table in AWS Glue data catalog, transform data using Glue ETL/EMR and query and visualize data using Athena and QuickSight.

This lab provides an end to end structure, from the source of the data to the business dashboard in a serverless analytics deployment model.

The next two sections will introduce Lambda and Redshift and the enhancements to this architecture, to meet advanced needs for analytics.