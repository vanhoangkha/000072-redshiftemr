+++
title = "Security group configuration"
date = 2021
weight = 4
chapter = false
pre = "<b>10.4 </b>"
+++

#### Confirm and add the rule to the default security group

In this step, we will confirm and add a rule for the Redshift security group so that the Glue service can work with Redshift.

1. Go to [VPC service administration interface: security groups](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#SecurityGroups:sort=tag:Name) .
  + Select Redshift security group. It will be at the default security if it was not changed when we created the Redshift cluster.
  + If you have more than 1 security group in the list, follow these steps:
    + Access to [Redshift service administration interface](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1).
    + Click **redshift-cluster-1**.
    + Click the **Properties** tab.
    + Scroll down and check the **Network and security** section to get the Security Group id.
  + Once you have confirmed Security Group, select security group.
  + Click **Inbound rules**.
  + Click **Edit rules**.

![Data Analysis on AWS](/images/10/19.png?featherlight=false&width=90pc)

2. Check the existing rule.
    + Type: All Traffic.
    + Source: [Name of the security group you are editing].


![Data Analysis on AWS](/images/10/20.png?featherlight=false&width=90pc)

{{% notice note %}}
This self-referencing rule is necessary for Glue to communicate with Redshift.
{{% /notice %}}

  + Add **HTTPS** rule for Amazon S3 access.
    + Type: ```HTTPS```.
    + Source: [s3-prefix-list-id].

{{% notice note %}}
Under **Source** select Custom and enter "pl in the text box next to it, the previously created S3 endpoint will display and select it.
{{% /notice %}}

  + Click **Save rules**.

![Data Analysis on AWS](/images/10/20.png?featherlight=false&width=90pc)

  + Click **Outbound Rules**.
  + Click **Edit rules**.


![Data Analysis on AWS](/images/10/21.png?featherlight=false&width=90pc)

  + Leave the rule as it is with the following values:
    + Type: All Traffic
    + Source: ```0.0.0.0/0```
  + Rule self-referencing
    + Type: All TCP
    + Source: [Name of the security group you are editing]
  + Click **Save rules**.

![Data Analysis on AWS](/images/10/22.png?featherlight=false&width=90pc)