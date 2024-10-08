# Welcome to an AWS / Splunk GDI MacGyver Workshop
#### a T-REX production

<p align="center">
<img src="/static/gdimacgyverlogo.png">
</p>

## Overview 

Welcome to the Splunk and AWS GDI MacGyver workshop. This workshop forms part of the AWS Workshop platform found <a>[HERE](https://catalog.us-east-1.prod.workshops.aws/workshops/5039b0de-622d-4224-8760-d9dff0c13e0b/en-US/getting-started) </a>

In this workshop, we will study different solutions to get AWS security and log data into Splunk. We will look at different GDI solutions like:
1) Ingesting AWS data using Amazon Data Firehose <b>(PUSH method)</b>
2) Ingesting AWS data using AWS Lambda Function <b>(PUSH method)</b>
3) Ingesting AWS data from S3 bucket and APIs using Splunk Add-on for AWS <b>(PULL method)</b>
4) Ingesting AWS data from EventBridge using inbuilt HTTP POST <b>(PUSH method)</b>

Finally in <b>lab 5</b> you will wrap up by exploring some of your ingested data in Splunk using SPL and saving that data into a custom dashboard!

>[!NOTE]
> -This workshop is expected to take approximately 2-3 hours to complete.<br>
> -This workshop is created for target audiences like Cloud Architects, Security Analysts and Splunk Administrators.<br>
> -The participants are expected to have a general experience with AWS products and services, along with basic knowledge Splunk, Splunk Apps and running Splunk SPL Queries.<br>
> -This workshop is not inteded to be run as part of a joint AWS and Splunk event. These labs should work in your own AWS envirnoemnt <br>
> -To make things easier we have already configured the AWS add-on on your Splunk service including an index called `aws-data` for you to use. Please use these are part of the labs. 

>[!IMPORTANT]
>Please make sure you sign out or use an incognito tab when using your AWS console as you do not want to accidentally use your work/personal AWS account and end up with a bill or get in trouble
>TRUST ME, it has happened to people!!

Once you have completed this workshop you will end up deploying the following archiecture pattern:

![gdi_architecture](/static/gdi_workshop_architecture.png)

## Time to get to get started!
Below are the links to each of the labs

<a>[LAB1 - EC2 metadata and AWS Config logs to Splunk via AWS add-on PULL method](/content/Lab1_awsaddon/index.en.md) </a>

<a>[LAB2 - Amazon EventBridge notification using native EventBridge PUSH method ](/content/Lab2_eventbridge/index.en.md) </a>

<a>[LAB3 - CloudTrail logs to Splunk via Amazon Data Firehose PUSH method ](/content/Lab3_firehose/index.en.md) </a>

<a>[LAB4 - VPC Flow logs to Splunk via Amazon Lambda PUSH method ](/content/Lab4_lambda/index.en.md) </a>

<a>[LAB5 - Explore our data using Splunk ](/content/Lab5_data_exploration/exploring_data_1.md) </a>

