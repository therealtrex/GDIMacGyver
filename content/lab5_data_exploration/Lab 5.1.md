# Lab 5.1 - Data Exploration

## Overview

The previous labs were focused on getting AWS data into Splunk. This lab builds upon the previous labs and is focused on exploring the data that is now in Splunk. 

### Open the Search App and Have a Play!


Select ‘Last 4 Hours’ from the time picker, then copy the following into the search bar:


`index=”aws-data”`


The results should look something like the below image. Spend some time exploring the interface. Click on some of the interesting fields. Expand an event. Change the time frame. See if you can find an insight that piques your interest.  


![image_tag](/static/50_data_exploration/Image_1.png)  


Click on **sourcetype**
  

Note the different sourcetypes that we’ve added in the previous labs. **Click on one of the sourcetypes**. You will see that the sourcetype has been added to the search, and the results will reflect the sourcetype selection. 


![image_tag](/static/50_data_exploration/Image_2.png)  



### Build a Dashboard

**Find Provisioning Activity From an Unusual IP**

Now that you have some familiarity with the data that is flowing into your Splunk environment, let’s build a dashboard! 

To start, we will run a search that looks for Cloud Provisioning activities that occur from new IP addresses. For our environment, all records are going to qualify as ‘new’ addresses, since the data that is loaded is brand new - so we don’t need to alert the instructor that our environment is compromised! In a production environment, the results of this search could suggest that credentials have been created or compromised, and are in control of an adversary. This could result in potential data leakage, data deletion, or cost run-up.


Let’s start with the search. Copy the below search string into the search bar and keep the time range for the last 4 hours.


`index="aws-data"  sourcetype=aws:cloudtrail eventName=Create* OR eventName=Run* OR eventName=Attach* 
| stats earliest(_time) as earliest latest(_time) as latest by src_ip, eventName 
| eval maxlatest=now() 
| eval peergroup_name="None", isOutlier=case(len(peergroup_name)>0 , if(isnotnull(earliest) AND earliest>=relative_time(maxlatest,"-1d@d") AND isnull(peerpast),1,0), earliest >= relative_time(maxlatest, "-1d@d"), 1, 1=1, 0) 
| where isOutlier=1 
| stats count`

Your results should look something like below:

![image_tag](/static/50_data_exploration/Image_3.png)  



  

It may look like a lot is happening in this search, but what we’re doing on the first line is bringing in our Cloudtrail logs filtered for provisioning activities. Then we use a stats command to calculate what the earliest and last date is that we’ve seen this combination of fields. Finally, if the earliest time we have seen this value was within the last day, that means the first time we’ve ever seen it just happened, and it qualifies as anomalous.


Since the result of this search is a number, this is a great candidate for a single value visualization. 

**Click** on the Visualization tab, then select the ‘Single Value’ option.

![image_tag](/static/50_data_exploration/Image_4.png)  
  

Your result will look something like this (the number will likely be different):
  

![image_tag](/static/50_data_exploration/Image_5.png)  

Now that we have a single value visualization, we can easily add it to a dashboard. 

Go to the top right corner of the screen and select **‘Save As -> New Dashboard’**.
  
![image_tag](/static/50_data_exploration/Image_6.png)  

On the ‘Save Panel to New Dashboard’ dialog, **enter/select** the following values:
* Dashboard Title: `AWS GDI Intro Dashboard`
* Select Dashboard Type: **Dashboard Studio**
* Style Selection: **Grid**
* Panel Title: `Outliers`
  
**Click ‘Save To Dashboard’**, then **click ‘Go To Dashboard’**. 

![image_tag](/static/50_data_exploration/Image_7.png)  

**Congratulations!** You’ve created your first dashboard. From here, you can change the appearance and layout of your dashboard. Feel free to click ‘Edit’ at the top right of the dashboard to customize your dashboard. 


![image_tag](/static/50_data_exploration/Image_8.png)  


Let’s make this dashboard a little more useful and add another panel. 

