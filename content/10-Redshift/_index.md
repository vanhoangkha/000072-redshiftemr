+++
title = "Warehouse on Redshift"
date = 2020
weight = 10
chapter = false
pre = "<b>10. </b>"
+++

---

In this section, we will set up an Amazon Redshift cluster, and use AWS Glue to load data into Amazon Redshift. We'll learn about some designs and best practices for loading data into a table in Redshift, and running queries on it.

![Architect](/images/10/redshift.png?width=60pc)

#### Content

1. [Create Redshift IAM role](10.1-createiamrole/)
2. [Create Redshift cluster](10.2-createcluster/)
3. [Create S3 Gateway Endpoint](10.3-s3gateway/)
4. [Configure Security Group](10.4-configuresecgroup/)
5. [Create Redshift connection](10.5-glueconnection/)
6. [Create schema and tables](10.6-createschema/)
7. [Transform and load data](10.7-extractloaddata/)
8. [Data Check](10.8-reviewdata/)
9. [Optimize Redshift](10.9-optimizeredshift/)