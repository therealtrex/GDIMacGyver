# Validate VPC Flow log data streaming into Splunk
Its time to now validate that the streaming VPC Flow log data for our Lambda function is coming into Splunk.

- From your Splunk Console, `select Apps` followed by `Search and reporting`
- From the Search bar enter in the search below:

```text
index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow"
```

>[!NOTE]
>You can leave the default time picker at last 24 hours or feel free to adjust to something smaller

![splunkflowlog](/static/30_lambda/splunkflowlog.png)

#### Congratulations! You have now sucessfully configured VPC Flow logs to send data to Splunk using a Lambda function. This lab is now complete. 

### Click <a>[HOME](/README.md)</a> to now choose another lab or click <a>[Back](/content/Lab4_lambda/setup_subscriptionfilter.md) to go back to the previous page</a>