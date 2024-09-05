# Setup the CloudWatch subscription filter to trigger a Lambda function
In this part of the lab we will configure a subscription filter to trigger off our Lambda function (which will send logs to Splunk) when new logs arrive in the log group. 

## Create CloudWatch Subscription Filter
- From your AWS [console](https://console.aws.amazon.com/serverlessrepo/home?/available-applications) search for and select CloudWatch
- From the left hand side select `Logs` and `Log Groups`
- Select your `SplunkGDIWorkshopFlowLogGroup` log group. 
- Select the `Subscription filters` tab.
- Click the `Create pull down` menu and select `Create Lambda subscription filter`
  
![subfilter](/static/30_lambda/subfilter.png)

- Select the Lambda function you created in previous lab, `by matching the physical id`.
- Name the subscription filter `SplunkVPCSubFilter`
- Leave remaining defaults and Click `Start streaming`.

##### Congratulations on completing this part of the lab. All that is left it to now verify the data in Splunk!

### Click <a>[Next](/content/Lab3_lambda/validate_data.md)</a> to continue or click <a>[Back](/content/Lab3_lambda/setup_lambda.md) to go back a page.</a>