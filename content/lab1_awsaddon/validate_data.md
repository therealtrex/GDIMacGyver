---
title: "Lab 3.4 - Validate Ingestion and Explore Data"
chapter: true
weight: 44
---

## Overview
In this lab you will validate if the data is ingested & indexed into Splunk successfully from AWS Add-on input you created earlier.

- From the **Splunk Add-on for AWS**, click the **Search** tab
- From the Search bar enter in the search below:

* Search: `index="aws-data" sourcetype="aws:cloudtrail"`
* Time Picker: **Last 24 hours**
* Search: `index="aws-data" sourcetype="aws:config" OR sourcetype="aws:metadata"`
* Time Picker: **Last 24 hours**


![image_tag](/static/10_awsaddon/validate_data/Image_1.png)


- Verify that there are *2* sourcetypes that appear in the search results. The sourcetypes are:

* `aws:metadata`
* `aws:config`


![image_tag](/static/10_awsaddon/validate_data/Image_2.png)

##### Congratulations! You have now sucessfully configured your Splunk Add-on for AWS and have instance metadata & AWS Config data in Splunk. 