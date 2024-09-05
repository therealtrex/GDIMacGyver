# Setting up Amzaon S3 Event Notrification
In this part of the lab you will be adding event notifications to an existing Amazon S3 bucket. This will be used by the Splunk Add-on for AWS to ingest the AWS Config Data. 

### Setup Event Notification for Amazon S3 Bucket
- Search for and select S3 your AWS Console. 
- Select the `team-template-awsconfig` bucket; you should see a bucket prefixed with `team-template-awsconfig.` 
- Click on `Properties.` See example below

![image_tag](/static/10_awsaddon/setup_aws/Image_9.png) 


- Scroll down until you get to the Event Notifications section and select `Create Event Notification` 


![image_tag](/static/10_awsaddon/setup_aws/Image_10.png) 


- In the Create event notification panel under General Configuration, `enter the Event Name` as `SplunkWorkshopEventNotification`
- Under Event types, select `All object create events`


![image_tag](/static/10_awsaddon/setup_aws/Image_11.png) 


- Scroll down and under Destination, select `SQS Queue` 
- Select the SQS queue `SplunkWorkshopQueue`  
- Click `Save Changes` once done.


![image_tag](/static/10_awsaddon/setup_aws/Image_12.png) 

>[!IMPORTANT]
>If you get an error like the screenshot below when clicking save changes then you have an issue with your SQS primary queue access policy. Go back to your primary SQS queue and edit the access policy. Re-check your steps earlier in this lab and make sure you edited the 4 required sections in the access policy correctly.

![image_tag](/static/10_awsaddon/setup_aws/setups3notification-errorscreenshot.png)

#### Congratulations, you have setup the S3 Event Notifications successfully. Lets move on to next step to setup SQS-based-S3 input on Splunk Add-on

### Click <a>[Next](/content/Lab1_awsaddon/setup_add_on.md)</a> to continue or click <a>[Back](/content/Lab1_awsaddon/setup_aws_sqs.md) to go back to the previous page</a>