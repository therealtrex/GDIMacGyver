# Setting up SQS
In this part of the lab you will be setting up and configuring Simple Queue Service (SQS) Queues. These will be used by the Splunk Add-on for AWS to ingest the AWS Config Data. 


### Setup Dead Letter Queue
- In your AWS Console navigate to the <code style="color : cyan">Simple Queue Service</code> and click <code style="color : cyan">Create Queue.</code>
- From the Create Queue section <code style="color : cyan">enter the name</code> of your SQS queue as <code style="color : cyan">SplunkWorkshopDeadLetterQueue</code>

![](/static/10_awsaddon/setup_aws/Image_1.png)

- Under the configuration section <code style="color : cyan">set visability timeout to 5 minutes</code>
- Leave remaining defaults and <code style="color : cyan">click Create Queue</code>

![image_tag](/static/10_awsaddon/setup_aws/Image_2.png)


### Setup second Amazon SQS Queue

::alert[Before we setupo our second SQS queue. We need to copy the S3 bucket ARN where our Config files are being sent.]{header="Note"}

- From AWS console in a **new TAB** search for and **select S3**.  
- Search for our AWS Config bucket by entering in **team-template-awsconfig** to the search bar. 

![s3_bucket](/static/10_awsaddon/setup_aws/s3_bucket.png)

- Click this bucket name followed by the **Properties** tab. 
- Copy the ARN of the S3 bucket to use in the Access Policy later.

![s3_bucketarn](/static/10_awsaddon/setup_aws/s3_bucketarn.png)

- From our other SQS tab earlier, select **Queus** followed by **Create queue** to create another SQS Queue from the SQS page in the AWS Console
- Name this queue `SplunkWorkshopQueue`

![image_tag](/static/10_awsaddon/setup_aws/Image_6.png)

- Under configuration **set the timeout to 5 minutes**.

![image_tag](/static/10_awsaddon/setup_aws/Image_2.png) 

- Scroll down to the **Accesss Policy** section to modify the default access policy for this SQS queue. 
- **Select Advanced** for Access Policy Method. 
- Input the following JSON Policy and *insert* the **AWS account ID** (in two sections) and **S3 Bucket ARN** you copied above

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

- Under Dead-letter queue **Select enabled**
- Click the drop down and **select the dead letter queue** we creted earlier in the lab. 
- Leave remaining defaults and **click Create Queue**

![image_tag](/static/10_awsaddon/setup_aws/Image_8.png) 

- Once created you should now have two SQS queues created. 

##### Congratulations, you have setup the SQS Queue successfully as the 1st step for the SQS-based-S3 Add-On Input. Lets move on to next lab to setup S3 Event Notifications