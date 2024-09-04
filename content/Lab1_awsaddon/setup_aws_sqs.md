# Setting up SQS
In this part of the lab you will be setting up and configuring Amazon Simple Queue Service (SQS) queues. These will be used by the Splunk Add-on for AWS to ingest the AWS Config Data. 


### Step One: Setup Dead Letter Amazon SQS Queue (DLQ)

>[!TIP]
>HOT TIP: I tend to setup my Dead Letter Queue first as this saves time when setting up the primary queue later as you can assign its DLQ at the same time when creating!  

- In your AWS Console navigate to the `Simple Queue Service` and click `Create Queue.`
- From the Create Queue section `enter the name` of your SQS queue as `SplunkWorkshopDeadLetterQueue`

![](/static/10_awsaddon/setup_aws/Image_1.png)

- Under the configuration section set `visability timeout` to `5 minutes`
- Leave remaining defaults and click `Create Queue`

![image_tag](/static/10_awsaddon/setup_aws/Image_2.png)


### Step Two: Setup primary Amazon SQS Queue

>[!IMPORTANT]
>Before we setup our primary SQS queue. We need to copy the S3 bucket ARN where our Config files are being sent.

- From AWS console in a `new TAB` search for and select `S3.`  
- Search for our AWS Config bucket by entering in `team-template-awsconfig` in the search bar. 

![s3_bucket](/static/10_awsaddon/setup_aws/s3_bucket.png)

- Click the bucket name and then select the `Properties` tab. 
- `Copy the ARN` of the S3 bucket somewhere (eg notepad) to use in the SQS Access Policy later.

![s3_bucketarn](/static/10_awsaddon/setup_aws/s3_bucketarn.png)

- From our SQS tab earlier, select `Queues` followed by `Create queue` to create our primary SQS Queue.
- Name this queue `SplunkWorkshopQueue`

![image_tag](/static/10_awsaddon/setup_aws/Image_6.png)

- Same as before, in the configuration section set the `timeout to 5 minutes.`

![image_tag](/static/10_awsaddon/setup_aws/Image_2.png) 

- Scroll down to the `Accesss Policy` section to modify the default access policy for this SQS queue. 
- `Select Advanced` for Access Policy Method. 
- Input the following JSON Policy below making sure to insert the `<AWS account ID>` (in two sections) and `<S3 Bucket ARN>` you copied above.

>[!TIP]
>You can copy your account id by selecting the drop down arror top right hand side of your AWS console. Then click the copy button next to the Account ID:<xxxx-xxxx-xxxx>

```json
{
  "Version": "2012-10-17",
  "Id": "example-ID",
  "Statement": [
    {
      "Sid": "example-statement-ID",
      "Effect": "Allow",
      "Principal": {
        "Service": "s3.amazonaws.com"
      },
      "Action": "SQS:SendMessage",
      "Resource": "arn:aws:sqs:us-east-1:<Insert-Account-ID>:SplunkWorkshopQueue",
      "Condition": {
        "StringEquals": {
          "aws:SourceAccount": "<Insert-Account-ID>"
        },
        "ArnLike": {
          "aws:SourceArn": "<Insert your S3 bucket ARN>"
        }
      }
    }
  ]
}
```
- Once completed it should look like the image below.

![image_tag](/static/10_awsaddon/setup_aws/Image_7.png) 

- Next in the section for Dead-letter queue `Select enabled`
- Click the drop down and `select the dead letter queue` you creted earlier. 
- Leave remaining defaults and click `Create Queue`

![image_tag](/static/10_awsaddon/setup_aws/Image_8.png) 

- Once created you should now have two SQS queues created. 

### Congratulations, you have setup the SQS Queue successfully as the 1st step for the SQS-based-S3 Add-On Input. Lets move on to next lab to setup S3 Event Notifications

### Click <a>[Next](/content/Lab1_awsaddon/setup_aws_s3.md)</a> to continue or click <a>[Back](/content/Lab1_awsaddon/index.en.md) to go back to the previous page</a>