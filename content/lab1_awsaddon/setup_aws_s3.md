---
title: "Lab 3.2 - Setup S3 Event Notification"
chapter: true
weight: 42
---

## Overview
In this lab you will be adding event notifications to an existing Amazon S3 bucket. This will be used by the Splunk Add-on for AWS to ingest the AWS Config Data. 

### Setup Event Notification for Amazon S3 Bucket
- Navigate to the Amazon S3 Service in your AWS Console. 
- Select **team-template-awsconfig** bucket; you should see a bucket prefixed with **team-template-awsconfig**. 
- Click on **Properties**. 


![image_tag](/static/10_awsaddon/setup_aws/Image_9.png) 


- Scroll down until you get to the Event Notifications section and select Create **Event Notification**. 


![image_tag](/static/10_awsaddon/setup_aws/Image_10.png) 


- Under General Configuration, **enter Event Name** as: `SplunkWorkshopEventNotification`
- Under Event types, select **All object create events**


![image_tag](/static/10_awsaddon/setup_aws/Image_11.png) 


- Scroll down and under Destination, select **SQS Queue** 
- Select the SQS queue **SplunkWorkshopQueue**.  
- Click **Save Changes** once done.


![image_tag](/static/10_awsaddon/setup_aws/Image_12.png) 

### Obtain AWS Credentials to Configure Splunk Add-on for AWS

In the AWS Console navigate to the **Secrets Manager** Service. Click on the *SplunkSecrets* Secret Name. 

![image_tag](/static/10_awsaddon/setup_aws/Image_13.png) 

Click on **Retrieve Secret Value**

![image_tag](/static/10_awsaddon/setup_aws/Image_14.png) 

Copy the **accesskey** & **secretkey**. These will be used in the next Lab 1.3 to configure your Splunk Add-on for AWS. 

![image_tag](/static/10_awsaddon/setup_aws/Image_15.png) 


##### Congratulations, you have setup the S3 Event Notifications successfully. Lets move on to next step to setup SQS-based-S3 input on Splunk Add-on

