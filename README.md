---
title: "Introduction"
weight: 0
---

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


# Splunk AWS Getting Data In (GDI) Workshop

In this workshop, we will study different solutions to get AWS security and log data into Splunk Enterprise. We will look at different GDI solutions like:

1) Ingesting AWS data using Amazon Data Firehose (PUSH method)
2) Ingesting AWS data using AWS Lambda Function (PUSH method)
3) Ingesting AWS data from S3 bucket and APIs using Splunk Add-on for AWS (PULL method)
4) Ingesting AWS data from EventBridge using inbuilt HTTP POST (PUSH method)
5) Exploring our ingested data in Splunk using SPL and saving that data into a custom dashboard

By completing this workshop, the participants will gain hands-on knowledge on different solutions available to get AWS data into Splunk.

## Additional Information
- This workshop is expected to take approximately 1 to 2 hours to complete.
- This workshop is created for target audiences like Cloud Architects, Security Analysts and Splunk Administrators.
- The participants are expected to have a general experience with AWS products and services, along with basic knowledge of Splunk Enterprise, Splunk Apps and running Splunk SPL Queries.
- There will be no cost incurred for doing this workshop in an AWS or Splunk hosted event. There will be cost incurred if you plan to do this workshop in your own AWS account. Please follow the clean up instructions included in each workshop Labs to avoid incurring any additional costs.
