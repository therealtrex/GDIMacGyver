# Lab 5 - Data Exploration
In this lab we will take some of the ingested data from the previous 4 labs and visualise this in a new Splunk dashboard.

## Basic Searching
First off let's quickly search our data and have a basic look at what's coming in already. 

- From your Splunk Console, `select Apps` followed by `Search and reporting`
- Set the time range picker to `4 hours`
- From the Search bar enter in the search below:

```text
    index=”aws-data”
```
The results should look something like the below image. 

![image_tag](/static/50_data_exploration/Image_1.png)  

>[!TIP]
>Spend some time exploring the interface. Click on some of the interesting fields. Expand an event. Change the time frame. See if you can find an insight that piques your interest. 

- Moving on, let's click on `sourcetype`
- Note the different sourcetypes that we’ve added in the previous labs. `Click on one of the sourcetypes`. You will see that the sourcetype has been added to the search, and the results will reflect the sourcetype selection. See exmaple below.

![image_tag](/static/50_data_exploration/Image_2.png)  

## Let's build a Dashboard!
Now we are familar with the layout and data. Let's build our first dashboard. But what do we want to visualize? How about we run an example search which will show us if any new cloud provisioning activities are happening from new IP addresses. In a production environment, the results of this search could suggest that credentials have been created or compromised, and are in control of an adversary. This could result in potential data leakage, data deletion, or cost run-up.

>[!NOTE]
>For our environment, all records are going to qualify as `new` addresses, since the data that is loaded is brand new - so we don’t need to alert the instructor that our environment is compromised! 

- Let’s start with the search. Copy the below search string into the search bar and keep the time range for the last 4 hours.

```text
`index="aws-data"  sourcetype=aws:cloudtrail eventName=Create* OR eventName=Run* OR eventName=Attach* 
| stats earliest(_time) as earliest latest(_time) as latest by src_ip, eventName 
| eval maxlatest=now() 
| eval peergroup_name="None", isOutlier=case(len(peergroup_name)>0 , if(isnotnull(earliest) AND earliest>=relative_time(maxlatest,"-1d@d") AND isnull(peerpast),1,0), earliest >= relative_time(maxlatest, "-1d@d"), 1, 1=1, 0) 
| where isOutlier=1 
| stats count`
```

Your results should look something like below:

![image_tag](/static/50_data_exploration/Image_3.png)  

>[!NOTE]
>It may look like a lot is happening in this search, but what we’re doing on the first line is bringing in our Cloudtrail logs filtered for provisioning activities. Then we use a stats command to calculate what the earliest and last date is that we’ve seen this combination of fields. Finally, if the earliest time we have seen this value was within the last day, that means the first time we’ve ever seen it has just happened, and it qualifies as anomalous.

Since the result of this search is a number, this is a great candidate for a single value visualization. 

- Click on the `Visualization tab`, then select the `Single Value` option. See example below (your number will likely be different).

![image_tag](/static/50_data_exploration/Image_4.png)  

![image_tag](/static/50_data_exploration/Image_5.png)  

Now that we have a single value visualization, we can easily add it to a dashboard. 

## Create a dashboard
On the top right corner of the screen select `Save As -> New Dashboard`
  
![image_tag](/static/50_data_exploration/Image_6.png)  

On the `Save Panel to New Dashboard` dialog, `enter/select` the following values:
    - Dashboard Title: `AWS GDI Intro Dashboard`
    - Select Dashboard Type: `Dashboard Studio`
    - Style Selection: `Grid`
    - Panel Title: `Outliers`
  
Click `Save To Dashboard`, then click `Go To Dashboard` 

![image_tag](/static/50_data_exploration/Image_7.png)  

##### Congratulations! You’ve created your first dashboard. From here, you can change the appearance and layout of your dashboard. Feel free to click ‘Edit’ at the top right of the dashboard to customize your dashboard.

![image_tag](/static/50_data_exploration/Image_8.png) 

### Click <a>[Next](/content/Lab5_data_exploration/extend_dashboard_with_table.md)</a> to continue or if you have had enough click <a>[HOME](/README.md) to go back home.</a>