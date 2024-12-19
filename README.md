# F1_analytics
Hobbyist project on historical trends in Formula 1 and exploring deeper into data, where modern motorsport data-journalism does not necessarily take all conditions into consideration.

# Data acquisition
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

### Alternate meta data
 - Front Row sizes.
   - Old Autosport forum threads.
   - Result websites
	
## Data Merging of key information.
Ergast and f1db data are merged by using identifiers that are consistent on both datasets.  

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
