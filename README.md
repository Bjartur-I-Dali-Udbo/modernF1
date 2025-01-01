- [Planned content.](#planned-content)
- [1. Qualification Dominance](#1-qualification-dominance)
  - [1.1. Percentage pace advantage to closest competitor](#11-percentage-pace-advantage-to-closest-competitor)
  - [1.2. Standard score (Z-Test) advantage of the field](#12-standard-score-z-test-advantage-of-the-field)
  - [1.3. Robust standard score (Robust Z-Test) advantage to the field](#13-robust-standard-score-robust-z-test-advantage-to-the-field)
  - [1.4. which F1 car is the most dominant qualifier?](#14-which-f1-car-is-the-most-dominant-qualifier)
    - [1.4.1. Limitations of metods.](#141-limitations-of-metods)
- [2. Data](#2-data)
  - [2.1 Data Acquisition](#21-data-acquisition)
    - [2.1.1. Ergast API (Deprecated after 2024 season)](#211-ergast-api-deprecated-after-2024-season)
    - [2.1.2. f1db Open Source Formula 1 Database](#212-f1db-open-source-formula-1-database)
    - [2.1.3. Non-database meta data.](#213-non-database-meta-data)
      - [2.1.3.1. Front Row conditions.](#2131-front-row-conditions)
      - [2.1.3.2. Customised color schemes.](#2132-customised-color-schemes)
  - [2.2. Data Merging of key information.](#22-data-merging-of-key-information)
  - [2.3. Data not used](#23-data-not-used)



# Planned content.
- [x] Qualification Dominance
  - [x] Percentage lead.
  - [x] Z-Test means.
  - [x] Z-Test medians
  - [ ] Adapt to consider specific chassis designs.
  - [ ] Revision of sample data, to address the potentially negative impact on Z-Tests of new team entries that underperform.
- [ ] Driver statistics for specific conditions (In writing).
- [ ] Most successful Lap-1 drivers since 1996 (Conceptualisation phase).

# 1. Qualification Dominance
In multiple motorsport journalistic publications, user projects posted on reddit
and other analytical work I often see them exclusively use the overall rate of
attaining pole position as a metric for how fast a car was at qualifying, without
taking into consideration that this car could have gotten its statistic not in a
dominant fashion. Other times are such opinions aided by converting gaps in
qualifying times between cars into percentage units - which is quantifiable
measure and far more robust to estimate _how fast_ a team is. But I do not believe
this measure tells enough of a story to confidently state the most advantageous
Formula 1 car in qualifying. Here I will introduce Z-Tests that instead consider
the best time of every team, this builds a *range* where most teams fall into. This
is utilised to consider if one or more teams are considerably better than the rest.


## 1.1. Percentage pace advantage to closest competitor
On average the top team acquires pole most frequently or are within 0.3% of the pole
time in every qualification session, providing a seasonal average of around 0.15% away
from the pole time. The advantage estimate is how much lower this average value is
to the closest competitors averae. Lets say the second fastest team has a score of
0.7% compared to your 0.15%, that is a difference of 0.55%. This difference is
displayed below, were the fastest teams' score is shown relative to the second fastest.

![Percentage gaps visualised](figures/Fig_diffPCT_restricted_vertical_limits.png?raw=true)

The most recent extreme domination in qualifying, was during the first three seasons
of the V6-Hybrid-Engines, where Mercedes almost had a 1% qualifying pace advantage
across three straight seasons, but is incomporable to the the late 1980s and early
1990s seasons of McLaren and Williams teams, whom were pusing towards 2%.
While Alfa Romeoand Ferrari had significant advantages in the 1950s, a period with few constructors.
This method does exemplify the biggest difference on absolute time, but does not
take into account if perhaps _two_ teams are leagues above the rest and only battling
with each other, _The Percentage Advantage_ would not be great and thus not
materialise with this method.

## 1.2. Standard score (Z-Test) advantage of the field

Standard scores or Z-Scores finds the standard deviation of all times used
(Only best time of each team). Which scales the teams' times by how many standard
deviations they deviate from the average. This allows more than one team to
be very far ahead of the rest, because this approach better presents each carmakers
gap to _the average performance of the whole field_ rather than just the closest opponent.

For all qualifying sessions are the best times used for each team. This is regardless of what qualifying session the time was set. If a teams fastest lap was in Q2, then that time is used. 

$$Z = \frac{\overline X_i - \mu}{\sigma}$$
$$Z\text{: Standard Score}, \space \overline X_i \text{: Team i's best qualification time}, \space \mu\text{: Mean of all } \overline X \text{ times}, \space \sigma\text{: Standard deviation of sample}$$

Presented below is the mean Z-Score for every team across a season.

![Standard Scores (Z-Scores) visualised](figures/Fig_Z_Scores_restricted_vertical_limits.png?raw=true)

Williams and McLaren of the late-1980s and early-1990s are still dominant, but Alfa Romeo and Ferrari in the 1950s lose their gap by quite a margin. Another notable appearance is 2020 Mercedes, a vehicle many fans remembers as a dominant force no one could touch. This model does show that this season Mercedes had an advantage on par with their 2014-2016 advantage. 

## 1.3. Robust standard score (Robust Z-Test) advantage to the field

The above approach uses all data, but also allows all data to be equally impactful to the dataset, thus allowing anomalies to skew data in one direction and modify the standard deviation used to quantify the standard scores.

A robust method, instead uses the median and eliminates the extreme impact of an anomaly like a backmarker team not in contention with any other teams.

$$Z_r = \frac{\overline X_i - \mu}{\text{MAD} \cdot 1.4826}$$
$$Z_r\text{: Standard Score}, \space \overline X_i \text{: Team i's best qualification time}, \space \mu\text{: Median of all } \overline X \text{ times}, \space \text{MAD: Median Absolute Deviation}$$

Below is the median Z-Score for every team across a season.

![Robust Standard Scores (Robust-Z-Scores) visualised](figures/Fig_Robust_Z_Scores_restricted_vertical_limits.png?raw=true)

The 1975 Maki team immediately jumps to a standard deviation from less than 5 in a regular Z-Test to beyond 20 in the robust Z-Test. This absolute increase in values is prominent in almost all seasons as far more teams are closer to five robust-standard-deviations, compared to only 2 in the normal method. To my surprise did the 2020 Mercedes jump ahead of any other Mercedes car, even though their percentage advantage was closer to 0.3% - this is a result of the remaining field being very close to another while Mercedes' gap to that field was proportionally large. Another notable surprise to me, is that Ferrari does not have a great advantage to the field in 2004, even though they had a notable gap in percentages. Signalling that the 2004 field was very spread out. While the 2000 season had both McLaren and Ferrari duke it ou all year while being heads above the rest.

## 1.4. which F1 car is the most dominant qualifier?
I had personally expected the Red Bull RB6 from 2010 to appear as one of the best qualifying cars ever. The Red Bull RB7 from 2011 has a more complete stat record and fumbled fewer times to attain a near-perfect qualifying statistic, but that RB6 was a car that made you lose hope, because when it did well - its gap was always so big that you had no real expectations for things to turn against them. Instead the more intact statistical methods I use, the RB6 falls further back in relation to the alltime great F1 qualifiers, and even behind the 2011 (RB7) and 2013 (RB8) cars.

In absolute numbers, it is between McLaren and Williams of the late 1980s and early 1990s. The 1988 McLaren **MP4/4** has a qualifying pace advantage of 1.48% to their nearest competitor, the 1989 McLaren **MP4/5** has a near identical advantage of 1.44%, while 1992 Williams **FW14B** is 1.59% and an incredible 1.80% for the 1993 Williams **FW15C**. These are values only seen since the 1950s and from Ferrari in 1961.

When adjusting for field pace (Z-Tests), are the advantages shuffled a bit, the differences between teams in the early days of F1 are not that extreme when considering how spread out all of the F1 teams are, being a midfielder who gains a lot of time will not necessarily grant you _reward you that much_. The FW14B is the car that deviates most from its respective competitors, while MP4/4 and FW15C are largely identical.

When further adjusting to the **Robust-Z-Test** to diminish the impact of very slow teams, are these ratings intact for the teams around the 1990 mark - except for the FW14B which jumps to an incredible 3.22 standard deviations away from the median team's performance, the greatest difference in Formula 1 history by a great margin.

Based on Z-scores and absolute percentage advantages, are the FW14B and FW15C in my opinion the greatest Formula 1 qualifying cars ever made.

### 1.4.1. Limitations of metods.

The 1988 McLaren qualifying advantage to the rest of its field, is smaller than
what the team had in three of its next four seasons; **1989 (MP4/5)**, 1990 (MP5/5B),
**1991 (MP4/6)** and **1992 (MP4/6B)** - this is an absolute shock to me, but it does
make sense because many new teams were entering F1 during this period with operations
they were not prepared for, while the frontrunning teams were gaining significant pace during these years, **this large increase in slow entries/anomalies _will_ weaken the robust-Z-Test as the times set by newly established and slower teams will distribute qualifying times into; _new entries_ trying to catch up which are clearly gapped by the _existing_ field.** The robust method can handle a few anomalies, but two separate groups of data skews it so one standard deviation covers
a greater time span - consequently will the top qualifiers have a greater Z-Score, giving an illusion of very strong development in the teams performance compared to the rest of the field. Likewise is the effect similar to how the 2010 Red Bull (RB6) falls behind the 2011 and 2013 cars during a period when three new teams entered F1.

Additionally are these data strictly seasonally dependent. There are instances of
teams using their past years' car in the early races of the Formula 1 calendar,
before introducing a finished chassis or their engine provider introduces a new engine.
These are changes I have not addressed in this presentation.

# 2. Data
If you are a fan of the totally not boring layout steps for the scientific method, I advise you to read this part. To your important information, this part of this scientific project, was not written with passionate love for the most repeated standard procedure known to mankind and I was very thorough to do it correctly the first time, so I won't have to do it again.

## 2.1 Data Acquisition

Majority of data is acquired from open source database projects that track historical Formula 1 World Championship data. Some other data are assessed 

### 2.1.1. Ergast API (Deprecated after 2024 season)
- https://ergast.com/mrd/
- Season List, Race Schedule  
- Qualifying Results, Sprint Qualifying Results  
- Lap Times, Pit Stops, Race Results, Finishing Status  
- Standings  
- Driver Information, Constructor Information, Circuit Information  


### 2.1.2. f1db Open Source Formula 1 Database
- https://github.com/f1db/f1db
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

### 2.1.3. Non-database meta data.
Some data is not acquired in databases or must be scraped from fanmade webpages.

#### 2.1.3.1. Front Row conditions.
Formula 1 World Championship has introduced standardisations for grid rows at different times.
- 1950-1973, no uniform standard grid layout. 2, 3 and 4 cars lined up side-by-side possible.
  - Old Autosport forum threads.
  - Result websites.
  - Pictures of starting grids.
- 1974-1977, 2x2 cars lined up side by side.
  - 12 meters between cars.
- 1978-1980, 2x2 cars lined up side by side.
  - Grid distance increased to 14 meters. 
- 1981-1986, 1x1s1 rows.
  - 1 car on each row, position of cars on each row are interchanging between left and right lane - or vice versa.
  - Distance seperation is 7 meters.
  - Total distance between cars on same lane is 14 meters, same as prior to 1981.
- 1987-present, 1x1x1 rows.
  - Distance between cars increased to 8 meters, resulting in 16 meters between cars on same lane.

#### 2.1.3.2. Customised color schemes.
- Constructor plotting colours
  - Manually selected for most common colours used in teams history.
- Driver plotting colours.
  - Manually selected for the team they have been affiliated with for the longest time or a colour scheme familiar to the flag of their nationality.

## 2.2. Data Merging of key information.
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

## 2.3. Data not used
- 1950-1960 Indianapolis 500
- Only Nino Farina entered the Indianapolis 500 while driving a full season in F1, while most Indianapolis 500 teams did not participate in F1 at all. Thus are these results not included in the analysis.
