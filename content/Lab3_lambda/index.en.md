## Lab 3: Setting up VPC flow logs to stream data into Splunk using Amazon Lambda PUSH method.
In this workshop, you will learn how to deploy a Lambda function to ingest AWS log data into Splunk over Http Event Collector (HEC) endpoint. For this use case, we will ingest [VPC Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html) into Splunk.

This lab will go through the following: 
- Configure a Splunk HEC for accepting pushed logs from Lambda
- Create a VPC Flow log which will stream logs to a CloudWatch Log group
- Deploy a lambda funtion which will send the logs to Splunk HEC
- Setup a CloudWatch subscription filter to trigger the lambda function 
- Validate the data is streaming to Splunk

### Architecture Diagram 
Below is the high level architecture that you will deploy for this lab:

![image001](/static/30_lambda/lamba-architecture.png)

### Click <a>[Next](/content/Lab3_lambda/setup_splunk.md)</a> to continue or click <a>[Back](/README.md) to go back to the beginning</a>