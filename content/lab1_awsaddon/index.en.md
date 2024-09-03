---
title: "Lab 3 - Splunk Add-on for AWS"
chapter: true
weight: 40
---

## Using Splunk Add-on for AWS to ingest data into Splunk
In this workshop, you will learn how to ingest data from AWS into Splunk using the Splunk Add-on for AWS. For this section you will be ingesting AWS Config and Instance Metadata from AWS into Splunk. 

This lab will go through the following: 
- Creatomg AWS SQS queues to monitor our S3 bucket for new data
- Configure a S3 event notification to trigger a new SQS message
- Configure the Splunk Add-on for AWS to use authenticated API calls to retieve AWS EC2 metadata
- Lastly, configure the Splunk Add-on for AWS to monitor the SQS queue and fetch the data from the S3 bucket


#### Architecture Diagram

![image_tag](/static/10_awsaddon/Image_1.png) 


### Doing this workshop on your own
Before you can start this lab, you will need to complete the following steps:

1. Install the Splunk Add-on for AWS on your Splunk environment.  Refer to Splunk Documentation for steps on how to install the Add-on. 
2. Ensure you have the proper AWS permissions for Amazon S3, Amazon SQS, & AWS Config. 