---
title: "Lab 1 - Amazon Data Firehose"
chapter: true
weight: 20
---

### Overview
This lab will take you through setting up CloudTrail to stream logs to S3 and CloudWatch. Then using a CloudWatch subscription filter we will **PUSH** logs to Splunk using Amazon Data Firehose.

This lab will go through the following: 
- Create a Splunk Index (optional if you already have one to use)
- Configure a Splunk HEC for accepting pushed logs from Amazon Data Firehose
- Create a CloudTrail Trail to send logs to S3 and CloudWatch
- Configure Amazon Data Firehose connection to send logs to Splunk
- Setup a CloudWatch subscription filter to push logs to Amazon Data Firehose


### Architecture Diagram 

![image001](/static/20_firehose/Image001.png)


