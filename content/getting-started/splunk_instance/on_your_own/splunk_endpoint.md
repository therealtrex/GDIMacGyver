---
title : "Step 4:  Splunk Endpoint URL"
weight : 1300
---


## Overview

In this section, we will setup a AWS Elastic Load Balancer and place Splunk instance behind the load balancer for data ingestion. This step also creates a DNS name for Splunk end point to serve as destination for the Firehose and Lambda workshop.

## Step 4 – Setup Classic Load Balancer

- When you create the CloudFormation stack in Step 2, you should have a CA certificate created by AWS Certificate Manager (ACM). Go to ACM dashboard in [AWS console](https://console.aws.amazon.com/acm/home), expand the left side panel and click **List certificates**. Verify if the certificate is in Issued state. You should see the certificate created in *<Your AWS Account ID>.splunk.parner.aws.dev* as the domain name.
![architecture](/static/10_prerequisites/splunk_endpoint/acm.png)
- Click [Launch Stack](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=SplunkGDIWorkshopELBStack&templateURL=https://ws-assets-prod-iad-r-iad-ed304a55c2ca1aee.s3.us-east-1.amazonaws.com/5039b0de-622d-4224-8760-d9dff0c13e0b/SplunkFirehoseLabELBModule_Latest.yml) to launch Cloudformation stack creation and click **Next**.
- For the **SplunkInstanceStack** parameter value, enter the cloudformation stack name for the stack you created in Step 2 (If you did not change the value in Step 2, then the stack name should be **SplunkGDIWorkshopStack**).
![architecture](/static/10_prerequisites/splunk_endpoint/cftstackname.png)
- Click **Next**, click **Next**  and create the stack. It should take about a minute to create this stack.
- Once the stack status is **CREATE_COMPETE**, go to **Outputs** tab and verify you can see values **SplunkEndpointURL** and **SplunkELBDNSName**. You should see the SplunkFirehoseURL in the below format:
  - `https://<AWSAccountId>.splunk.partner.aws.dev`
![architecture](/static/10_prerequisites/splunk_endpoint/cftoutputs.png)
- This endpoint URL is created for this workshop to resolve for the Load balancer DNS name. The CA certificate you verified in previous step above, is installed on the Load balancer. This setup will meet the firehose requirements for public endpoint with valid CA certificate installed.
- Now go to your desktop terminal and check if the Endpoint URL is resolved to the Load balancer DNS name. You can use commands like `dig`. Example below shows a dig command resolving the Endpoint URL to the **SplunkELBDNSName** you got from above step. (If it doesn’t resolve to any names, wait for few minutes and try again).
  
![dig](/static/10_prerequisites/splunk_endpoint/dig.png) 

- If you are using Windows desktop, use `nslookup` command in command prompt to check the domain name (See below).
![architecture](/static/10_prerequisites/splunk_endpoint/nslookup.png)  

- You can now send some sample data over this endpoint using curl command to check if the endpoint works.
```curl
curl https://<Your AWS Account ID>.splunk.partner.aws.dev/services/collector -H "Authorization:Splunk <HEC Token>" -d '{"sourcetype": "mysourcetype", "event":"Hello, World!"}'
```
- Congratulations, you have now a Splunk Instance and an endpoint URL setup for the Firehose and Lambda workshop. Copy and use this **SplunkEndpointURL** for the Firehose and Lambda workshops.
