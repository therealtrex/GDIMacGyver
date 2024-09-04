---
title: "Lab 4 - Amazon EventBridge"
chapter: true
weight: 50
---

### Overview
In this workshop you will learn how to create Splunk destination as EventBridge Target and configure EventBridge Rules to ingest events from Amazon GuardDuty into Splunk.

This lab will go through the following: 
- Create a Splunk Index (optional if you already have one to use)
- Setup Splunk as a API destination in Eventbridge
- Setup Eventbridge Rule for Amazon GuardDuty events
- Validate data is streaming into Splunk from Amazon GuardDuty

### Architecture Diagram 

![image001](/static/40_eventbridge/architecture-eventbridge.png)



### Prerequisites
  
- You will need Amazon GuardDuty enabled in your AWS account. For AWS hosted Event, this will be enabled in the Workshop Studio AWS account. You can skip to next Step. For those running on their own account, follow [aws documentation](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html) to enable Amazon GuardDuty in your account.