---
title: "Lab 4.3 - Setup EventBridge Rule"
chapter: true
weight: 52
---

## Overview
In previous lab we setup Splunk as EventBridge Destination for our target. Lets now setup an EventBridge Rule to get all GuardDuty Events sent to Splunk

### Configure EventBridge Target & Connection for Splunk
- Go Amazon Eventbridge in [AWS console](https://console.aws.amazon.com/events/home), select **Rules** under **Buses** on the left hand side.
- Click **Create Rule**.
- Enter the name for the Rule as `SplunkGuardDutyRule`, leave default values and Click **Next**.
- Leave *Event source* as *AWS events or EventBridge partner events*, scroll down to **Event Pattern**.
- From the Event Pattern section, select the following:
  - Select **AWS services** for *Event source*
  - Select **GuardDuty** for *AWS Service* 
  - Select **All Events** for *Event Type*
  
![event_selection](/static/40_eventbridge/eventbridge_eventselection.png)  

- Click **Next** and select **EventBridge API destination** as *Target Type*.
- Under *API Destination* check **Use an existing API destination** and select the Splunk destination we created in earlier step
- Under *Execution Role*, select **Use existing role** and select the IAM Role **SplunkGDIWorkshopEventBridgeInvokeApiRole**

![target_selection](/static/40_eventbridge/eventbridge_targetselection.png) 

- Click **Next**. Enter any tags or skip this screen and Click **Next**.
- Review the configurations and **click Create rule** to create the rule.
  
##### Congrats you have now successfully created EventBridge destination for Splunk and a Rule to ingest GuardDuty Findings as events into Splunk. Wait for about 10-15 minutes and check your Splunk index to see if you receive the GuardDuty Events

![check_splunk](/static/40_eventbridge/splunk_guardduty.png)