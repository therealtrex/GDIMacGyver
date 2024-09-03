---
title: "Lab 4.4 - Validate Ingestion and Explore Data"
chapter: true
weight: 44
---

## Validate Eventbridge data streaming into Splunk
Its time to now validate that the Amazon EventBridge data is flowing into Splunk.

::alert[Eventbridge data from Amazon Guard Duty can take up to 15 minutes too appear in Splunk due to the fequency of when the data is logged in Amazon Guard Duty.]{header="Note"}

- From your Splunk Console, **select Apps** followed by **Search and reporting**
- From the Search bar enter in the search below:

* Search: `index=aws-data sourcetype="aws:cloudwatch:guardduty"`
* Time Picker: **Last 24 hours**


![splunkguardduty](/static/40_eventbridge/splunk_guardduty.png)


##### Congratulations! You have now sucessfully configured Amazon Guard Duty logs through Amazon Eventbridge into Splunk. This lab is now complete.