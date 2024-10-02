# Deploy a lambda function to stream logs to Splunk HEC endpoint
In this lab we will setup the Lambda function and configure VPC Flow Logs to ingest data into Splunk via the HEC endpoint. 

## Deploy Splunk Lambda Processor - Serverless Application
For this workshop, we developed a serverless application called `splunk-aws-lambda-cloudwatchlogs-processor`
- From your AWS [console](https://console.aws.amazon.com/serverlessrepo/home?/available-applications) search for and select `Serverless Application Repository`
- Select `Available applications` 
- Search for `splunk-aws-lambda-cloudwatchlogs-processor` under `Public applications` and `select the application` to deploy. See example below:

![lambda_serverless](/static/30_lambda/serverless.png)

- Under the `Application settings`, enter the following parameters:
    -  `SplunkSourceType`: Enter source type `aws:cloudwatchlogs:vpcflow` for VPC Flow Logs.
    -  `ELBCookieName`: Enter `AWSELB` for ELB cookie name.
    -  `SplunkHttpEventCollectorToken`: Enter your HEC token created earlier in the lab.
    -  `SplunkHttpEventCollectorURL`: Enter the Endpoint URL copied earlier for Splunk eg example `https://<splunkcloud-instanceid>.splunk.show:8088`
  
![parameters](/static/30_lambda/parameters.png)

- Once the application settings parameters are filled as above, click `Deploy` to deploy this application. 
- Once deployed, you will be taken to Lambda Applications home page, where you can get the logical and physical id of the lambda function under `Resources`. `Copy the physical id` of the Lambda function, you will require this in next step.

![physicalid](/static/30_lambda/physical_id.png)

>[!NOTE]
>You can verify your deployment worked correctly by selecting the `Deployments` tab and checking under the deployment history is says `Create complete`. If this has failed you will need to verify why it failed and try again.

#### Congratulations on completing this part of the lab. Now we have setup our lambda we can configure the subscription filter for VPC Flow logs log group to trigger the lambda function. 

### Click <a>[Next](/content/Lab4_lambda/setup_subscriptionfilter.md)</a> to continue or click <a>[Back](/content/Lab4_lambda/setup_flowlogs.md) to go back a page.</a>