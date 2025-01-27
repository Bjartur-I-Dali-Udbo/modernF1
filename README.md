# modernF1

### Using historical Formula 1 data to visualise statistical information modern motorsport journalism lacks

This repository is an ongoing hobby project to provide answers to debates that are mostly unanswered. I pick one subject or myth commonoly raised in comment sections of discussion boards, which I 

## Projects
- [Qualifying Analysis of the best performing team entry (1950-2024)](https://github.com/Bjartur-I-Dali-Udbo/modernF1/blob/main/qualifying_analysis.md)


# 1. Data
If you are a fan of the totally not boring layout steps for the scientific method, I advise you to read this part. To your important information, this part of this project, was not written with passionate love for the most repeated standard procedure known to mankind and I was very thorough to do it correctly the first time, so I won't have to do it again.

## 1.1 Data Acquisition

Data is acquired from open source database projects that track historical Formula 1 World Championship data. While grid layouts are assembled manually.

### 1.1.1. Ergast API (Deprecated after 2024 season)
- https://ergast.com/mrd/
- Season List, Race Schedule  
- Qualifying Results, Sprint Qualifying Results  
- Lap Times, Pit Stops, Race Results, Finishing Status  
- Standings  
- Driver Information, Constructor Information, Circuit Information  


### 1.1.2. f1db Open Source Formula 1 Database
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

### 1.1.3. Non-database meta data.
Some data is not acquired in databases or must be scraped from fanmade webpages.

#### 1.1.3.1. Front Row conditions.
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

#### 1.1.3.2. Customised color schemes.
- Constructor plotting colours
  - Manually selected for most common colours used in teams history.
- Driver plotting colours.
  - Manually selected for the team they have been affiliated with for the longest time or a colour scheme familiar to the flag of their nationality.

## 1.2. Data Merging of key information.
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

## 1.3. Data not used
- 1950-1960 Indianapolis 500
  - Only Nino Farina entered the Indianapolis 500 while driving a full season in F1, while most Indianapolis 500 teams did not participate in F1 at all. Thus are these results not included in the analysis.
