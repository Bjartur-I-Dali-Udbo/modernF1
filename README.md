# F1_analytics
Hobbyist project on historical trends in Formula 1 and providing insights, where modern motorsport data-journalism usually neglects important factors.

### Upcoming content.
- Driver specific stats.

# Qualification Dominance
Throughout each race for a whole season, are the best qualifying times of each team entrant compared to one another, the time difference to the best team are modified to percentages to maintain a comparative scale. If the best team sets a time of 100 seconds and the second fastest team sets a time of 101 seconds -- Pole setter gets a score of 0% - while the second fastest team gets a score of 1%, while constructors with slower times get even higher percentage scores. For the whole season is the mean score calculated for each constructor. If a team happened to set pole position in every race event, they would always receive a score of 0% and have a mean of 0%.
## Calculating percentage advantage
On average the top team acquires pole most frequently or are within 0.3% of the pole time in every qualification session, providing a seasonal average of around 0.15% away from the pole time. The advantage estimate is how much lower this value is to the closest competitor. Lets say the second fastest team has a score of 0.7%. That is a difference of 0.55%. This difference is displayed below, were the fastest teams' score is shown relative to the second fastest.

![Percentage gaps visualised](figures/Fig_diffPCT_restricted_vertical_limits.png?raw=true)

The most recent extreme domination in qualifying, was during the first three seasons of the V6-Hybrid-Engines, where Mercedes almost had a 1% qualifying pace advantage across three straight seasons, but is incomporable to the the late 1980s and early 1990s seasons of McLaren and Williams teams, whom were pusing towards 2%. While Alfa Romeo and Ferrari had significant advantages in the 1950s, a period with few constructors.
This method does exemplify the biggest difference on absolute time, but does not take into account if perhaps _two_ teams are leagues above the rest and only battling with eachother, _The Percentage Advantage_ would not be great and thus not materialise with this method.

## Standardisation of qualifying times (Z-Test)

Standard scores or Z-Scores, instead finds the standard deviation of all times (Only best time of each team). Which then scales the dots by how many standard deviations each team deviates from the average. This allows more than one team to be very far ahead of the rest, because this approach better presents each carmakers gap to _the average performance of the whole field_ rather than just the closest opponent.

![Standard Scores (Z-Scores) visualised](figures/Fig_Z_Scores_restricted_vertical_limits.png?raw=true)

Williams and McLaren of the late-1980s and early-1990s are still dominant, but Alfa Romeo and Ferrari in the 1950s lose their gap by quite a margin. Another notable appearance is 2020 Mercedes, a vehicle many fans remembers as a dominant force no one could touch. This model does show that this season Mercedes had an advantage on par with their 2014-2016 advantage. 

## Robust standardisation of qualifying times (Robust Z-Test)

The above approach uses all data, but also allows all data to be equally impactful to the dataset, thus allowing anomalies to skew data in one direction and modify the standard deviation used to quantify the standard scores.

A robust method, instead uses the median and eliminates the extreme impact of an anomaly like a backmarker team not in contention with any other teams.

![Robust Standard Scores (Robust-Z-Scores) visualised](figures/Fig_Robust_Z_Scores_restricted_vertical_limits.png?raw=true)

The 1975 Maki team immediately jumps to a standard deviation from less than 5 in a regular Z-Test to beyond 20 in the robust Z-Test. This absolute increase in values is prominent in almost all seasons as far more teams are closer to five robust-standard-deviatons, compared to only 2 in the normal method. To my surprise did the 2020 Mercedes jump ahead of any other Mercedes car, even though their percentage advantage was closer to 0.3% - this is a result of the remaining field being very close to another while Mercedes' gap to that field was proportionally large. Another notable surprise to me, is that Ferrari does not have a great advantage to the field in 2004, even though they had a notable gap in percentages. Signalling that the 2004 field was very spread out. While the 2000 season had bot McLaren and Ferrari duke it ou all year while being heads above the rest.

### So which F1 car is the most dominant qualifier?
I had personally expected the Red Bull RB6 from 2010 to appear as one of the best qualifying cars ever. The Red Bull RB7 from 2011 has more complete stat record and less fumbles to attain a near-perfect qualifying statistic, but to those who watched back then I often feel we all agree that RB6 was a car that made you lose hope, because when it did well - its gap was always too big. Instead the more intact statistical methods I use, further back it falls. Perhaps I am only thinking of te 2014-2016 Mercedes vehicles the same way, because I had already experienced _that_ shock from 2010 and 2011 Red Bull.

In absolute numbers, it is between McLaren and Williams of the late 1980s and early 1990s. The 1988 McLaren **MP4/4** has a qualifyin pace advantage of 1.48% to their nearest competitor, the 1989 McLaren **MP4/5** has a near identical advantage of 1.44%, while 1992 Williams **FW14B** is 1.59% and an incredible 1.80% for the 1993 Williams **FW15C**. These are values only seen since the 1950s and from Ferrari in 1961.

When adjusting for field pace (Z-Tests), are the advantages shuffled a bit, the differences between teams in the early days of F1 are not that extreme when considering how spread out all of the F1 teams are, being a midfielder who gains a lot of time will not necessarily grant you _reward you that much_. The FW14B is the car that deviates most from its respective competitors, while MP4/4 and FW15C are largely indentical.

When further adjusting to the **Robust-Z-Test** to diminish the impact of very slow teams, are these ratings intact for the teams around the 1990 mark - except for the FW14B which jumps to an incredible 3.22 standard deviations away from the median team's peformance, the greatest difference in Formula 1 history by a great margin.


Based on Z-scores and absolute percentage advantages, are the FW14B and FW15C in my opinion the greatest Formula 1 qualifying cars ever made.

### Weaknesses of the approaches used.

The 1988 McLaren qualifying advantage to the rest of its field, is smaller than what the team had in its three of its next four seasons; **1989 (MP4/5)**, 1990 (MP5/5B), **1991 (MP4/6)** and **1992 (MP4/6B)** - this is an absolute shock to me, but it does make sense because many new teams were entering F1 during this period with operations they were not prepared for, **a large increase in slow entries/anomalies _will_ weaken the robust-Z-Test as the times set by newly establised and slower teams will distribute qualifying times into; _new entries_ trying to catch up which are clearly gapped by the _existing_ field.** The robust method can handle a few anomalies, but two separate groups of data skews it so one standard deviation covers a greater time span - consequently will the top qualifiers have a greater Z-Score.

#
# Data acquisition
If you are a fan of the totally not borings layout steps for the scientific method, I advise you to read this part. To your important information, this part of this scientific project, was not written with passionate love for the most repeated standard procedure known to manking and I was very thorough to do it correctly the first time, so I won't have to do it again.

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
     - race results  1
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

## Data not used
- 1950-1960 Indianapolis 500
 - Only Nino Farina entered the Indianapolis 500 while driving a full season in F1, while most Indianapolis 500 teams did not participate in F1 at all. Thus are these results not included in the analysis.
