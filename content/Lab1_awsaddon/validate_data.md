# Validate our data coming into Splunk
In this lab you will validate if the data is ingested & indexed into Splunk successfully from AWS Add-on input you created earlier.

- From the `Splunk Add-on for AWS`, click the `Search` tab
- From the Search bar enter in the search below and click the search button:

```text
    index="aws-data" sourcetype="aws:config" OR sourcetype="aws:metadata"
```

>[!NOTE]
>You can leave the default time picker at last 24 hours or feel free to adjust to something smaller

![image_tag](/static/10_awsaddon/validate_data/Image_1.png)


- Verify that there are *2* sourcetypes that appear in the search results. The sourcetypes are:
    `aws:metadata`
    `aws:config`

![image_tag](/static/10_awsaddon/validate_data/Image_2.png)

>[!TIP]
>If you are having issues with not seeing noth sourcetypes then check which one  you are missing and go back to the part of the lab which they were setup to check your steps again. For S3 notifications you can check the SQS queues to see if there is messages in flight. The _internal index for Splunk can also help you check the status of indexing logs for SQS based S3 inputs. Ask your instructor how to do this. 

##### Congratulations! You have now sucessfully completed this lab! You configured your Splunk Add-on for AWS and have EC2 instance metadata & AWS Config data coming in Splunk using the PULL method. 

### Click <a>[HOME](/README.md)</a> to now choose another lab or click <a>[Back](/content/Lab1_awsaddon/setup_add_on.md) to go back to the previous page</a>