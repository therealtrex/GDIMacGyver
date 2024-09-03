---
title : "Step 2: Splunk Enterprise Instance Setup"
weight : 32
---


## Overview

In this section, we will setup a Splunk Enterprise Instance and load balancers to get an endpoint for Firehose and Lambda workshop. We will launch a VPC and deploy a Splunk Enterprise Instance and host behind a load balancer to get the endpoint URL.


## Splunk Enterprise Instance Setup

- Click [Launch Stack](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=SplunkGDIWorkshopStack&templateURL=https://ws-assets-prod-iad-r-iad-ed304a55c2ca1aee.s3.us-east-1.amazonaws.com/5039b0de-622d-4224-8760-d9dff0c13e0b/SplunkFirehoseLabModule_Latest.yml) to launch Cloudformation stack creation and click **Next** as shown below
- Scroll down and for **Splunk AMI** parameter value, enter the AMI id you noted from previous step. 
- Click **Next** and Click **Next**, check the acknowledgement under Capabilities and transforms and click **Create Stack**
- It takes about 4-5 mins to create this stack. Once the stack is shown as **CREATE_COMPETE**, go to **Outputs** tab and verify you have the following outputs as shown in figure below:
 ![architecture](/static/10_prerequisites/splunk_instance/cftoutputs.png)
- Go to EC2 dashboard in AWS console. You should see an instance named **Splunk-Enterprise** running. Select the instance click **Connect**
 ![architecture](/static/10_prerequisites/splunk_instance/ec2instance.png)
- Go to **Sessions Manager** and Click **Connect**
![architecture](/static/10_prerequisites/splunk_instance/ec2connect.png)
- This opens a new tab in your browser with session manager session. 
- Copy and enter the following commands in the terminal
```bash
sudo su
export SPLUNK_BIN=/opt/splunk/bin/splunk
export SPLUNK_HOME=/opt/splunk
cd $SPLUNK_HOME/etc/system/local
ls
```
- Check if you can find `web.conf` file
![architecture](/static/10_prerequisites/splunk_instance/webconf.png)
- Use vi or vim editor and edit the `web.conf` to set `enableSplunkWebSSL` option to `true`. This will enable SSL option for the Splunk instance.
```bash
enableSplunkWebSSL = true
```
![architecture](/static/10_prerequisites/splunk_instance/webconfssl.png)
- Save the file and enter the following command to restart the Splunk instance:
```bash
$SPLUNK_BIN restart
```
- You should see the message as below confirming the Splunk instance restarted  
![architecture](/static/10_prerequisites/splunk_instance/splunkrestart.png)
- Exit out of the session manager session. Now go back to **Outputs** tab in Cloudformation stack for the stack you created above, scroll down and right-click the **SplunkURL** url value and open in a new browser tab. 
![architecture](/static/10_prerequisites/splunk_instance/splunkurl.png)
- This will open up the Splunk admin console. 
- If above URL do not work and you get a connection error, *ensure you are not connected to any corporate VPN. Since this Splunk URL uses arbitrary port 8000, some corporate firewalls may block the port. Disconnect from your VPN connection and try again.*
- You will get warning message first time in the browser since Splunk by default uses a self signed certificate inside the Splunk instance. Accept the risk and proceed. If you are using chrome browser, and see a warning message like **Your connection is not private** just click anywhere on the browser and type the word *thisisunsafe* and press enter to ignore the warning and proceed. Refer How to Video [here](https://www.youtube.com/results?search_query=chrome+this+is+unsafe+bypass).
- Enter **admin** as user name and for the password, go back to Cloudformation **Outputs** tab and copy the **SplunkUserPassword** value (The format of this Value is `SPLUNK-<AWS Instance Id>`)  and paste the value. This should log into your Splunk Console.
![architecture](/static/10_prerequisites/splunk_instance/splunkpasswd.png)
- Congratulations on finishing this step, let’s move on to install the AWS Add-on App in this Splunk instance.
