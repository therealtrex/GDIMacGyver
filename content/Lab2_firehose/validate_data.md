---
title: "Lab 3.4 - Validate Ingestion and Explore Data"
chapter: true
weight: 44
---

## Validate CloudTrail data streaming into Splunk
Its time to now validate that the streaming Amazon Data Firehose data for CloudTrail is coming into Splunk.

- From your Splunk Console, **select Apps** followed by **Search and reporting**
- From the Search bar enter in the search below:

* Search: `index="aws-data" sourcetype="aws:cloudtrail"`
* Time Picker: **Last 24 hours**


![image004](/static/20_firehose/Image024.png)

##### Congratulations! You have now sucessfully configured your Splunk Add-on for AWS and have instance metadata & AWS Config data in Splunk. 