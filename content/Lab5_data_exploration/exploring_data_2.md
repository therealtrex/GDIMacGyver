# Adding an additional panel to our dashboard
Continuing on, let’s make this dashboard a little more useful and add another panel. 

-Click on the `Search tab` at the top of the screen to get back to the search screen. `Copy and paste the below search`, with the `time picker set to the last 4 hours`

```text
index="aws-data" sourcetype=aws:cloudtrail eventName=Create* OR eventName=Run* OR eventName=Attach* 
| stats earliest(_time) as earliest latest(_time) as latest by src_ip, eventName 
| eval maxlatest=now() 
| eval peergroup_name="None", isOutlier=case(len(peergroup_name)>0 , if(isnotnull(earliest) AND earliest>=relative_time(maxlatest,"-1d@d") AND isnull(peerpast),1,0), earliest >= relative_time(maxlatest, "-1d@d"), 1, 1=1, 0) 
| table "src_ip" "eventName", earliest, latest, maxlatest, isOutlier 
| convert ctime(earliest) ctime(latest) ctime(maxlatest)
```

>[!NOTE]
>This search will look very similar to the previous search, but this time we replaced the stats command with a table command, which outputs the specified fields. 

- Similar to our previous search, click on `Save As` at the top right of the screen, but this time click `Existing Dashboard` 
  
![image_tag](/static/50_data_exploration/Image_9.png)  

Select `AWS GDI Intro Dashboard` (or the dashboard name you used in the previous step), and enter `Outlier Details` in the Panel Title. Click `Save to Dashboard` and then `View Dashboard`.

![image_tag](/static/50_data_exploration/Image_10.png)  
  
- Your dashboard should now look something like below:

![image_tag](/static/50_data_exploration/Image_11.png)  

## Create a Map Visualization
Now we will create a world map based on non US-based countries
- Start by entering the following search:

```text
index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow" 
| iplocation src_ip 
| search Country!="United States"
```
>[!NOTE]
>The search just retrieved all entries in the `aws-data` index with the `aws:cloudwatchlogs:vpcflow` sourcetype, then piped those results into an `iplocation command`. The `iplocation command` extracts location information from IP addresses. In our case from the `src_ip` field and adds the location fields to our search results. Lastly, we also omitted traffic originating from the United States, since we are interested in countries that aren’t in the US. 

![image_tag](/static/50_data_exploration/Image_12.png)  

- Let’s finish our search by adding in the `geom command`, which adds a field containing geographic data structures that are used to create choropleth map visualizations. `Copy and paste the below search into the search bar` (overwriting the previous search).

```text
index="aws-data" sourcetype="aws:cloudwatchlogs:vpcflow" 
| iplocation src_ip 
| search Country!="United States" 
| stats count by Country 
| geom geo_countries featureIdField="Country"
```

The results should look something like the image below. At the moment, this doesn’t seem all that useful - and maybe looks a little complicated!

![image_tag](/static/50_data_exploration/Image_13.png)  

- Click on the `Visualization tab` 
- Click on the `Chloropleth Map` in the `Recommended section`

![image_tag](/static/50_data_exploration/Image_14.png)  

You should now see a map, with Great Britain as the most obviously highlighted country. You may have to modify the map formatting to have more granularity. You can update this by selecting the `Format -> Colors` option, then updating the Number of Bins. `Select` the largest option - in our case the option `9`. 

![image_tag](/static/50_data_exploration/Image_15.png)  

Feel free to make the color scheme your own by updating the colors or other options!
  
- Let’s add it to our AWS GDI Intro Dashboard. Click on `Save As - Existing Dashboard`. 
- Select the `AWS GDI Intro dashboard`, and enter `Traffic Heatmap` for the Panel Title.
  
![image_tag](/static/50_data_exploration/Image_16.png)  

Your dashboard should now look something like below:

![image_tag](/static/50_data_exploration/Image_17.png)  

##### Congratulations! You have completed this lab. Please proceed to the next lab to explore some already made security dashboards.

### Click <a>[Next](/content/Lab5_data_exploration/exploring_aws_security_app.md)</a> to continue or if you have had enough click <a>[HOME](/README.md) to go back home.</a>