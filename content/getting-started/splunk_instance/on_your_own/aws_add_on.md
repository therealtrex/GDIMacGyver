---
title : "Step 3: Splunk AWS Add-on App Setup"
weight : 33
---


## Overview

In this section, we will log into Splunk console and setup AWS Add-on app.


## Step 3 – Splunk AWS App Setup

- Open a separate tab in your browser and go to [splunkbase](https://splunkbase.splunk.com/) web page
- Click **My Account** at top left corner and select login to login with your Splunk Credentials. *If you don’t have Splunk account credentials, use Sign up to sign up for new Splunk Account*.
![architecture](/static/10_prerequisites/aws_add_on/splunkbase.png)
- Once Logged in, search for AWS Add-on, you should get pull down list starts with **Splunk Add-on for Amazon Web Services**. Select this App
![architecture](/static/10_prerequisites/aws_add_on/awsaddon.png)
- Download and save the app installation file to your local desktop **(You will install this App on the Splunk instance)**. Once downloaded, go back to your Splunk console and Click the Gear icon next to Apps at left hand side top
![architecture](/static/10_prerequisites/aws_add_on/appinstall1.png)
- Click **Install App from file**
![architecture](/static/10_prerequisites/aws_add_on/appinstall2.png)
- Browse the location of the App you downloaded and click **Upload**. This will install the App. You will get a message *Splunk Add-on for AWS* was installed successfully and you can view the App from the App List
![architecture](/static/10_prerequisites/aws_add_on/appinstall3.png)

### Now that we installed the AWS Add-on App, lets create a HTTP Event Collector (HEC) token for testing the endpoint in next step
- Go to **Settings** at right hand side top panel and Click **Data inputs**
![architecture](/static/10_prerequisites/aws_add_on/datainput.png)
- Click **+ Add new** next HTTP Event Collector
![architecture](/static/10_prerequisites/aws_add_on/datainputadd.png)
- Provide a name to the Event Collector (Ex: FirehoseLabHEC) and check **Enable indexer acknowledgement**
![architecture](/static/10_prerequisites/aws_add_on/hec1.png)
- Click **Next** and click Select option for the Source type. Enter *vpcflow* and select `aws:cloudwatchlogs:vpcflow` as source type
- Scroll Below to **Selected Allowed indexes**.  Select `main` which is the default Splunk index to store the data.
![architecture](/static/10_prerequisites/aws_add_on/hec2.png)
- Click **Review** and **Submit**. You should see a message that *Token has been created successfully* and see the Token Value. **Copy this HEC token value, you will require this later in next step.**
![architecture](/static/10_prerequisites/aws_add_on/hec3.png)
- Congratulations, you have now setup AWS Add-on App to receive AWS logs data and added an input to test the data ingestion on this Splunk instance. In next step we will create a load balancer to get an endpoint url to ingest data on this Splunk instance.