# Final Project: Traffic Levels and Vehicle Accidents In Manhattan, NY
## DS Final Project
By Thy Ly, Yuqi Wang, Hoang Le, Yuqing Wu, Yesenia Ramirez

### Introduction
#### Business Understanding
As the holidays are approaching our group noticed that we typically see higher rates of traffic and car accidents. These high rates of traffic generally cause accidents because of the volume that is on the roads, or the bad weather. Therefore for our final project our group wanted to see when is the busiest time in Manhattan and do those date, times, and streets correlate with the date, time and streets of car accidents recorded. Additionally, our group will also like to see if the weather has any affect on the level of traffic and accident rates during the holidays. Through these findings we will be able to develop suggestions on approaches to navigate through these high traffic areas to avoid car accidents as well as manage through difficult weather situations to minimize accidents as well. 
Our group looked into NYC Open Data for daily traffic volume counts from 2015 to 2019. In this data set, one can see which of the administrative divisions the data was taken from, the month, year, date, hour and minute that the data was taken in. One can also see the volume of traffic that was in a specific street and in which direction the traffic was heading. In addition, we used NYC Open Data to pull Motor Vehicle Collisions which brought data surrounding car accidents in Manhattan in the same time frame (2015-2019). For the weather data, our group looked into National Centers for Environmental Information’s (NCEI) National Oceanic and Atmospheric Administration (NOAA) for Manhattan daily weather reports during the same time period as the traffic volume counts dataset. 

#### Link for Dataset
  - Motor Vehicle Collisions - Crashes: https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95
  - Climate Data Online: https://www.ncdc.noaa.gov/cdo-web/search?datasetid=GHCND
  - Automated Traffic Volume Counts: https://data.cityofnewyork.us/Transportation/Automated-Traffic-Volume-Counts/7ym2-wayt

#### Data Understanding
For the Data Understanding phase, we add to the foundation set up by Business Understand and drive the focus down to identify and analyze the data sets chosen to complete the project. To collect initial data, the requirements were that the data needs to be relatively recent and be separated by days. We confirmed that there is data available for the hypothesis, traffic volume, accidents numbers, and weather data were easy to find but we ran into the problem of there being too many cases for analysis and made the decision to narrow the search to Manhattan from January 2015 to December 2019. With this defined selection criteria, our initial data sets are the NCEI’s and NOAA’s Manhattan daily weather report, Manhattan traffic volume count datasets, and Manhattan accidents count.
The source of the dataset used in our project is a merged dataset of all the ones listed above by date. The number of observations is 1111 days. Below is the list of variables in the dataset.
•	TAVG - Average Temperature (Fahrenheit)
•	PRCP - Precipitation (inches)
•	SNOW - Snowfall (inches)
•	SNWD - Snow depth (inches)
•	AWND - Average daily wind speed (miles per hour)
•	Holiday - Names the specific Federal holiday on given date
•	hld - dummy variable to indicate holiday
•	A dummy variable for each weekday (Sunday, Monday, ..., Saturday)
While doing preliminary data exploration, we noted that not all dates in each year are available. For example, the last two weeks of December are typically not listed. The week of July 4th holiday is not listed. The original dataset omitted these days. For our research purposes, there needs to be a weekday and a holiday variable created so the addition was made to the dataset.

### Insights and Actions
- ANOVA TEST

The first ANOVA test is used to see the variation between total crashes and holidays.

According to summary from anova test, our p-value is 6.89e-08，which is less than 0.05. It means the daily number of car accidents varies greatly betwwen holidays and non-holidays. 

<img width="458" alt="Screen Shot 2022-12-15 at 3 39 20 PM" src="https://user-images.githubusercontent.com/54876981/207962381-79721e1b-dffa-48d4-8853-ac1818dff21a.png">

Diving deeper, we find out the average number of car crashes during federal holiday is 66.52 per day while the total number of car crashes during non-holiday is 96.19 per day. By just comaring their mean value, the amount of car accidents is 23.6% lower on federal holidays than on non-holidays.

<img width="138" alt="Screen Shot 2022-12-15 at 2 01 57 PM" src="https://user-images.githubusercontent.com/54876981/207961731-be5903a8-355f-495a-8f95-a0df2a1f3c1c.png">

The second ANOVA test, called "mod_weekday", was used to explore the effect of different day on traffic accidents.
Based on the results we got from the summary, the F value is 45.32, which is a significant compare with 1, indicating there is a variance among means of different weekdays The p value is 2e-16,which is less than 0.05. These two values provide strong evidence to reject the null hypothesis. 

<img width="493" alt="Screen Shot 2022-12-15 at 3 42 52 PM" src="https://user-images.githubusercontent.com/54876981/207962964-aacaf9d7-4258-4697-bac3-5063667c522a.png">

The mean value for each weekday is identifical with each other, among all of them, the number of traffic accidents reached its peak on Friday, the highest number of the week, with an average of 110.98, and the lowest number of traffic accidents occurred on Sunday, with an average of 75.07.

<img width="138" alt="Screen Shot 2022-12-15 at 2 04 38 PM" src="https://user-images.githubusercontent.com/54876981/207963302-e612fc86-4262-4347-add1-3b22aeafc85d.png">

After investigating the variance between weekdays, we need to think: whether this trend is only related to different weekdays, or it is related to working days and weekends in general. Therefore, another test was designed based on the whether weekend is the factor that affect the overall results in genral.

<img width="127" alt="Screen Shot 2022-12-15 at 2 05 58 PM" src="https://user-images.githubusercontent.com/54876981/207963435-31d62a04-1c67-413a-89c4-1ad87eb81d82.png">




### LINK TO CODE

### LINK TO YOUTUBE VIDEO

