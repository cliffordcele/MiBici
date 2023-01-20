# MiBici: Guadalajara's Bike-Sharing System & COVID-19

## Introduction

[MiBici](https://www.mibici.net/) (MyBike) is Guadalajara's public bike sharing system in the state of Jalisco, Mexico. Created in 2014, the system has over 3,200 
bikes and 300 stations available in the municipalities of Guadalajara, Zapopan, and Tlaquepaque. MiBici consists of a line of bikes that are locked into a network 
of docking stations throughout the municipalities. To use the bikes, one must purchase a subscription. The bikes can be unlocked from one station and returned to 
any other station in the system. Bikes are available every day of the year from 05:00 AM to 00:59 AM the next day and are designed to be used for an unlimited number 
of trips so long as each trip is less than 30 minutes (on Sundays, this is 45 minutes). When bikes are used for periods of more than 30 minutes, additional charges 
are incurred. The program acts as a complement or extension to other transportation systems in the area [[MiBici FAQs]](https://www.mibici.net/es/preguntas-frecuentes/).

As such, the goal of this project is to explore and visualize how cycling behaviors have changed in Guadalajara and its surrounding municipalities due to the COVID-19 
pandemic (between January 2017 and December 2022).

## Data Sources

### MiBici

The MiBici [open data](https://www.mibici.net/es/datos-abiertos/) system contains over 20 million observations across 14 variables. Each observation represents a bike ride, and each variable contains information about the bike ride. Reverse geocoding was used in Python to obtain the full address, neighborhood, and municipality of each station. Data between January 2017 & December 2022 are analyzed in this analysis.


Individual Ride Data    | Docking Station Data | Additional Station Data 
----------------------- | -------------------- | -----------------------
Trip ID                 | Station ID           | Address
User ID                 | Station Name         | Municipality 
Gender                  | Municipality         | Neighborhood
Year of Birth           | Latitude             | 
Start & End Date/Time   | Longitude            | 
Start & End Station ID  | Docking Status       | 


### COVID-19

The general directive of epidemiology for the Mexican government maintains a [dashboard](https://datos.covid-19.conacyt.mx/) of COVID-19 data for the country. In this analysis, the daily counts of confirmed cases are used for the municipalities of interest.

### Google Directions API

The google directions API is used to obtain  the cycling route coordinates between two stations. The [website states](https://developers.google.com/maps/documentation/directions/get-directions) that "The API returns the most efficient routes when calculating directions. Travel time is the primary factor optimized, but the API may also take into account other factors such as distance, number of turns and many more when deciding which route is the most efficient." Although each trip may not take the most efficient route between stations, this is assumed to be the case for the sake of visualization.


## Questions

### 1. How has the number of trips taken changed pre and post COVID?

This question is based on a study by [Padmanabhan et al. (2021)](https://www.sciencedirect.com/science/article/pii/S2590198220301937) who investigated the effects of COVID-19 on bike-sharing systems in three cities in the United States. The idea here is to compare biking trends to various waves of COVID-19 where cases changed drastically.

### 2. Has the trip duration changed over time?

The MiBici system is described to be used as a commuting option for people. With the lifestyle changes brought on by the COVID-19 pandemic, have people changed how long they use the system for?

### 3. What times of day are most popular to use the MiBici system?

This question is based on a [blog post](https://toddwschneider.com/posts/a-tale-of-twenty-two-million-citi-bikes-analyzing-the-nyc-bike-share-system/) by Todd W Schneider who analyzed the Citi Bike system in New York City. They created a plot of the average number of weekday Citi Bike trips by hour of day between Manhattan and the outer boroughs. It illustrates that in the mornings there are more riders entering Manhattan than leaving, and the reverse occurs in the afternoon; illustrating commuter patterns like rush hour (when people are heading to and from work/school).

### 4. What are the most popular routes and starting stations?

Are the popular locations that users visited before the pandemic different from the ones they visited during and after the pandemic?

## Key Outcomes 

**1. How has the number of trips taken changed pre and post COVID?**

Between 2017 and 2019, the MiBici system saw a steady increase in the number of trips taken daily. Occasional drops in ridership can be seen around dates associated with holidays such as New Year's and Easter. This trend continues in the beginning of 2020. However, COVID-19 cases began appearing in Guadalajara in mid-March, and by the end of month, lockdown measures were implemented from 23 March to 30 May. With a ban on non-essential activities at the national level, the MiBici system saw a drastic drop in daily ridership from 10,000+ trips daily to a low of roughly 2,000 trips in April. Since the end of the national lockdown, the system has seen a slow rise in usage. It is interesting to note that the number of daily trips did not fall when larger waves of COVID-19 cases in 2021 & 2022 occured.

<p align="center">
<img src="https://github.com/cliffordcele/MiBici/blob/main/Github_Pics/DailyTrips_COVID.png" width="600" />
</p>

**2. Has the trip duration changed over time?**

The trip durations range between 1.5 - 150 minutes, with most trips falling under 30 minutes. The most common trips have a duration of 5–7 minutes. Although there were overall less rides in 2020, this did not effect the pattern of trip durations seen in years before.

<p align="center">
  <img src="https://github.com/cliffordcele/MiBici/blob/main/Github_Pics/trip_durations.png" width="250" />
  <img src="https://github.com/cliffordcele/MiBici/blob/main/Github_Pics/Weekday.png" width="250" /> 
  <img src="https://github.com/cliffordcele/MiBici/blob/main/Github_Pics/Weekend.png" width="250" />
</p>

**3. What times of day are most popular to use the MiBici system?**

The MiBici system sees a sharp increase in ridership Monday - Friday during commuting hours for those going to work/school (8h), leaving school (14h), and leaving work (18h). On the weekend, a peak occurs around 13h, which seems to indicate a more leisurely use of the system. This pattern does not change between 2019 & 2020, but there is a decrease in the average count of trips per hour between the two years. Although lockdown measures were in place between late March and the end of May, not all people had the luxury of working from home which may explain why the commuter pattern still exists in 2020.


**4. What are the most popular routes taken and starting stations used?**

The top 30 routes taken in 2019 & 2020 are all located within the municipality of Guadalajara, the largest city in the state. Among the top 10 routes in 2019, none of these trips start & end at the same station, and only 7/30 are roundtrips. This is different from 2020 where 4 of the top 10 trips start & end at the same station, and 10/30 are roundtrips. 

<p align="center">
<img src="https://github.com/cliffordcele/MiBici/blob/main/Github_Pics/trip_routes.png"/>
</p>

**Conclusion**


In conclusion, it appears that overall ridership decreased once the pandemic started, however the major patterns of how the system is used did not change drastically.

## Tools & Publications

* Tools: Python, Tableau, exploratory data analysis (EDA), jupyter notebook, webscraping, pandas, beautifulsoup, Data Visualization
* Publication: [Tableau Dashboard](https://public.tableau.com/app/profile/clifford.cele/viz/MiBici/)



