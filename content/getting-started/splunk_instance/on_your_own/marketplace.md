---
title : "Step 1: Marketplace subscription"
weight : 31
---

## Splunk Enterprise - AWS Marketplace Subscription

- Login to AWS Console and search for AWS Marketplace, click the AWS Marketplace Subscriptions 
  ![architecture](/static/10_prerequisites/marketplace/marketplace1.png)

- Expand the left hand side panel by clicking the hamburger menu for **AWS Marketplace** options
  ![architecture](/static/10_prerequisites/marketplace/marketplace1_1.png)
- Click **Discover Products**.

- Enter Splunk and look for **Splunk Enterprise**
![architecture](/static/10_prerequisites/marketplace/marketplace2.png)

- Select Splunk Enterprise and Click **Continue to Subscribe** option at top left hand side
![architecture](/static/10_prerequisites/marketplace/marketplace3.png)

- The AMI listed is a BYOL license with 60 days trial license included. For the scope of this lab, this trial license should be good.

- Review and **Accept Terms**

![architecture](/static/10_prerequisites/marketplace/marketplace4.png)

- It will take a few minutes to process the request

- Once the Subscription process is complete, you will get a messaging confirming the subscription with the effective date as current date
![architecture](/static/10_prerequisites/marketplace/marketplace5.png)

- Click Continue to Configuration. Note the AMI id for the region selected. 
::alert[Ensure you select the current AWS region from the Region choice and note the correct AMI id. Each region will have different AMI ids. The figure shown below shows an example of AMI id in **US-EAST-1** region.]{header="Note"}
![architecture](/static/10_prerequisites/marketplace/marketplace6.png)

- Exit from the marketplace once you are done with subscription and noted the AMI id. **Do not launch the instance manually.**

