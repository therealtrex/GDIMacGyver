# Lab 1: Ingesting AWS Config and EC2 Metadata into Splunk using the AWS add-on (PULL) method
Welcome to Lab 1. This lab will step you through all required steps to ingest AWS config and ec2 meta data logs into Splunk using the Splunk support AWS add-on. 

This lab will go through the following: 
- Creatomg AWS SQS queues to monitor our S3 bucket for new data
- Configure a S3 event notification to trigger a new SQS message
- Configure the Splunk Add-on for AWS to use authenticated API calls to retieve AWS EC2 metadata
- Lastly, configure the Splunk Add-on for AWS to monitor the SQS queue and fetch the data from the S3 bucket


## Architecture Diagram
Below is the architecture pattern used for this lab:

![image_tag](/static/10_awsaddon/Image_1.png) 


>[!NOTE]
>Usually this lab would have a pre-requisite of the <a>[AWS add-on](https://splunkbase.splunk.com/app/1876)</a> installed on your Splunk intallation. To make things simpler we have already done this. 


### Click <a>[Next](/content/Lab1_awsaddon/setup_aws_sqs.md)</a> to continue or click <a>[Back](/README.md) to go back to the beginning</a>