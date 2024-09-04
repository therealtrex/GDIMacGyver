---
title: "Lab 2 - AWS Lambda"
chapter: true
weight: 30
---

### Overview
In this workshop, you will learn how to deploy a Lambda function to ingest AWS log data into Splunk over Http Event Collector (HEC) endpoint. For this use case, we will ingest [VPC Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) into Splunk.

This lab will go through the following: 
- Create a Splunk Index (optional if you already have one to use)
- Configure a Splunk HEC for accepting pushed logs from Lambda
- Create a VPC Flow log which will stream logs to a CloudWatch Log group
- Setup a CloudWatch subscription filter to trigger the lambda function to send logs to Splunk
- Validate the data is streaming to Splunk

### Architecture Diagram 

![image001](/static/30_lambda/lamba-architecture.png)

 
### Doing this workshop on your own
::alert[Follow the below step for CloudFormation **only if you are doing this workshop on your own and not in AWS Hosted Event**. You are doing this workshop in an AWS hosted event, **you can skip to next step** since these resources have been already provisioned for you]{header="Note"}
Click [Launch Stack](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=SplunkGDIWorkshopFlowLogStack&templateURL=https://ws-assets-prod-iad-r-iad-ed304a55c2ca1aee.s3.us-east-1.amazonaws.com/5039b0de-622d-4224-8760-d9dff0c13e0b/SplunkFlowlogs.yml) to launch Cloudformation stack creation. This stack will will create the CloudWatch Log Group and IAM role, which you would need in next steps. Wait for the Cloudformation to complete.