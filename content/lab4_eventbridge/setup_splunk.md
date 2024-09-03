---
title: "Lab 4.1 - Setup Splunk ready for EventBridge data"
chapter: true
weight: 21
---

## Overview
This first part of the lab will take you through configuring a Splunk Index to store your AWS data and a Http Event Collector (HEC) token to use with Amazon Eventbridge.


::alert[You may already have a Splunk index `aws-data `for storing your AWS data. If so skip this first part of the lab and only complete the HEC creation section.]{header="Note"}

### Creating a Splunk Index for AWS data
- Login to your Splunk console
- From your Splunk Console select **Settings, Indexes**
- Select **New Index**
- Name the index as `aws-data` 
- Leave remaining defaults and click **Save** to create the index. 
- Click **Continue** on **Saving New Index**

![image003](/static/40_eventbridge/Image003.png)

### Creating a Splunk Index for AWS data
- From your Splunk Console select **Settings, Data Inputs**
- Select **HTTP Event Collector**
- Select **New Token**
- Give your HEC token a name Example: `eventbridge-hec`
- Leave Enable Indexer Acknowledgement **Unticked**

![image004](/static/40_eventbridge/create-hec.png)

::alert[For this lab we will NOT be using the HEC acknowlegement feature. Turning this on may cause the lab to fail sending data to Splunk.]{header="Note"}


- Leave remaining defaults and click **next** at the top of the screen. 
- For sourcetype click **select** and then click **Select Source Type**
- Select `aws:cloudwatch:guardduty`
- In the index section select the index `aws-data` you for your AWS data. 
- Click **review**, check over your steps.

![image004](/static/40_eventbridge/create-hec-2.png)

Click **Submit** to create HEC token.
**Copy your HEC token to use later**

![image005](/static/40_eventbridge/Image005.png)

- Lastly, **copy** your **Splunk Cloud URL** to use later eg scv-shw-87bea8f2733e0f.stg.splunkcloud.com

##### Congratulations on completing this part of the lab. Now we have a Splunk index for storing data and a HEC token we can move onto AWS to start configuring our services there.