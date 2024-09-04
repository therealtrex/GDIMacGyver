---
title: "Lab 3.3 - Setup Splunk Add-on for AWS"
chapter: true
weight: 43
---


## Overview
In this lab you will set up the Splunk Add-on for AWS to begin ingesting data into Splunk. 

### Obtain AWS IAM User Credentials for Splunk Add-on for AWS to use
- In a new tab from your AWS console. Search for and **Secrets Manager**
- From the Secrets page select **SplunkSecrets**
- From the Secret value section select the button **Retrieve secret value**


![image_tag](/static/10_awsaddon/setup_addon/Image_10.png)

- Leave this tab open or copy the **accesskey** and **secretkey** somewhere to use for later

### Configure Splunk Add-on for AWS
- Navigate to your Splunk environment and log into Splunk.  
- From the Splunk home screen **select Splunk Add-on for AWS** located on the left navigation bar.


![image_tag](/static/10_awsaddon/setup_addon/Image_1.png)


- Navigate to the **Configuration** tab and click **Add** to add a new AWS account to the Add-on. 


![image_tag](/static/10_awsaddon/setup_addon/Image_2.png)


*Enter the following information to the **Add Account** window*:

- Enter a name of: `SplunkWorkshopAWS`
- Paste in the **Key ID** and **Secret Key** copied earlier from AWS Secrets Manager
- Leave Region Category as Global and **click Add** when done.

You should now see a new configuration named **SplunkWorkshopAWS**

![image_tag](/static/10_awsaddon/setup_addon/Image_3.png)


### Add Metadata Input
Navigate to the **Inputs** tab and click **Create New Input** and select **Metadata**. 


![image_tag](/static/10_awsaddon/setup_addon/Image_4.png)


- On the Add Metadata screen enter in a name of: `SplunkWorkshopMetadata`
- Select the **SplunkWorkshopAWS account** from the list you created earlier.
- From AWS Regions select **US East (N. Virginia)**
- Under APIs/Internal (in seconds), select **Clear All**
- Expand the **EC2 arrow** and **select all EC2 options** while also changing the **frequency from 3600 to 300**

![image_tag](/static/10_awsaddon/setup_addon/Image_5.png) 

- Leave sourcetype as aws:metadata and change the index to `aws-data`

![image_tag](/static/10_awsaddon/setup_addon/Image_6.png)

- Click **Add** when done.

::alert[AWS EC2 Metadata is now being sent to Splunk. We will validate this later on in the lab.]{header="Note"}


### Add Config Input
Next we want to configure AWS Config input. 
- From the **Inputs** tab, click **Create New Input** and select **Config > SQS-Based-S3**. 


![image_tag](/static/10_awsaddon/setup_addon/Image_7.png)

- Enter in the Name of: `SplunkWorkshopConfig`
- Select the same account we selected earlier: **SplunkWorkshopAWS**
- Select **US East (N. Virginia)** as the AWS Region setting. 
- Under SQS Queue Name, select `SplunkWorkshopQueue` that we created earlier. 
- **Untick** the **Signature Validate All Events** option
- Set the index as `aws-data`
- Leave remainng defaults and click **Add**



![image_tag](/static/10_awsaddon/setup_addon/Image_8.png)


 Your inputs page should look like this:

![image_tag](/static/10_awsaddon/setup_addon/Image_9.png)

##### Congratulations! You have completed setting up your Splunk Add-on for AWS. AWS Config data & Instance Metadata have now been added and is being sent to Splunk. Proceed to the next part of the lab to validate Splunk is receiving data from AWS. 