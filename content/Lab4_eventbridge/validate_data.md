# Validate Eventbridge data streaming into Splunk
Its time to now validate that the Amazon EventBridge data is flowing into Splunk.

>[!NOTE]
>As mentioned earlier Eventbridge data from Amazon GuardDuty can take up to 15 minutes too appear in Splunk due to the fequency of when the data is logged in Amazon Guard Duty.

- From your Splunk Console, `select Apps` followed by `Search and reporting`
- From the Search bar enter in the search below:

```text
    index=aws-data sourcetype="aws:cloudwatch:guardduty"
```

>[!NOTE]
>You can leave the default time picker at last 24 hours or feel free to adjust to something smaller

![splunkguardduty](/static/40_eventbridge/splunk_guardduty.png)


##### Congratulations! You have now sucessfully configured Amazon Guard Duty logs through Amazon Eventbridge into Splunk. This lab is now complete.

### Click <a>[HOME](/README.md)</a> to now choose another lab or click <a>[Back](/content/Lab4_eventbridge/setup_rule.md) to go back to the previous page</a>