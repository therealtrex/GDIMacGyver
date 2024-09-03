---
title: "Lab 2.2 - Setup Lambda Function"
chapter: true
weight: 31
---

## Overview
In this lab we will setup the Lambda function and configure VPC Flow Logs to ingest into Splunk. 

### Deploy Splunk Lambda Processor - Serverless Application
For this workshop, we developed a serverless application called **splunk-aws-lambda-cloudwatchlogs-processor**.  
- To deploy this application, go to AWS [console](https://console.aws.amazon.com/serverlessrepo/home?/available-applications) Serverless Application Repository 
- Select **Available applications** 
- Search for `splunk-aws-lambda-cloudwatchlogs-processor` under **Public applications** and select the application to deploy.

![lambda_serverless](/static/30_lambda/serverless.png)

- Under the **Application settings**, enter only the following parameters and leave the rest to default values:
    -  **SplunkSourceType**: Enter source type `aws:cloudwatchlogs:vpcflow` for VPC Flow Logs.
    -  **ELBCookieName**: Enter `AWSELB` for ELB cookie name.
    -  **SplunkHttpEventCollectorToken**: Enter your HEC token created in previous steps, or create a new HEC token for Lambda and enter the value.
    -  **SplunkHttpEventCollectorURL**: Enter the Endpoint URL for Splunk. 
  
::alert[Include the indexer port 8088 if you use Splunk Show instance. Ex: `https://i-instanceid.splunk.show:8088`]{header="Note"}  

![parameters](/static/30_lambda/parameters.png)

- Once the application settings parameters are filled as above, click **Deploy** to deploy this application. 
- Once deployed, you will be taken to Lambda Applications home page, where you can get the logical and physical id of the lambda function under **Resources**. **Copy the physical id** of the Lambda function, you will require this in next step.

![physicalid](/static/30_lambda/physical_id.png)

::alert[You can verify your deployment worked correctly by selecting the **Deployments** tabe and checking under the deployment history is says **Create complete**. If this has failed you will need to verify why it failed and try again.]{header="Note"}  