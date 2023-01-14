+++
title = "Check EMR Job"
date = 2021
weight = 3
chapter = false
pre = "<b>6.3 </b>"
+++

#### Check status of Transform Job running on EMR

1. EMR cluster will take 6-8 minutes to initialize, and a few minutes to complete Spark script.
  + Cluster will delete itself after Spark job finishes running.
  + To check the status of the job, Click on the Cluster name: **analytics-workshop-transformer**.

![Data Analysis on AWS](/images/6/11.png?featherlight=false&width=90pc)

2. Go to the **Steps** tab.
  + Here you will see 2 components: **Spark application** and **Setup hadoop debugging**.
  + The state of **Spark application** will change from **Pending** to **Running** then **Completed**.

![Data Analysis on AWS](/images/6/12.png?featherlight=false&width=90pc)

3. When the Spark job has finished running, the EMR cluster will be deleted.
  + Under EMR > Cluster, you will see the status of the cluster as **Terminated** with the message **All steps completed**.

![Data Analysis on AWS](/images/6/13.png?featherlight=false&width=90pc)