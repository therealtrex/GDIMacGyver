# Create a HEC token to use for EventBridge
This first part of the lab will take you through configuring a Http Event Collector (HEC) token to use with Amazon Eventbridge.

>[!NOTE]
>You already have a Splunk index `aws-data `for storing your AWS data so we won't need to create one for this lab.

### Creating a Splunk HEC toekn for EventBridge
- From your Splunk Console select `Settings, Data Inputs`
- Select `HTTP Event Collector`
- Select `New Token`
- Give your HEC token a name Example: `eventbridge-hec`
- Leave Enable Indexer Acknowledgement `Unticked`

![image004](/static/40_eventbridge/create-hec.png)

>[!NOTE]
>For this lab we will NOT be using the HEC acknowlegement feature. Turning this on may cause the lab to fail sending data to Splunk.

- Leave remaining defaults and click `next` at the top of the screen. 
- For sourcetype click `select` and then click `Select Source Type`
- Select `aws:cloudwatch:guardduty`
- In the index section select the index `aws-data` you for your AWS data. 
- Click `review`, check over your steps.

![image004](/static/40_eventbridge/create-hec-2.png)

Click `Submit` to create HEC token.
Now `Copy your HEC token to use later`

![image005](/static/40_eventbridge/Image005.png)

- Lastly, `copy` your `Splunk Cloud URL` to use later eg scv-shw-87bea8f2733e0f.stg.splunkcloud.com

##### Congratulations on completing this part of the lab. Now we have a Splunk index for storing data and a HEC token we can move onto AWS to start configuring our services there.

### Click <a>[Next](/content/Lab4_eventbridge/setup_target.md)</a> to continue or click <a>[Back](/content/Lab4_eventbridge/index.en.md) to go back a page.</a>