# Final Project: Traffic Levels and Vehicle Accidents In Manhattan, NY
## DS Final Project
By Thy Ly, Yuqi Wang, Hoang Le, Yuqing Wu, Yesenia Ramirez

### Introduction
#### Business Understanding
As the holidays are approaching our group noticed that we typically see higher rates of traffic and car accidents. These high rates of traffic generally cause accidents because of the volume that is on the roads, or the bad weather. Therefore for our final project our group wanted to see when is the busiest time in Manhattan and do those date, times, and streets correlate with the date, time and streets of car accidents recorded. Additionally, our group will also like to see if the weather has any affect on the level of traffic and accident rates during the holidays. Through these findings we will be able to develop suggestions on approaches to navigate through these high traffic areas to avoid car accidents as well as manage through difficult weather situations to minimize accidents as well. 
Our group looked into NYC Open Data for daily traffic volume counts from 2015 to 2019. In this data set, one can see which of the administrative divisions the data was taken from, the month, year, date, hour and minute that the data was taken in. One can also see the volume of traffic that was in a specific street and in which direction the traffic was heading. In addition, we used NYC Open Data to pull Motor Vehicle Collisions which brought data surrounding car accidents in Manhattan in the same time frame (2015-2019). For the weather data, our group looked into National Centers for Environmental Information’s (NCEI) National Oceanic and Atmospheric Administration (NOAA) for Manhattan daily weather reports during the same time period as the traffic volume counts dataset. In particular, we retreived data from the weather station at LaGuardia Airport.

#### Link for Dataset
  - Motor Vehicle Collisions - Crashes: https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95
  - Climate Data Online: https://www.ncdc.noaa.gov/cdo-web/search?datasetid=GHCND
  - Automated Traffic Volume Counts: https://data.cityofnewyork.us/Transportation/Automated-Traffic-Volume-Counts/7ym2-wayt

#### Data Understanding
For the Data Understanding phase, we add to the foundation set up by Business Understand and drive the focus down to identify and analyze the data sets chosen to complete the project. To collect initial data, the requirements were that the data needs to be relatively recent and be separated by days. We confirmed that there is data available for the hypothesis, traffic volume, accidents numbers, and weather data were easy to find but we ran into the problem of there being too many cases for analysis and made the decision to narrow the search to Manhattan from January 2015 to December 2019. With this defined selection criteria, our initial data sets are the NCEI’s and NOAA’s Manhattan daily weather report, Manhattan traffic volume count datasets, and Manhattan accidents count.

#### Data Preparation
The source of the dataset used in our project is a merged dataset of all the ones listed above by date. The number of observations is 1111 days. Below is the list of variables in the dataset.
•	Total_Traffic - Total Daily Traffic Volume
•	log_traffic - Natural Logarithm of Total Daily Traffic Volume
•	Total_Crash - Total Daily Traffic Crashes
•	TAVG - Average Temperature (Fahrenheit)
•	PRCP - Precipitation (inches)
•	SNOW - Snowfall (inches)
•	SNWD - Snow depth (inches)
•	AWND - Average daily wind speed (miles per hour)
•	Holiday - Names the specific Federal holiday on given date
•	hld - dummy variable to indicate holiday
•	A dummy variable for each weekday (Sunday, Monday, ..., Saturday)
While doing preliminary data cleaning, we noted that not all dates in each year are available. For example, the last two weeks of December are typically not listed. The week of July 4th holiday is not listed. The original dataset omitted these days. For our research purposes, there needs to be a weekday and a holiday variable created so the addition was made to the dataset.

#### Exploratory Data Analysis (EDA)
We first prepared some summary statistics for numeric variables. The average daily total traffic is 410,952. The average daily wind speed is 10.82 miles per hour. The average daily precipitation is 0.12 inches. The average daily amount of snow is about 0.06 inches. The average daily snow depth is about 0.12 inches. The average daily temperature is about 55.6 degrees Fahrenheit. The average daily total crash accidents is 96. Finally, the average natural logarithm of total traffic is 11.9.

<img width="450" src="https://user-images.githubusercontent.com/68659092/208114616-6a5de73f-473a-46c3-9669-f7a2081dfff5.JPG">

We examined the average traffic crashes for each weekday in our sample. Crashes tend to occur more on working weekdays than on weekends.

<img width="450" src="https://user-images.githubusercontent.com/68659092/208115661-6a24e97e-f47d-451d-8f1c-8534291a677e.JPG">

We also created a scatterplot of log of total traffic volume versus total crashes. The scatterplot shows a positive correlation between these two variables.

