---
title: "Clean up Lab environment"
chapter: true
weight: 25
---

### To avoid incurring any costs, clean up in following order
1) Stop Logging and Remove the CloudTrail trail for this lab.
2) Remove the subscription filter from CloudWatch log group
3) Remove the Log group used for your CloudTrail lab
2) Delete the Amazon Data Firehose used in the lab
3) Delete the CloudFormation Stack which deployed prerequisites
4) Login to Splunk and remove the HEC token created in Splunk