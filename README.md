# Final Project: Traffic Levels and Vehicle Accidents In Manhattan, NY
## DS Final Project
By Thy Ly, Yuqi Wang, Hoang Le, Yuqing Wu, Yesenia Ramirez

### Introduction
#### Business Understanding
As the holidays are approaching our group noticed that we typically see higher rates of traffic and car accidents. These high rates of traffic generally cause accidents because of the volume that is on the roads, or the bad weather. Therefore for our final project our group wanted to see when is the busiest time in Manhattan and do those date, times, and streets correlate with the date, time and streets of car accidents recorded. Additionally, our group will also like to see if the weather has any affect on the level of traffic and accident rates during the holidays. Through these findings we will be able to develop suggestions on approaches to navigate through these high traffic areas to avoid car accidents as well as manage through difficult weather situations to minimize accidents as well. 
Our group looked into NYC Open Data for daily traffic volume counts from 2015 to 2019. In this data set, one can see which of the administrative divisions the data was taken from, the month, year, date, hour and minute that the data was taken in. One can also see the volume of traffic that was in a specific street and in which direction the traffic was heading. In addition, we used NYC Open Data to pull Motor Vehicle Collisions which brought data surrounding car accidents in Manhattan in the same time frame (2015-2019). For the weather data, our group looked into National Centers for Environmental Information’s (NCEI) National Oceanic and Atmospheric Administration (NOAA) for Manhattan daily weather reports during the same time period as the traffic volume counts dataset. 

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

### LINK TO CODE

### LINK TO YOUTUBE VIDEO

### Insights and Actions
