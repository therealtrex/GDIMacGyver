# Create a Amazon Data Firehose to stream CloudTrail logs.
In this part of the lab we will setup the Amazon Data Firehose to stream CloudTrail logs to Splunk from CloudWatch. 

## Create Amazon Data Firehose
- From your AWS console search for and select `Amazon Data Firehose`

![image014](/static/20_firehose/Image014.png)

- From the Amazon Data Firehose page. Select `Create Firehose stream`
- From the Source drop down select `Direct PUT` 

>[!TIP]
>The PUT method here is used when we are using logs from a native AWS service Eg CloudWatch.


- In the Destination drop down scroll down and select `Splunk` (Not the observability one!)
- Name your delivery stream as : `SplunkWorkshopDeliveryStream`
- Under the `transform` section, check the options for  `Turn on decompression` and `Turn on Message Extraction`


![image015](/static/20_firehose/Image015.png)

![image016](/static/20_firehose/Image016.png)

- In destination settings. Enter your `Splunk cluster endpoint.`

>[!IMPORTANT]
>Include the indexer port 8088 if you use Splunk Show instance. Ex: `https://i-instanceid.splunk.show:8088`

- Leave `RAW endpoint` selected.
- Paste in your `HEC token` copied earlier into the `Authentication token field.`

>[!NOTE]
>You can check this by checking the Show Token option.


![image017](/static/20_firehose/Image0172.png)

- Leave HEC acknowledgement timeout settings as they are
- Click the expand arrow under `Buffer hints`
- Enter in `1MiB` and `0 seconds` for the buffer

![image023](/static/20_firehose/Image023.png)

- For `backup settings` leave `failed events only` selected
- Select `browse` and select the bucket `splunk-backup-bucket-\<Your AWS Account NUMBER\>` for a `failed events`

![image018](/static/20_firehose/Image018.png)

- `Expand` the `Advanced settings` section 
- Under Service Access, `select the radio for Choose existing IAM role.`
- Select the pre-configured role called `SplunkGDIWorkshopFirehoseRole`
- `Leave remaining defaults` and click `Create Firehose stream.`

##### Congratulations on completing this part of the lab. Now that Amazon Data Firehose is setup. We can setup a CloudWatch subscription filter to use this new Firehose stream. 

### Click <a>[Next](/content/Lab2_firehose/setup_cloudwatch_subscriptionfilter.md)</a> to continue or click <a>[Back](/content/Lab2_firehose/setup_cloudtrail.md) to go back a page.</a>