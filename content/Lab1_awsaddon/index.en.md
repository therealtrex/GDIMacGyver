# Lab 1: Ingesting AWS Config and EC2 Metadata into Splunk using the AWS add-on (PULL) method
Welcome to Lab 1. This lab will step you through all required steps to ingest AWS config and ec2 meta data logs into Splunk using the Splunk support AWS add-on. 

This lab will go through the following: 
- Creatomg AWS SQS queues to monitor our S3 bucket for new data
- Configure a S3 event notification to trigger a new SQS message
- Configure the Splunk Add-on for AWS to use authenticated API calls to retieve AWS EC2 metadata
- Lastly, configure the Splunk Add-on for AWS to monitor the SQS queue and fetch the data from the S3 bucket

>[!IMPORTANT]
>I will call this out twice as its important. AWS config does not log frequently! AWS Config has two logging pieces. The configuration recorder and configuration snapshots. The Recorder when setup in continuous mode does continuous recording but will only log to S3 every six hours. The configuration snapshot capability of AWS Config will log to S3 on either a 1,3,6,12 or 24 hour frequewcy (we have setup 1hr for this lab). This means during this lab you may have to wait for a full hour to see anythign in Splunk. It is recommended you completed the lab and then we will check on it later during the day to make sure logs are coming in ok. More Info on this <a>[HERE](https://aws.amazon.com/blogs/mt/configuration-history-configuration-snapshot-files-aws-config/)</a>.

## Architecture Diagram
Below is the architecture pattern used for this lab:

![image_tag](/static/10_awsaddon/Image_1.png) 


>[!NOTE]
>Usually this lab would have a pre-requisite of the <a>[AWS add-on](https://splunkbase.splunk.com/app/1876)</a> installed on your Splunk intallation. To make things simpler we have already done this. 


### Click <a>[Next](/content/Lab1_awsaddon/setup_aws_sqs.md)</a> to continue or click <a>[Back](/README.md) to go back to the beginning</a>