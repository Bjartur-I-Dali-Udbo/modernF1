# F1_analytics
Hobbyist project on historical trends in Formula 1 and providing proper insights, where modern motorsport data-journalism usually neglects important factors. I 


# Data acquisition
If you are not a nerdy fan of the layout steps for the scientific method, I advise you to skip this part. To your important inormation this highly critical part of this scientific project, was not written with passionate love for the most repeated standard procedure known to manking.
### **Ergast API** (https://ergast.com/mrd/) Now deprecated
  - Season List, Race Schedule  
  - Qualifying Results, Sprint Qualifying Results  
  - Lap Times, Pit Stops, Race Results, Finishing Status  
  - Standings  
  - Driver Information, Constructor Information, Circuit Information  
  

### **f1db Open Source Formula 1 Database** (https://github.com/f1db/f1db)  
  - All drivers, constructors (including chassis), engine manufacturers (including engines)  
  - All tyre manufacturers, circuits and location data  
  - All seasons from 1950 to present; including:  
     - entrants,  
     - standings  
  - All races; including:,  
     - free practice and warming-up results  
     - qualifying and pre-qualifying results  
     - sprint race results  
     - starting grid positions  
     - race results  
     - fastest laps  
     - pit stops  
     - driver of the day results  
     - standings

### Other meta data
- Front Row sizes.
	- Sources for Pre-1974. (No standardised grid layouts).
		- Old Autosport forum threads.
   		- Result websites.
   		- Pictures of starting grids.
 	- 1974-1980
  		- 2x2 cars lined up side by side, standardised.
 	- 1981-present.
  		- 1x1x1cars line up, separated 8m length wise and width offset with a track dependent value, standardised.
      		- 1980 Monaco GP used such a line up, or similar.
        		- **TODO:** Identify race starts that deviate from reulations.
- Constructor plotting colours
	- Manually selected for most common colours used in teams history.
- Driver plotting colours.
	- Manually selected for the team they have been affiliated with for the longest time or a colour scheme familiar to the flag of their nationality.
	
## Data Merging of key information.
Ergast and f1db databases are largely identical, but there are cases in Ergast not having qualification data, but contains lap times of the race (1996-present), while f1db contains all qualification times ever set, but not lap times. Data is merged by using identifiers that are consistent in both datasets.  

**Race events**  
 - Season/Year  
 - race name and track.

**Constructors**
 - Season entrants.

**Drivers**
- Filtered race events
- Filtered constructors
- Race number of car
- First and last name of driver.  

Drivers used to be able to share a seat and swap during tire changes - this happened regularily in the earlier years of Formula 1 World Championship. So there are instances of drivers having multiple finish positions as they contributed in more than one car at the same race.


# Qualification analysis

## Seasonal performance of constructors based on best qualification time set by any of the drivers.

The most frequently used meausring stick to determine best cars in Formula 1, is to use the number of wins acquired in a season, or how many pole positions they acheived. Other times are the supertimes used, which are the fastest times set by a team in any of the sessions in a race week. Then measure the absolute time difference to their closest competitor, usually in percentage terms.

The former method by using qualification or race results, most frequently draws in the following seasons as those with the best cars.  
- 1988 McLaren
- 2002 Ferrari
- 2004 Ferrari
- 2011 Red Bull
- 2013 Red Bull
- 2014-2016 Mercedes.
- 2022-2023 Red Bull

However this approach does not quantify actual pace. Often brought up counter points in these comparisons are the 1992, 1993 Williams cars and 2020 Mercedes car. Which are renowned for their pace in relation to the rest of the Formula 1 field. All three cars acquired a high rate of pole positions and wins, but not within the realm of the 1988, 2022 and 2023 blow outs. But are they worthy of being spoken of as some of the best ever, when they did not produce as many championship points one would expect from such performance?

### Percentage gap to closest competitor.
Throughout each race for a whole season, are the best times of each constructor compared to one another, the time difference to the best team are scaled in percentages to maintain comparative units. If the best team sets a time of 100 seconds and the second fastest team sets a time of 101 seconds -- the second fastest team gets a score of 1%, while the constructors with slower times get even higher scores. Pole setter gets a score of 0%. For the whole season is the mean score calculated for each constructor. If a team happened to set pole position in every race event, they would always receive a score of 0% and have a mean of 0%.

**For plotting the gap to the closest competitor,** the are scales shifted to make *relative* percentage to second fastest team, this better exemplifies the percentage advantages across seasons.