<img width="450" src="https://user-images.githubusercontent.com/68659092/208115998-b4ecac22-e6f6-442b-b4b9-e2c502130909.JPG">

We also create a scatterplot of the average temperature versus daily total crashes. There is a positive correlation between these two variables. As temperatures increase, people tend to travel more, which may be related to more traffic accidents. 

<img width="450" src="https://user-images.githubusercontent.com/68659092/208116248-46517a0d-3bc0-40b9-8757-537c138dbb47.JPG">

Finally, we also create a correlation matrix to see the correlation between total traffic crashes and other variables. We looked at the row with total crashes. A more intense blue color indicates a strong positive correlation. A more intense negative red color indicates a strong negative correlation. As observed in our previous figures, total crashes has a positive correlation with average temperature, log of total traffic, and the indicator variable for weekday.

<img width="450" src="https://user-images.githubusercontent.com/68659092/208116481-bad2c9ed-4ec4-4f3f-a378-88209e20ca71.JPG">

### Machine Learning Model Training
- ANOVA TEST

The first ANOVA test is used to see the variation between total crashes and holidays.

According to summary from anova test, our p-value is 6.89e-08，which is less than 0.05. It means the daily number of car accidents varies greatly betwwen holidays and non-holidays. 

<img width="458" alt="Screen Shot 2022-12-15 at 3 39 20 PM" src="https://user-images.githubusercontent.com/54876981/207962381-79721e1b-dffa-48d4-8853-ac1818dff21a.png">

Diving deeper, we find out the average number of car crashes during federal holiday is 66.52 per day while the total number of car crashes during non-holiday is 96.19 per day. By just comaring their mean value, the amount of car accidents is 23.6% lower on federal holidays than on non-holidays.

<img width="138" alt="Screen Shot 2022-12-15 at 2 01 57 PM" src="https://user-images.githubusercontent.com/54876981/207961731-be5903a8-355f-495a-8f95-a0df2a1f3c1c.png">

The second ANOVA test, called "mod_weekday", was used to explore the effect of different day on traffic accidents.
Based on the results we got from the summary, the F value is 45.32, which is significantly large compare with 1, indicating there is a variance among means of different weekdays The p value is 2e-16,which is less than 0.05. These two values provide strong evidence to reject the null hypothesis. 

<img width="473" alt="Screen Shot 2022-12-15 at 3 50 46 PM" src="https://user-images.githubusercontent.com/54876981/207964536-ccf23bac-0793-4eac-b6a5-e24bf2851c21.png">


The mean value for number of total crashes on each day is identifical with each other, among all of them, the number of traffic accidents reached its peak on Friday, the highest number of the week, with an average of 110.98, and the lowest number of traffic accidents occurred on Sunday, with an average of 75.07.

<img width="138" alt="Screen Shot 2022-12-15 at 2 04 38 PM" src="https://user-images.githubusercontent.com/54876981/207963302-e612fc86-4262-4347-add1-3b22aeafc85d.png">

After investigating the variance between weekdays, we need to think: whether this trend is only related to different weekdays, or it is related to working days and weekends in general. Therefore, another test was designed based on the whether weekend is the factor that affect the overall results in genral.

From the summary of the weekend model ANOVA test, the F value is 139.8, which is greater than 1, and p value is 2e-16, also less than 0.05, both results shows that the average of the total crashes is significantly different with eath other on weekends and weekdays. 
The values provides insights into our findings as we can conclude that car crashes is more likely to occur on weekdays than during weekends as the mean value for weekday groups is 101 while the mean value for weekend groups is only 82.49. 


<img width="127" alt="Screen Shot 2022-12-15 at 2 05 58 PM" src="https://user-images.githubusercontent.com/54876981/207963435-31d62a04-1c67-413a-89c4-1ad87eb81d82.png">


- Model Selection

- Check Multicollinearity 

<img width="478" alt="Screen Shot 2022-12-15 at 15 56 25" src="https://user-images.githubusercontent.com/119276239/207965410-c34f450c-30bc-4507-ad40-49b260866151.png">
All VIFs are close to 1. Therefore, no variables should be removed here.

Then, we use three methods to do the model selection.

- Backwards elimination via p-value

In this part, we removed the variable with largest p-value each time until all variables are statistically significant. Here is the model we get from Backwards elimination via p-value.

<img width="466" alt="Screen Shot 2022-12-15 at 15 59 52" src="https://user-images.githubusercontent.com/119276239/207966024-c1aa0cf7-24c5-42f1-bb12-f03c446b2fa1.png">

