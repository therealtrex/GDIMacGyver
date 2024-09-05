## Setting up Splunk for streaming of data. 
This first part of the lab will take you through configuring a Http Event Collector (HEC) token to use for Amazon Data Firehose

### Creating a Splunk HEC token for AWS data
- From your Splunk Console select `Settings, Data Inputs`
- Select `HTTP Event Collector`
- Select `New Token`
- Give your HEC token a name of: `cloudtrail-hec`
- Check `Enable Indexer Acknowledgement`

>[!IMPORTANT]
>Amazon Data Firehose has a feature inbuilt to check HEC data acknowledgement, if you do not enable indexer acknowledgement you will get an error when deploying Amazon Data Firehose.

- Leave remaining defaults and click `next` at the top of the screen. 
- For sourcetype click `select` and then click `Select Source Type`
- Select `aws:cloudtrail`
- In the index section select the index `aws-data` you for your AWS data. 
- Click `review`, check over your steps. It should look like the image below.

![image004](/static/20_firehose/Image004.png)

- Click `Submit` to create HEC token.
- `Copy your HEC token to use later` eg notepad. 

![image005](/static/20_firehose/Image005.png)

- Before moving onto the the next part of the lab. We want to get your Splunk URL. `Copy` your `Splunk Cloud URL` to use later eg scv-shw-87bea8f2733e0f.stg.splunkcloud.com

##### Congratulations on completing this part of the lab. Now we have a Splunk index for storing data and a HEC token we can move onto AWS to start configuring our services there.

### Click <a>[Next](/content/Lab2_firehose/setup_cloudtrail.md)</a> to continue or click <a>[Back](/content/Lab2_firehose/index.en.md) to go back a page.</a>