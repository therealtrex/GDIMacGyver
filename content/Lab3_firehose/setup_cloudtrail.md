# This part of the lab will setup a CloudTrail to start streaming logs to CloudWatch and S3. 
This lab will take you through setting up a CloudTrail trail to stream management activity to S3 and CloudWatch for ingestion into Splunk later on using Amazon Data Firehose.

## Create an S3 Bucket for CloudTrail logs
- From the AWS console search for and `select S3`

![image006](/static/20_firehose/Image006.png)

- From the S3 menu select `Create Bucket`
- Select your `AWS region` as the current region where you are doing this workshop. Not sure? Ask your instructor. (Example: `us-west-1`)
- The bucket name has to be unique. Enter bucket name as `cloudtrail-<aws-region>-<aws-account-number>` 

    Example: If your region is us-west-1 and your AWS account id is 123456789012 then enter `cloudtrail-us-west-1-123456789012` as bucket name. Example below.

![image007](/static/20_firehose/Image007.png)

- Leave remaining defaults and click `Create Bucket`

## Create CloudTrail Management Trail
- From the AWS console search for and select `CloudTrail`

![image008](/static/20_firehose/Image008.png)

- From the CloudTrail menu select `Create trail`
- Name your trail as: `cloudtrail-management-<aws-region>-<aws-account-number>`
- Select the `Use existing S3 bucket` radio button
- Click `browse` and select the bucket you created above

![image009](/static/20_firehose/Image009.png)

- Leave `Prefix` empty
- Leave `Enabled` checked for `SSE-KMS encryption`
- Select `New` for `Customer Managed AWS KMS Key`
- Enter a name for the `AWS KMS Key` as: `cloudtrail-management-<aws-region>-<aws-account-number>-KMS`

![image010](/static/20_firehose/Image010.png)

- Select `Enabled` for CloudWatch Logs. 
- Select `Existing` for Log Group
- Paste `CloudTrail/SplunkGDIWorkshopCTrailLogGroup` into your CloudWatch Log group 
- For IAM Role, select `Existing`
- Select the role name of `SplunkGDIWorkshopCTrailLogGroupRole` from the drop down list.

![image011](/static/20_firehose/Image011.png)

- Leave remaining defaults and `click Next`
- Leave defaults for `Choose Log Events (Management events only)` and click `Next`
- Review and click `Create Trail`

## Verify CloudTrail CloudWatch log group is working
- From your AWS console, search for and select `CloudWatch`

![image012](/static/20_firehose/Image012.png)

- Select `Logs`, then `Log Groups` from the left hand menu
- Select the `Log group` mentioned earlier `CloudTrail/SplunkGDIWorkshopCTrailLogGroup`
- Confirm there is `at least one Log Stream` in that Log group. Explore this if you wish. 
- If you `refresh` the `log streams after a few minutes` you should have multiple streams with log data now

![image013](/static/20_firehose/Image013.png)

#### Congratulations on completing this part of the lab. Now that CloudTrail is configured correctly, we will move onto creating the Firehose Stream to Splunk.

### Click <a>[Next](/content/Lab3_firehose/setup_firehose.md)</a> to continue or click <a>[Back](/content/Lab3_firehose/setup_splunk.md) to go back a page.</a>