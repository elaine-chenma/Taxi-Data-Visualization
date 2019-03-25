# Tips of Taking a Taxi To JFK Airport From NYC 

Authors : April Chen, Elaine Ma, William Gao

[Link to Tableau Public](https://public.tableau.com/profile/chen.ma#!/vizhome/taxi_19/Dashboard2?publish=yes)
 
## Goals and Objectives 

“Taxi!” a yellow cab pulls up and you hop in. Sounds familiar? Nowadays, taking taxi is no longer the most popular choice of getting from point A to Point B in a private vehicle. Uber and other ride-sharing services have taken over more than half of the market shares from taxi industry in New York City. However, as a century-long public transportation service, it might be beneficial to take a look at how NYC taxi has been operating. 

With that being said, our team decided to dig into the 2016 NYC taxi data which contains over a million taxi ride events. Our primary goal is to build a visualization tool to access the approximate supply and demand of taxi services in a selected area in New York City. We went further to estimate ride durations with 80% of confidence for passengers who plans to hop in a taxi to JFK International Airport. For example: Kelly is a tourist in Time Square who has a flight leaving JFK at 7pm. She can use our visualization tool to find out an estimate time needed to travel to JFK from Time Square during the period of 3pm to 5pm so that she can decide whether to leave early for the airport. Then she can look at the lower left graph to see if she can get a taxi on the street without calling the taxi company. Calling the taxi company for a taxi can be an unpleasant when it is hard to describe where you are and the wait time can be more than 10 minutes. 

So how to read the dashboard? Users will be able to select an area on the map as taxi pick up location, then the Taxi Demand and Supply Graph on the lower left will display a drop off vs pick up analysis. Positive values indicate there are taxis available in the area, while negative value shows there is a high taxi demand in the area, but a passenger might still have a chance of getting in a taxi from vacant taxis cruising the area. Meanwhile, lower-right-corner graph shows the taxi trip time from selected area to JFK with 80% confidence bands the upper band represents the longest trip duration 80% of the time. 

## Data Insights 
With the taxi ride data in New York City 2016 and the dashboard provided above, taxi riders will be able to estimate the trip durations to JFK airport during certain time of the day and how many taxis are available around. Following interesting recommendations can be provided by this dashboard:

**1. It is very hard for people to find a vacant taxi during time periods from 5:00 am to 9:00 am and from 4:00 pm to 6:00 pm in NYC, probably because of the rush hour.**

Generally speaking, the busiest hours for taxi drivers in NYC is during these two time periods. The demands of taxi are much higher than supplies, with 7:00 am and 5:00 pm being the peak hours in the city. There are almost no vacant taxi available for riders during these two time periods, hence taxi is not the best way to commute during the rush hours in NYC.

**2. Travelers should avoid traveling to JFK from central park around 3:00 pm to 5:00 pm.**

According to year 2016 data, it takes longer time to travel from the central park to JFK airport during the late afternoon (from 3:00 pm to 5:00 pm) than other time in a day. The trip duration ranges from 50 min to one and a half hours which might result in a fat bill as the meter will remain counting even you are stuck in traffic. Taxi availability during this time period is very low, and the demands usually exceed the supplies. Hence there is a high possibility that travelers cannot find any available taxi during this time period.

**3. Taxi availabilities are usually low at Manhattan and downtown NYC area.**

For most time of the day, more people were picked up than being dropped off in the Lower Manhattan and downtown NYC area, indicating few vacant cars (disregarding vacant taxis cruising in the city). On the other hand, the situation is much better in upper Manhattan area. Usually there are more vacant taxi in the Upper Manhattan area, and the average travel time to JFK is around 40 minutes, much less time compared with starting from Lower Manhattan.

## Design Choices 
**1. Interact with the map to choose pick-up location**

NYC taxi dataset describes completed trips, with which we could have delivered descriptive analysis of taxi trips in NYC, but instead of presenting static stories, we want users to be able to interact with the map and choose the pick-up location. When user selects an area manually on the map, the map will act as a filter for the other graphs. By interacting with the map, user can focus on areas of interests and get an idea of the traffic condition of a taxi trip to JFK airport. 

**2. Demonstrate number of vacant taxis**
Waiting for a long time without seeing a vacant taxi is very frustrating, so when designing the chart, we thought it would be very helpful if we were able to estimate how likely users can find a available taxi. The likelihood to find vacant taxi is defined by the number of drop-off taxis minus number of pick-up taxis, within user-selected area. In order to do so, the original dataset is split into two sets of data with timestamps and location coordinates: pick-up data set and drop-off data set. When a user selects a certain area on the map, pick-up points and drop-off points within that area will be aggregated hourly. By comparing the demands and supplies of taxi information that is demonstrated in the line chart, user can get an intuitive idea of the taxis’ availability condition within a day.  

**3. Estimate trip time with confidence bands**

We considered using a bar chart or line chart to present average trip time to users, but when you have a flight to catch up with, you definitely care about how much time at most the trip will take, so that you can control the risk of missing the flight. The last plot uses a line chart with the confidence band to show the average trip time. 80% confidence band is estimated to indicate an estimation of the trip duration range.

## Future Developments
As we mentioned above, we deliberately ignored the existing vacant taxis which are already cruising in the city due to lack of information. We plan to gather data on NYC taxi vacancy rates for each area in different time ranges within a day. With these data, our team will be able to estimate the probability of a passenger getting a taxi ride in selected area more accurately.

### Reference
*Dataset: https://data.cityofnewyork.us/Transportation/2016-Green-Taxi-Trip-Data/hvrh-b6nb/data *

*Taxi, Uber, and Lyft Usage in New York City, by Todd W. Schneide: http://toddwschneider.com/posts/taxi-uber-lyft-usage-new-york-city/ *


