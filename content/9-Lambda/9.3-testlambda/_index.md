+++
title = "Querying data with Lambda"
date = 2021
weight = 3
chapter = false
pre = "<b>9.3 </b>"
+++

#### Data query with Lambda

Our function is now ready to test.

1. Deploy function by pressing **Deploy** button.


![Data Analysis on AWS](/images/9/12.png?featherlight=false&width=90pc)

2. Configure the test lambda function to see the run result of the newly created lambda function.
  + Click **Test** in the upper right corner of the **Code Source** section.

![Data Analysis on AWS](/images/9/13.png?featherlight=false&width=90pc)


3. In the new pop-up window configure test event.
  + **Create new test event** is selected by default.
  + Event template: **Hello World**.
  + Event name: **Test**.
  + Leave everything else as is.
  + Click **Create**.

![Data Analysis on AWS](/images/9/14.png?featherlight=false&width=90pc)

4. Press **Test** again
  + You will see the output in json format under **Execution Result** section.


![Data Analysis on AWS](/images/9/15.png?featherlight=false&width=90pc)

Next we will check if the data from the Lambda function is the same as the data queried from Athena.