# modernF1
Hobbyist project on historical trends in Formula 1 and providing insights, where modern motorsport data-journalism usually neglects important factors.

### Upcoming content.
- Driver specific stats.

# Table Of Contents

1. [Qualification Dominance](https://github.com/92FO/modernF1/edit/main/README.md#1-qualification-dominance)  
   1.1. [Percentage pace advantage to closest competitor](https://github.com/92FO/modernF1/edit/main/README.md#11-percentage-pace-advantage-to-closest-competitor)  
   1.2. [Standard score (Z-Test) advantage of the field](https://github.com/92FO/modernF1/edit/main/README.md#standardisation-of-qualifying-times-z-test)  
   1.3. [Robust standard score (Robust Z-Test) advantage to the field](https://github.com/92FO/modernF1/edit/main/README.md#robust-standardisation-of-qualifying-times-robust-z-test)

# 1. Qualification Dominance
In countless of motorsport journalistic publications, reddit posts and other hobbyists I often see them exclusively use the overall rate of attaining pole position as a metric for how fast a car was at qualifying, without taking into consideration that this car could have gotten its statistic not in a dominant fashion. Other times are such opinions aided by converting gaps in qualifying times between cars into percentage units - which is quantifiable measure and far more robust to estimate _how fast_ a team is. But even, I still do not think this is good enough.


## 1.1. Percentage pace advantage to closest competitor
On average the top team acquires pole most frequently or are within 0.3% of the pole time in every qualification session, providing a seasonal average of around 0.15% away from the pole time. The advantage estimate is how much lower this average value is to the closest competitors averae. Lets say the second fastest team has a score of 0.7% compared to your 0.15%, that is a difference of 0.55%. This difference is displayed below, were the fastest teams' score is shown relative to the second fastest.

![Percentage gaps visualised](figures/Fig_diffPCT_restricted_vertical_limits.png?raw=true)

The most recent extreme domination in qualifying, was during the first three seasons of the V6-Hybrid-Engines, where Mercedes almost had a 1% qualifying pace advantage across three straight seasons, but is incomporable to the the late 1980s and early 1990s seasons of McLaren and Williams teams, whom were pusing towards 2%. While Alfa Romeo and Ferrari had significant advantages in the 1950s, a period with few constructors.
This method does exemplify the biggest difference on absolute time, but does not take into account if perhaps _two_ teams are leagues above the rest and only battling with each other, _The Percentage Advantage_ would not be great and thus not materialise with this method.

## 1.2. Standard score (Z-Test) advantage of the field

Standard scores or Z-Scores, instead finds the standard deviation of all times (Only best time of each team). Which then scales the dots by how many standard deviations each team deviates from the average. This allows more than one team to be very far ahead of the rest, because this approach better presents each carmakers gap to _the average performance of the whole field_ rather than just the closest opponent.

![Standard Scores (Z-Scores) visualised](figures/Fig_Z_Scores_restricted_vertical_limits.png?raw=true)

Williams and McLaren of the late-1980s and early-1990s are still dominant, but Alfa Romeo and Ferrari in the 1950s lose their gap by quite a margin. Another notable appearance is 2020 Mercedes, a vehicle many fans remembers as a dominant force no one could touch. This model does show that this season Mercedes had an advantage on par with their 2014-2016 advantage. 

## 1.3. Robust standard score (Robust Z-Test) advantage to the field

The above approach uses all data, but also allows all data to be equally impactful to the dataset, thus allowing anomalies to skew data in one direction and modify the standard deviation used to quantify the standard scores.

A robust method, instead uses the median and eliminates the extreme impact of an anomaly like a backmarker team not in contention with any other teams.

![Robust Standard Scores (Robust-Z-Scores) visualised](figures/Fig_Robust_Z_Scores_restricted_vertical_limits.png?raw=true)

The 1975 Maki team immediately jumps to a standard deviation from less than 5 in a regular Z-Test to beyond 20 in the robust Z-Test. This absolute increase in values is prominent in almost all seasons as far more teams are closer to five robust-standard-deviations, compared to only 2 in the normal method. To my surprise did the 2020 Mercedes jump ahead of any other Mercedes car, even though their percentage advantage was closer to 0.3% - this is a result of the remaining field being very close to another while Mercedes' gap to that field was proportionally large. Another notable surprise to me, is that Ferrari does not have a great advantage to the field in 2004, even though they had a notable gap in percentages. Signalling that the 2004 field was very spread out. While the 2000 season had both McLaren and Ferrari duke it ou all year while being heads above the rest.

### which F1 car is the most dominant qualifier?
I had personally expected the Red Bull RB6 from 2010 to appear as one of the best qualifying cars ever. The Red Bull RB7 from 2011 has a more complete stat record and fumbled fewer times to attain a near-perfect qualifying statistic, but that RB6 was a car that made you lose hope, because when it did well - its gap was always so big that you had no real expectations for things to turn against them. Instead the more intact statistical methods I use, the RB6 falls further back in relation to the alltime great F1 qualifiers, and even behind the 2011 (RB7) and 2013 (RB8) cars.

In absolute numbers, it is between McLaren and Williams of the late 1980s and early 1990s. The 1988 McLaren **MP4/4** has a qualifying pace advantage of 1.48% to their nearest competitor, the 1989 McLaren **MP4/5** has a near identical advantage of 1.44%, while 1992 Williams **FW14B** is 1.59% and an incredible 1.80% for the 1993 Williams **FW15C**. These are values only seen since the 1950s and from Ferrari in 1961.

When adjusting for field pace (Z-Tests), are the advantages shuffled a bit, the differences between teams in the early days of F1 are not that extreme when considering how spread out all of the F1 teams are, being a midfielder who gains a lot of time will not necessarily grant you _reward you that much_. The FW14B is the car that deviates most from its respective competitors, while MP4/4 and FW15C are largely identical.

When further adjusting to the **Robust-Z-Test** to diminish the impact of very slow teams, are these ratings intact for the teams around the 1990 mark - except for the FW14B which jumps to an incredible 3.22 standard deviations away from the median team's performance, the greatest difference in Formula 1 history by a great margin.


Based on Z-scores and absolute percentage advantages, are the FW14B and FW15C in my opinion the greatest Formula 1 qualifying cars ever made.

### Weaknesses of the approaches used.

The 1988 McLaren qualifying advantage to the rest of its field, is smaller than what the team had in three of its next four seasons; **1989 (MP4/5)**, 1990 (MP5/5B), **1991 (MP4/6)** and **1992 (MP4/6B)** - this is an absolute shock to me, but it does make sense because many new teams were entering F1 during this period with operations they were not prepared for, **a large increase in slow entries/anomalies _will_ weaken the robust-Z-Test as the times set by newly established and slower teams will distribute qualifying times into; _new entries_ trying to catch up which are clearly gapped by the _existing_ field.** The robust method can handle a few anomalies, but two separate groups of data skews it so one standard deviation covers a greater time span - consequently will the top qualifiers have a greater Z-Score, giving an illusion of very strong development in the teams performance compared to the rest of the field. Likewise is the effect similar to how the 2010 Red Bull (RB6) falls behind the 2011 and 2013 cars during a period when three new teams entered F1.

Additionally are these data strictly seasonally dependent. There are instances of teams using their past years' car in the early races of the Formula 1 calendar, before introducing a finished chassis or their engine provider introduces a new engine. These are changes I have not addressed in this presentation.

#
# Data acquisition
If you are a fan of the totally not boring layout steps for the scientific method, I advise you to read this part. To your important information, this part of this scientific project, was not written with passionate love for the most repeated standard procedure known to mankind and I was very thorough to do it correctly the first time, so I won't have to do it again.

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
- **TODO:** Identify race starts that deviate from regulations.
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

Drivers used to be able to share a seat and swap during tire changes - this happened regularly in the earlier years of Formula 1 World Championship. So there are instances of drivers having multiple finish positions as they contributed in more than one car at the same race.

## Data not used
- 1950-1960 Indianapolis 500
- Only Nino Farina entered the Indianapolis 500 while driving a full season in F1, while most Indianapolis 500 teams did not participate in F1 at all. Thus are these results not included in the analysis.
