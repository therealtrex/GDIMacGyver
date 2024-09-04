---
title: "Lab 2.5 - Validate Ingestion and Explore Data"
chapter: true
weight: 44
---

## Validate VPC Flow log data streaming into Splunk
Its time to now validate that the streaming VPC Flow log data for our Lambda function is coming into Splunk.

- From your Splunk Console, **select Apps** followed by **Search and reporting**
- From the Search bar enter in the search below:

* Search: `index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow"`
* Time Picker: **Last 24 hours**


![splunkflowlog](/static/30_lambda/splunkflowlog.png)


##### Congratulations! You have now sucessfully configured VPC Flow logs to send data to Splunk using a Lambda function. This lab is now complete. 