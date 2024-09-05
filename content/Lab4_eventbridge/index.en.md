# Setup Eventbridge to send Amazon GuardDuty logs to Splunk using native EventBrirdge PUSH method
In this workshop you will learn how to create Splunk destination as EventBridge Target and configure EventBridge Rules to ingest events from Amazon GuardDuty into Splunk.

This lab will go through the following: 
- Create a HEC token to use for Eventbridge
- Setup Splunk as a API destination in Eventbridge
- Setup Eventbridge Rule for Amazon GuardDuty events
- Validate data is streaming into Splunk from Amazon GuardDuty

<!--->
>[!NOTE]
>As EventBridge destination endpoint uses HEC (unacknowledged) we will re-use the HEC token created in <a>[Lab3](/content/Lab3_lambda/index.en.md)</a>. If you have not done Lab 3 yet then either do this or at least run the first steps on <a>[creating the HEC token](/content/Lab3_lambda/setup_splunk.md)</a> before starting this lab.
--->

## Architecture Diagram 
Below is the high level architecture that you will deploy for this lab:

![image001](/static/40_eventbridge/architecture-eventbridge.png)

### Click <a>[Next](/content/Lab4_eventbridge/setup_splunk.md)</a> to continue or click <a>[Back](/README.md) to go back to the beginning</a>