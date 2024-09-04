---
title: "Lab 2.4 - Setup CloudWatch Subscription Filter"
chapter: true
weight: 32
---

## Overview
In this part of the lab we will configure a subscription filter to trigger off our Lambda function (which will send logs to Splunk) when new logs arrive in the log group. 

### Create CloudWatch Subscription Filter
- Select your **SplunkGDIWorkshopFlowLogGroup** log group we clicked on earlier in the lab. (if not select it from CloudWatch, Logs, Log groups). 
- Select the **Subscription filters** tab.
- Click the **Create pull down** menu and select **Create Lambda subscription filter**.
  
![subfilter](/static/30_lambda/subfilter.png)

- Select the Lambda function you created in previous lab, by matching the physical id. 
- Name the subscription filter `SplunkVPCSubFilter`
- Leave remaining defaults and Click **Start streaming**.

##### Congratulations on completing this part of the lab. All that is left it to now verify the data in Splunk!