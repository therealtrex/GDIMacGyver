# Setup an EventBridge destination target to point to Splunk HEC
In this part of the Lab we will setup the EventBridge Targets to configure Splunk as a Target. 

## Configure EventBridge Target & Connection for Splunk
- From your [AWS console](https://console.aws.amazon.com/events/home) search for and select Amazon Eventbridge
- Select `API Destinations` under `Integrations` on the left hand side.
- Click `Create API Destination`
- Enter the name for API Destination as `SplunkDestination`
- Enter your Splunk Endpoint URL under `API destination endpoint` formatted as following:
  - `https://<Your Splunk Endpoint URL>:8088/services/collector/raw`
- Select `HTTP Method` as `POST`.
- For the `Connection Type` check `Create a new connection`. See example below.

![event_destination](/static/40_eventbridge/eventbridge_destination.png)

- Enter the name for API Connection as: `SplunkConnection`.
- Check `Destination type` as `Partners` and select `Splunk` as Partner Destinations.
- Check `API Key` as `Authorization Type`.
- Type `Authorization` as the `API key name` value and enter the HEC you created for Eventbridge as `Splunk <Your HEC Token Value>` for `Value`
  - Example: If your HEC token is 72e88f28-9afd-4c52-96fe-16b27a67067e then enter `Splunk 72e88f28-9afd-4c52-96fe-16b27a67067e`.

>[!TIP]
>Put this in notepad first and then copy into the field to make it easier and reduce change of error as the field is *** out when you paste it in
  
![event_connection](/static/40_eventbridge/eventbridge_connection.png)

- Leave remaining defaults and click `Create` to create the endpoint.

##### You have successfully setup the Eventbridge destination for Splunk target. Lets move on to next lab to setup an EventBridge Rule to ingest GuardDuty events into Splunk

### Click <a>[Next](/content/Lab4_eventbridge/setup_rule.md)</a> to continue or click <a>[Back](/content/Lab4_eventbridge/setup_splunk.md) to go back a page.</a>