- Best subsets

We also use the best subsets approach to improve the model selection.

<img width="480" alt="Screen Shot 2022-12-15 at 16 04 09" src="https://user-images.githubusercontent.com/119276239/207966733-24ac5a70-ba3f-41ce-b62e-d33e8db850bb.png">

The bic graph indicates the goodness of fit of different regression models. In this graph, the lower the bic is, the better the model is.
Therefore, the bic graph indicates that the subset with 3 variables is the best.

<img width="480" alt="Screen Shot 2022-12-15 at 16 05 01" src="https://user-images.githubusercontent.com/119276239/207966890-04003d27-56be-4ba5-977c-91266cd0628d.png">

Mallows's cp is used to find the best subset of predictors based on the residual sum of squares. A smaller cp value indicates a more precise model.
In the cp graph, the model of 5 predictors has the smallest cp value.

<img width="480" alt="Screen Shot 2022-12-15 at 16 06 13" src="https://user-images.githubusercontent.com/119276239/207967111-56b671ce-0e79-458e-b866-858c1094593c.png">

The adjusted R^2 indicates that how much variance of the output variable is explained by the input variables. By adding variables, we can see an increase of adjusted R^2. The adjusted R^2 reaches its peak when the subset is of 6 predictors.
In terms of the different subsets that suggested by different graphs. We have to compare these results with other model selection methods to decide the optimal model.

- Automated Stepwise

<img width="425" alt="Screen Shot 2022-12-15 at 16 08 33" src="https://user-images.githubusercontent.com/119276239/207967498-47052a34-591f-4cc6-99b2-77649465d100.png">

In the automated stepwise model selection, we used backward stepwise which is in the beginning of the model, all variables are included, and then test each variable as it is removed from the model (which selected is depends on the lowest AIC value of the variables in the current model because lower AIC indicated a best-fit model), then keep those that are considered to be the most statistically significant - repeating the process until the results are optimal.

Here is the summary of the optimal model.

<img width="465" alt="Screen Shot 2022-12-15 at 16 10 24" src="https://user-images.githubusercontent.com/119276239/207967796-f93bd2f6-4573-484c-be61-4ac014566dc2.png">

After the selection, the optimal model with the lowest AIC includes AWND, TAVG, hld, Weekday, and Total_Traffic, which is the same as the model that we got from the backward elimination via p-value.

- Final Model

According to results from different approaches, we include AWND, TAVG, hld, Weekday, and Total_Traffic as the predictors in the final model.

- Transformation

<img width="465" alt="Screen Shot 2022-12-15 at 16 11 39" src="https://user-images.githubusercontent.com/119276239/207967990-8a0916d7-7e9f-4474-9636-4cdf3ee3cda4.png">

Due to the different scales of different variables, we take the log of Total_Crash and Total_Traffic to make the coefficients look normal.
After the transformation, we successfully improve the Adjusted R\^2 from 12.2% to 14.7%.

- Model Evaluation

<img width="505" alt="Screen Shot 2022-12-15 at 16 12 22" src="https://user-images.githubusercontent.com/119276239/207968123-a439028a-0cc2-4309-8d40-2263232f10b9.png">

The residual plots indicate that the model overall fits very well. The dataset is normally distributed and has no outliers.

### Actions

- From both the ANOVA tests and our regression models, we can conclude that number of car crashes reached its peak on Friday among all other days. The reason might be that many people travel between near towns or county for work, and they are going home on Friday. Friday is probably the buisest day of the week, so we can add more traffic police power in busy areas/time to maintain traffic order, and clear the vehicle in the accidents on time to ensure the circulation of the road section in the event of an accident. 

- Based on our findings, car crashes happened more during normal weekdays compare with the total number of crashes on weekends, therefore we can change the timing of traffic lights to accommodate to different volume of traffic according to traffic conditions during weekdays and weekends.

- Send drivers real time notifications about traffic volume and conditions and ask them to be cautious during busy hours through radio or maps.

### LINK TO CODE
#### Data Cleaning and EDA
https://www.kaggle.com/code/ghghtak4/data-cleaning-and-eda

#### Machine Learning Model
https://www.kaggle.com/code/ghghtak4/machine-learning-model

#### Model Selection
https://www.kaggle.com/code/ghghtak4/model-selection

### LINK TO YOUTUBE VIDEO
Presentation video: https://youtu.be/kr3jxNvfYSI

Tutorial video: https://youtu.be/exMnIX4yf6I
