# Streaming AWS CloudTrail logs to Splunk using Amazon Data Firehose (PUSH)
This lab will take you through setting up CloudTrail trail to stream logs to S3 and CloudWatch. Then using a CloudWatch subscription filter we will PUSH logs to Splunk using Amazon Data Firehose.

This lab will go through the following: 
- Create a Splunk HEC for accepting pushed logs from Amazon Data Firehose
- Create a CloudTrail trail to send logs to S3 and CloudWatch
- Configure Amazon Data Firehose connection to send logs to Splunk
- Setup a CloudWatch subscription filter to push logs to Amazon Data Firehose

## Architecture Diagram 
Below is the architecture pattern used for this lab:

![image001](/static/20_firehose/Image001.png)

### Click <a>[Next](/content/Lab3_firehose/setup_splunk.md)</a> to continue or click <a>[Back](/README.md) to go back to the beginning</a>