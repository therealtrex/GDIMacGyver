# Lab 4.2 - Explore Security Dashboards

### Overview

The **Splunk App for AWS Security Dashboards** offers a rich set of pre-built Security dashboards and reports to analyze and visualize data from numerous AWS services – including AWS CloudTrail, Amazon VPC Flow Logs, Amazon S3 Access Logs, Amazon CloudFront Access Logs – from a single, free app. These dashboards will display information once the required underlying AWS data is onboarded to Splunk. 

*Note -Depending on which modules were completed in the lab, the dashboard panels that will have data will vary.*


### Explore Splunk App for AWS Security Dashboard

Go to the top-left corner of your Splunk screen and **click** on the Apps link, then **click** on the ‘Splunk App for AWS Security Dashboards’ link.  

![image_tag](/static/50_data_exploration/Image_18.png)  

You should see the ***Security Overview dashboard***, which has an array of panels providing information about a wide variety of AWS activity. 
  
![image_tag](/static/50_data_exploration/Image_19.png)  

As this dashboard is interactive, **click** on the *IAM Errors* link. This will take you to the ***IAM Activity dashboard***, where you can see further details about the activity happening with the IAM service.

![image_tag](/static/50_data_exploration/Image_20.png)  
  
**Click** on Security -> User Activity to switch to a user-centric view. 


![image_tag](/static/50_data_exploration/Image_21.png)  

As with most of the Security dashboards, the User Activity dashboard has numerous filters that can be applied. 
  

Additionally, some of the panels allow you to drill down directly to the underlying data and events. 

**Click** on the Active Users link, which will take you back to the Search app where you can see the search and search results. 



Continue to click on the different dashboard options to explore the options that are available once you load more AWS data into Splunk!

![image_tag](/static/50_data_exploration/Image_19.png)  



Congratulations! You have completed this lab.