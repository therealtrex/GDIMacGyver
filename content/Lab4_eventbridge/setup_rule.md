# Create a rule in Eventbridge to send data to the destination endpoint
In previous lab we setup Splunk as EventBridge Destination for our target. Lets now setup an EventBridge Rule to get all GuardDuty Events sent to Splunk

## Configure EventBridge Target & Connection for Splunk
- From your [AWS console](https://console.aws.amazon.com/events/home) search for and select `Amazon Eventbridge` 
- Select `Rules` under `Buses` on the left hand side.
- Click `Create Rule`.
- Enter the name for the Rule as `SplunkGuardDutyRule`, leave default values and Click `Next`.
- Leave `Event source` as `AWS events or EventBridge partner events`, scroll down to `Event Pattern`.
- From the Event Pattern section, `select the following`:
  - Select `AWS services` for `Event source`
  - Select `GuardDuty` for `AWS Service` 
  - Select `All Events` for `Event Type`

See example below

![event_selection](/static/40_eventbridge/eventbridge_eventselection.png)  

- Click `Next` and select `EventBridge API destination` as `Target Type`.
- Under `API Destination` check `Use an existing API destination` and select the `Splunk destination created earlier`
- Under `Execution Role`, select `Use existing role` and select the IAM Role `SplunkGDIWorkshopEventBridgeInvokeApiRole`

![target_selection](/static/40_eventbridge/eventbridge_targetselection.png) 

- Click `Next`. Enter any tags and Click `Next`.
- Review the configurations and `click Create rule` to create the rule.
  
![check_splunk](/static/40_eventbridge/splunk_guardduty.png)

##### Congrats you have now successfully created EventBridge destination for Splunk and a Rule to ingest GuardDuty Findings as events into Splunk. 

>[!NOTE]
>It may take up to 15 minutes to start recieving data into Splunk from Amazon GuardDuty. Feel free to continue onto next part of validation but data may not be present yet. 

### Click <a>[Next](/content/Lab4_eventbridge/validate_data.md)</a> to continue or click <a>[Back](/content/Lab4_eventbridge/setup_target.md) to go back a page.</a>