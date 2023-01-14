+++
title = "Join dataset"
date = 2020
weight = 3
chapter = false
pre = "<b>5.3 </b>"
+++


#### Join dataset in DataBrew

1. Click **GRID** tab to return to grid view.
  + Click **JOIN**.


![Data Analysis on AWS](/images/5/13.png?featherlight=false&width=90pc)


2. Click **Connect new dataset**.

![Data Analysis on AWS](/images/5/14.png?featherlight=false&width=90pc)

3. Click **All AWS Glue table**, and click **analyticsworkshopdb**.


![Data Analysis on AWS](/images/5/15.png?featherlight=false&width=90pc)


4. Click **reference_data**.
  + Dataset name - **reference-data-dataset**.

![Data Analysis on AWS](/images/5/16.png?featherlight=false&width=90pc)

5. At the **Join** page.
  + Select **track_id** from **raw-dataset**.
  + Select **track_id** from **reference-data-set**.
  + Uncheck **track_id** from **Table B**.
  + Click **Finish**.

![Data Analysis on AWS](/images/5/18.png?featherlight=false&width=90pc)

6. You will see the result as below.
  + On the right hand side, the **Recipe** section, you will see the transform steps you have taken, including changing the data type to String and performing **inner join** with **reference-data-dataset **.

![Data Analysis on AWS](/images/5/19.png?featherlight=false&width=90pc)