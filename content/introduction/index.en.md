---
title : "Architecture"
weight : 10
---


By completing all modules of this workshop, you will be deploying the following architecture:

![gdi_architecture](/static/gdi_workshop_architecture.png)


#### We will be deploying solutions to get the following AWS source data into Splunk:
- Ingest CloudTrail log data from CloudWatch Logs into Splunk using Amazon Data Firehose (Push Method).
- Ingest VPC FlowLogs from CloudWatch Logs into Splunk using AWS Lambda function (Push Method).
- Using Splunk add-on for AWS in Splunk to configure inputs for AWS Config logs from S3 bucket & EC2 metadata into Splunk (Pull Method).
- Ingest Amazon GuardDuty findings as events from EventBridge by configuring Splunk as a target API Destination (Push Method).
