# Setting up Amzaon S3 Event Notrification
In this part of the lab you will be adding event notifications to an existing Amazon S3 bucket. This will be used by the Splunk Add-on for AWS to ingest the AWS Config Data. 

### Setup Event Notification for Amazon S3 Bucket
- Search for and select S3 your AWS Console. 
- Select the `team-template-awsconfig` bucket; you should see a bucket prefixed with `team-template-awsconfig.` 
- Click on `Properties.` See example below

![image_tag](/static/10_awsaddon/setup_aws/Image_9.png) 


- Scroll down until you get to the Event Notifications section and select Create `Event Notification` 


![image_tag](/static/10_awsaddon/setup_aws/Image_10.png) 


- In the Create event notification panel under General Configuration, `enter the Event Name` as `SplunkWorkshopEventNotification`
- Under Event types, select `All object create events`


![image_tag](/static/10_awsaddon/setup_aws/Image_11.png) 


- Scroll down and under Destination, select `SQS Queue` 
- Select the SQS queue `SplunkWorkshopQueue`  
- Click `Save Changes` once done.


![image_tag](/static/10_awsaddon/setup_aws/Image_12.png) 

>[!NOTE]
>In the next section we will obtain the AWS IAM user credentials which have been pre-configured to use for the Splunk AWS add-on. This user has the required policies attached to interact with AWS services we need for these labs. For more information on Splunk required policies/permissions see <a>[HERE](https://splunk.github.io/splunk-add-on-for-amazon-web-services/ConfigureInputs/) </a>

### Obtain AWS Credentials to Configure Splunk Add-on for AWS

- In the AWS Console search for the `Secrets Manager` service. 
- Click on the `SplunkSecrets` secret name. 

![image_tag](/static/10_awsaddon/setup_aws/Image_13.png) 

- Click on `Retrieve Secret Value`

![image_tag](/static/10_awsaddon/setup_aws/Image_14.png) 

- Copy the `accesskey` & `secretkey` somewhere (eg notepage). These will be used in the next lab to configure your Splunk Add-on for AWS. 

![image_tag](/static/10_awsaddon/setup_aws/Image_15.png) 


##### Congratulations, you have setup the S3 Event Notifications successfully. Lets move on to next step to setup SQS-based-S3 input on Splunk Add-on

### Click <a>[Next](/content/Lab1_awsaddon/setup_add_on.md)</a> to continue or click <a>[Back](/content/Lab1_awsaddon/setup_aws_sqs.md) to go back to the previous page</a>