# Validate CloudTrail data streaming into Splunk
Its time to now validate that the streaming Amazon Data Firehose data for CloudTrail is coming into Splunk.

- From your Splunk Console, `select Apps` followed by `Search and reporting`
- From the Search bar enter in the search below:

```text
    index="aws-data" sourcetype="aws:cloudtrail"
```

>[!NOTE]
>You can leave the default time picker at last 24 hours or feel free to adjust to something smaller

![image004](/static/20_firehose/Image024.png)

##### Congratulations! You have now sucessfully configured your Splunk Add-on for AWS and have instance metadata & AWS Config data in Splunk. 

### Click <a>[HOME](/README.md)</a> to now choose another lab or click <a>[Back](/content/Lab2_firehose/setup_cloudwatch_subscriptionfilter.md) to go back to the previous page</a>