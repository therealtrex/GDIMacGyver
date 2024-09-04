---
title: "Lab 1.4 - Setup CloudWatch Subscription Filter"
chapter: true
weight: 24
---

## Overview
In this part of the lab we will setup the CloudWatch subscription filter on the Log Group for our CloudTrail to stream logs to Amazon Data Firehose configured earlier.

### Setup CloudWatch Subscription Filter

- From your AWS console. search and select **CloudWatch**

![image019](/static/20_firehose/Image019.png)

- From the **logs** section select **Log Groups**
- Select the log group **CloudTrail/SplunkGDIWorkshopCTrailLogGroup**

- Select the **subscription filter tab**
- Click the **Create** drop down and select **Create Amazon Data Firehose subscription filter**


![image020](/static/20_firehose/Image020.png)

- Select **Current Account**
- Under the Kinesis Firehose Delivery Stream select the delivery stream created earlier in the lab. i.e **SplunkWorkshopDeliveryStream**
- Under **Grant Permissions** search for and select **SplunkGDIWorkshopCTrailSubscriptionRole**

![image021](/static/20_firehose/Image021.png)

- Under **subscription filter name**, name as: `cloudtrail-\<aws-region\>-\<aws-account-number\>-filter`
- Leave remaining defaults and click **Start Streaming**


##### Congratulations, now that you have setup CloudTrail, Amazon DataFirehose and the CloudWatch subscription filter. All that is left to do is verify the data is streaming into Splunk. 