**Click** on the Search tab at the top of the screen to get back to the search screen.  Copy and paste the below search, with the **time picker set to the last 4 hours**.


`index="aws-data" sourcetype=aws:cloudtrail eventName=Create* OR eventName=Run* OR eventName=Attach* 
| stats earliest(_time) as earliest latest(_time) as latest by src_ip, eventName 
| eval maxlatest=now() 
| eval peergroup_name="None", isOutlier=case(len(peergroup_name)>0 , if(isnotnull(earliest) AND earliest>=relative_time(maxlatest,"-1d@d") AND isnull(peerpast),1,0), earliest >= relative_time(maxlatest, "-1d@d"), 1, 1=1, 0) 
| table "src_ip" "eventName", earliest, latest, maxlatest, isOutlier 
| convert ctime(earliest) ctime(latest) ctime(maxlatest)`

This search will look very similar to the previous search, but we replaced the stats command with a table command, which outputs the specified fields. 


Similar to our previous search, **click on ‘Save As’** at the top right of the screen, but instead of *clicking ‘New Dashboard’, click ‘Existing Dashboard.*’ 
  
![image_tag](/static/50_data_exploration/Image_9.png)  

Select **AWS GDI Intro Dashboard** *(or the dashboard name you used in the previous step)*, and enter `‘Outlier Details’` in the Panel Title. **Click ‘Save to Dashboard’** and then **‘View Dashboard.’**

![image_tag](/static/50_data_exploration/Image_10.png)  
  
Your dashboard should now look something like below:

![image_tag](/static/50_data_exploration/Image_11.png)  

### *Optional - Create a Map Visualization:*

*If you have completed the Lambda Lab and you have data with the **aws:cloudwatchlogs:vpcflow** sourcetype, you can now create a visualization showing which non US-based countries traffic is originating from in our environment.*

Start by entering the following search:


`index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow" 
| iplocation src_ip 
| search Country!="United States" `


The search just retrieved all entries in the **“aws-data”** index with the **aws:cloudwatchlogs:vpcflow** sourcetype, then piped those results into an *iplocation command*. The *iplocation command* extracts location information from IP addresses - in our case from the **src_ip** field - and adds the location fields to our search results. 

![image_tag](/static/50_data_exploration/Image_12.png)  

We also omitted traffic originating from the United States, since we are interested in countries that aren’t the US. 


Let’s finish our search by adding in the *geom command*, which adds a field containing geographic data structures that are used to create choropleth map visualizations. **Copy** the below search and paste it in the search bar (overwriting the previous search)


`index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow" 
| iplocation src_ip 
| search Country!="United States" 
| stats count by Country 
| geom geo_countries featureIdField="Country"`


The results should look something like the image below. At the moment, this doesn’t seem all that useful - and maybe looks a little complicated!

![image_tag](/static/50_data_exploration/Image_13.png)  


However, if you **click on the Visualization tab**, you will see a number of different visualization options for the data, and Splunk will recommend a visualization based on the results of the search. **Click on the ‘Chloropleth Map’ in the ‘Recommended’ section**


![image_tag](/static/50_data_exploration/Image_14.png)  


You should now see a map, with Great Britain as the most obviously highlighted country. You may have to modify the map formatting to have more granularity. You can update this by selecting the **‘Format -> Colors’** option, then updating the Number of Bins. **Select** the largest option - in our case the option ‘9’. 

![image_tag](/static/50_data_exploration/Image_15.png)  

Feel free to make the color scheme your own by updating the colors or other options!
  

Once you have the map formatted the way you want, let’s add it to our AWS GDI Intro Dashboard. **Click on Save As - Existing Dashboard**. 

**Select** the AWS GDI Intro dashboard, and enter `Traffic Heatmap` for the Panel Title.
  
![image_tag](/static/50_data_exploration/Image_16.png)  


Your dashboard should now look something like below:

![image_tag](/static/50_data_exploration/Image_17.png)  


**Congratulations!** You have completed this lab. Please proceed to the next lab to explore some already made security dashboards.