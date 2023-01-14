+++
title = "Run Jupyter Notebook"
date = 2021
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

#### Run Jupyter Notebook


1. Download and save the file below: [analytics-workshop-notebook.ipynb](https://intro-to-analytics-on-aws.workshop.aws/notebooks/analytics-workshop-notebook.ipynb ).
  + You can also download the attached notebook file [here](https://000072.awsstudygroup.com/download/analytics-workshop-notebook.ipynb).


2. Go to [Notebooks admin interface](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks)
  + Click **aws-glue-AnalyticsworkshopNotebook** and click **Open Jupyter**, Jupyter Notebook will be automatically opened in a new tab.

![Data Analysis on AWS](/images/3/00014.png?featherlight=false&width=90pc)

3. Click **Upload** (top right corner of the screen)
  + Find and upload the previously downloaded **analytics-workshop-notebook.ipynb** file.
  + Click **Upload** to confirm upload.

![Data Analysis on AWS](/images/3/00015.png?featherlight=false&width=90pc)

4. Click **analytics-workshop-notebook.ipynb** to open the notebook.

![Data Analysis on AWS](/images/3/00016.png?featherlight=false&width=90pc)

5. Make sure 'Sparkmagic (PySpark)' is written on the right corner of the notebook; this is the name of the kernel Jupyter will use to run code blocks in the notebook.

6. Read and follow the instructions to understand the concepts of Glue.

{{%notice tip%}}
As you go through the steps in the notebook, you will also need to change some information such as the name of your S3 bucket.
{{%/notice%}}

![Data Analysis on AWS](/images/3/00017.png?featherlight=false&width=90pc)

7. Execute the command run.

![Data Analysis on AWS](/images/3/00018.png?featherlight=false&width=90pc)

8. Create dynamic frames from **Glue catalog**

![Data Analysis on AWS](/images/3/00019.png?featherlight=false&width=90pc)

9. View schema.

![Data Analysis on AWS](/images/3/00020.png?featherlight=false&width=90pc)

10. View the record number

![Data Analysis on AWS](/images/3/00021.png?featherlight=false&width=90pc)

11. View record details from **Dataframe**

![Data Analysis on AWS](/images/3/00022.png?featherlight=false&width=90pc)

12. Using **Spark SQL**

![Data Analysis on AWS](/images/3/00023.png?featherlight=false&width=90pc)

13. Implement **Count** and **Filter**

![Data Analysis on AWS](/images/3/00024.png?featherlight=false&width=90pc)

14. Implementing **Glue Transforms**

![Data Analysis on AWS](/images/3/00025.png?featherlight=false&width=90pc)

15. Write to **S3**

![Data Analysis on AWS](/images/3/00026.png?featherlight=false&width=90pc)

16. Using **boto3**

![Data Analysis on AWS](/images/3/00027.png?featherlight=false&width=90pc)

17. Check the table

![Data Analysis on AWS](/images/3/00028.png?featherlight=false&width=90pc)

18. Test from the **S3** interface

![Data Analysis on AWS](/images/3/00029.png?featherlight=false&width=90pc)