# Setup the Splunk add-on for AWS
In this lab you will set up the Splunk Add-on for AWS to begin ingesting data into Splunk from AWS using the SQS based S3 and Meta Data API calls

>[!NOTE]
>You will have noticed up until this point we have not configured anything in AWS in regards to the Ec2 Metadata. This is because we will us a direct API PULL request to the AWS ec2 machine using our AWS IAM user. 

### Obtain AWS IAM User Credentials for Splunk Add-on for AWS to use
- In a new tab from your AWS console. Search for and `Secrets Manager`
- From the Secrets page select `SplunkSecrets`
- From the Secret value section select the button `Retrieve secret value`


![image_tag](/static/10_awsaddon/setup_addon/Image_10.png)

- Leave this tab open or copy the `accesskey` and `secretkey` somewhere to use for later

### Configure Splunk Add-on for AWS
- In a new tab navigate to your Splunk environment and log into Splunk.  
- From the Splunk home screen select `Splunk Add-on for AWS` located on the left navigation bar. See example below.


![image_tag](/static/10_awsaddon/setup_addon/Image_1.png)


- Navigate to the `Configuration` tab and click `Add` to add a new AWS account to the Add-on. 


![image_tag](/static/10_awsaddon/setup_addon/Image_2.png)


In the add account window enter the following information:
- Enter a name of: `SplunkWorkshopAWS`
- Paste in the `Key ID` and `Secret Key` copied earlier from AWS Secrets Manager
- Leave Region Category as Global.
- click `Add` when done.

You should now see a new configuration named `SplunkWorkshopAWS`. See example below.

![image_tag](/static/10_awsaddon/setup_addon/Image_3.png)


### Add Metadata Input
- Navigate to the `Inputs` tab 
- Click `Create New Input` and select `Metadata`. 


![image_tag](/static/10_awsaddon/setup_addon/Image_4.png)


- On the Add Metadata screen enter in a name of: `SplunkWorkshopMetadata`
- Select the `SplunkWorkshopAWS` account you created earlier.
- From AWS Regions select the `region` you are using for this lab (not sure? Ask your instructor) eg US West (N. California) us-west-1.
- Under APIs/Internal (in seconds), select `Clear All`
- Expand the `EC2 arrow` and `select all EC2 options` while also changing the `frequency from 3600 to 300`. See example below

![image_tag](/static/10_awsaddon/setup_addon/Image_5.png) 

- Leave sourcetype as aws:metadata and change the index to `aws-data`

![image_tag](/static/10_awsaddon/setup_addon/Image_6.png)

- Click `Add` when done.

>[!NOTE]
>AWS EC2 Metadata is now being sent to Splunk. We will validate this later on in the lab.


### Add Config Input
Next we want to configure AWS Config input. 

- From the `Inputs` tab, click `Create New Input` and select `Config > SQS-Based-S3`. 


![image_tag](/static/10_awsaddon/setup_addon/Image_7.png)

- Enter in the Name of: `SplunkWorkshopConfig`
- Select the same account we selected earlier: `SplunkWorkshopAWS`
- Select the same `region` we used in the previous step for EC2 metadata. eg US West (N. California) us-west-1. 
- Under SQS Queue Name, select `SplunkWorkshopQueue` that we created earlier. 
- `Untick` the `Signature Validate All Events` option
- Set the index as `aws-data`
- Leave remainng defaults and click `Add`

>[!IMPORTANT]
>If you do not untick signature validation all events here then you will get issues and no data coming in later. 

>[!TIP]
>If you are trying this on your own and you get an error during this step it most likely will be because your IAM user premissions are incorrect and Splunk cannot authenticate to SQS and S3.

![image_tag](/static/10_awsaddon/setup_addon/Image_8.png)

 Your inputs page should look like this:

![image_tag](/static/10_awsaddon/setup_addon/Image_9.png)

>[!IMPORTANT]
>Well done on setting up your two inputs. Just a reminder in case you didn't read this earlier. AWS config does not log frequently! AWS Config has two logging pieces. The configuration recorder and configuration snapshots. The Recorder when setup in continuous mode does continuous recording but will only log to S3 every six hours. The configuration snapshot capability of AWS Config will log to S3 on either a 1,3,6,12 or 24 hour frequewcy (we have setup 1hr for this lab). This means during this lab you may have to wait for a full hour to see anythign in Splunk. It is recommended you completed the lab and then we will check on it later during the day to make sure logs are coming in ok. More Info on this <a>[HERE](https://aws.amazon.com/blogs/mt/configuration-history-configuration-snapshot-files-aws-config/)</a>.


#### Congratulations! You have completed setting up your Splunk Add-on for AWS. AWS Config data & Instance Metadata have now been added and is being sent to Splunk. Proceed to the next part of the lab to validate Splunk is receiving data from AWS. 

### Click <a>[Next](/content/Lab1_awsaddon/validate_data.md)</a> to continue or click <a>[Back](/content/Lab1_awsaddon/setup_aws_s3.md) to go back to the previous page</a>