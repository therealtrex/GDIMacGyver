# Setup VPC Flow Logs to output to CloudWatch in order to stream into Splunk
In this Lab we will setup VPC Flow logs in a VPC with CloudWatch Logs as a destination. This will then be used later to stream into Splunk using Lambda.

## Create VPC Flow Logs
- Go to AWS [console](https://console.aws.amazon.com/vpcconsole/home) and search for and select `VPC`
- on the VPC dashboard Select `Your VPCs` on the left hand side.
- Select the `VPC ID` for your VPC Named `SplunkWorkshopVPC` VPC where we will create the Flow logs.
- Go to `Flow logs` tab for the VPC and click `Create flow log`

![physicalid](/static/30_lambda/vpc_console.png)

- Give the name to the FlowLog as `SplunkVPCFlowLog`
- Select the `Maximum aggregation interval` to `1 minute`
- Under `Destination` make sure `Send to CloudWatch Logs` is selected. 
- For Destination log group, select the pre-created `SplunkGDIWorkshopFlowLogGroup` log group.
- Under IAM role, select the pre-created `SplunkGDIWorkshopFlowLogGroupRole` IAM Role.
- Leave remaining defaults and click `Create flow log`.

## Verify VPC Flow logs in CloudWatch
- Search for and select `CloudWatch` from your AWS [console](https://console.aws.amazon.com/cloudwatch/home) 
- Under Logs, Logs Groups, select `SplunkGDIWorkshopFlowLogGroup`
- You should see Log streams for VPC Flow logs created in the CloudWatch Log Group. Select one of the log streams and you can see the VPC Flow log records.
  
![flowlogrecords](/static/30_lambda/flowlogrecords.png)

#### Congratulations on completing this part of the lab. Now we have VPC flow logs putting logs in CloudWatch we can setup a subscription filter to trigger off our Lambda function.

### Click <a>[Next](/content/Lab3_lambda/setup_lambda.md)</a> to continue or click <a>[Back](/content/Lab3_lambda/setup_splunk.md) to go back a page.</a>