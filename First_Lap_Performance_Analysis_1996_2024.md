# The best performing Lap 0 / First Lap driver in Formula 1 World Championship.

In Formula 1's history, there are often some select race drivers who are spoken of as legends in their starts. Fernando Alonso as an example is often spoken of as the best starter in modern times - a status he especially got cemented after the 2011 Spanish GP, where he pulled off the most spectacular start I have ever seen. Starting fourth and navigating between the two monstrously dominant RB7 Red Bulls to take the lead into first turn.

Here I look at the available lap time data from 1996 to the end of 2024 season, to see what the total change in positions are between starting and finishing first lap.

# 1. Positions gained/lost on the first lap.
The initial anomaly is the data (Ergast) displays starting positions at grid position 0, which are cars starting from the pit-lane.

![Heat map of unfiltered starting positions and position change delta when starting second lap](figures/fig_d_L0_pos_heat_map.png?raw=true)

The singular case of Markus Winkelhock in the 2007 European Grand Prix is present, where he started in the pit lane (0), who then overtook more than half of the field by the end of the first lap. Because he was the only driver to change tyres to Extreme Wets by the end of the formation lap, being the only vehicle to start the race ready to tackle the immediately arriving rain shower.

## 1.1. Starting positions adjusted to actual race position
Here I translate the starting position to actual race position, because a driver may start at 10th grid slot, but driver in grid slot #9 may have withdrawn or start from the pit lane. This accounts for that gap and translates the drivers position to race position order. Additionally are starting positions at 0, pit lane starts taken account -- if multiple cars are starting from the pit lane, are their starting order sorted by their qualification results, as per FIA's F1 rule book.


![Heat map of unfiltered starting positions and position change delta when starting second lap](figures/fig_d_adj_L0_adj_heat_map.png?raw=true)

As for cases like in the 2007 European GP, where Markus Winkelhock overtook twelve cars in the first lap, it is not fair to consider his overtakes legitimate race condtion positions he won, as *every single* car he overtook, did infact enter the pits by the end of the first lap - as no one was equally equipped for racing in those conditions.

This figures still displays all first laps since 1996, but the number of positions gained/lost are reduced if the driver overtook someone who went into the pits or retired from the race.

## 1.2. Overtakes on retiring and pit stopping drivers excluded.

When accounting for positions gained/lost due to DNFs or pit stops are changes concentrating around the gained/lost value of 0.

![Heat map of filtered starting positions and position change delta when starting second lap, pit stop and DNF overtakes removed](figures/fig_d_pit_DNF_L0_adj_heat_map.png?raw=true)

The furthest back anyone has been to gain the lead was Robert Kubica in the 2008 Japanese Grand Prix at Fuji Speedway, where Hamilton was first to take the first corner, but locked up his brakes and pushed cars on the outside line very wide, this allowed Robert Kubica to take the lead ater the first lap.

# 2. Seasonal driver statistics.

Continuing from 1.2 with cleaned data, are all drivers' seasonal first lap performanced summarised into a dot each. For all horizontal axes, are the dots placed on the given drivers' average race position - when the race begins.

- **Top left**
  - Average number of positions gained or lost on the first lap, the average difference between Race start position and end of first lap position.

- **Top right**
  - Average number of positions gained or lost from others and their own retirements.

- **Bottom left**
  - Average number of positions gained or lost from others and their own pit stops.

- **Bottom right**
  - Average number of positions gained or lost, when DNFs and pit stops are accounted for. This is both their own DNFs and retirements, but also other drivers.

As expected, is the impact of positions lost from DNFs greatest in drivers that started races on average in strong positions, as a single retirement can cost them more than ten lost positions.


![Seasonal Lap 0 performance all entries sorted by drivers season](figures/fig_2x2_seasonal_NOT_filtered.png?raw=true)

In average positions gained or lost from pit stops, is there are a single instance of a driver gaining 11 positions on average in the first lap -- this is also the only instance of Markus Winkelhock entering a Formula 1 Grand Prix, where he was the only car to switch to Extreme Wet tyres after the formation lap, allowing him to gain eleven positions in one lap - all whom where drivers that took a pit stop at the end of the first lap.

Filtering it to be drivers who had at least five race starts for a season to be considered, cleans up the data by a great deal and makes it far more legible.

![More than five entries per season. Seasonal Lap 0 performance of all drivers](figures/fig_2x2_seasonal_filtered.png?raw=true)

Just like with the DNF figures (Top right), is there a similar bias in drivers who start close to the front to lose more positions to pit stops than those starting further that - this is as expected.

There is one extreme instance with an average starting position of ~18 that gains close to six places on the first lap, while none of it can be explained by either taking advantage of DNFs or retirements. When adjusted for these factors this drivers average first lap gain is still greater than four places. A value no other driver has even when considering their advantage of DNFs or pit stops.

Overall throughout the past ten or so Formula 1 seasons, I got my own impression that Kevin Magnussen was the best starter I had seen in Formula 1. There have been many instances were he had gained five or six positions by the time he began his second lap, a consistency I had a very stong gut feeling about. While I also held Antonion Giovinazzi to a similar regard. Likewise did Fernando Alonso pull off similar first laps in his less favourable years at McLaren when they were equipped with Honda engines.

# 2.1. Kevin Magnussen, Antonio Giovinazzi and Fernando Alonso

The main observation to make is that all of these drivers are in general performing well on the first lap, when considering *where* in relation to those who started on similar start positions. Alonso's 2006 season stands out strikingly alone in the plot adjusted for DNFs and pit stops. While his 2012 season had an actual average of -0.2, but when adjusting for DNFs and pit stops, it jumps up to 1.35 overtakes on average that season.

![Seasonal Lap 0 performance of Kevin Magnussen and Antonio Giovinazzi](figures/fig_2x2_seasonal_filtered_giovinazzi_kevin_magnussen_alonso.png?raw=true)

Kevin Magnussen and Giovinazzi are rather consistently in the top half relative to their start position, somewhat confirming my bias, I had personally an expectation their statistics would stand out mores significantly. The 2020 season of Giovinazzi I a

## 2.1.1. Data results: Kevin Magnussen, Antonio Giovinazzi and Fernando Alonso.

Table below presents season averages. Positive values signal positions gained, negative values signal positions lost.

$\text{Adjusted for pit and DNF} = \text{Position changes} - \text{Changes due to DNFs} - \text{Changes due to pit stops}$

| Driver_Season        |   Position changes |   Changes due to DNFs |   Changes due to pit stops |   Adjusted for pit and DNF |   Start Position |
|:---------------------|-------------------:|----------------------:|---------------------------:|---------------------------:|-----------------:|
| Alonso 2010          |              -1.11 |                  0.11 |                      -0.47 |                      -0.74 |             5.79 |
| Alonso 2021          |               0.05 |                  0.23 |                       0.36 |                      -0.55 |            10.41 |
| Alonso 2009          |              -0.53 |                 -0.41 |                       0.29 |                      -0.41 |             8.88 |
| Alonso 2017          |               0    |                  0.16 |                       0.21 |                      -0.37 |            12.68 |
| Alonso 2007          |              -0.29 |                  0    |                       0.06 |                      -0.35 |             3.18 |
| Kevin Magnussen 2018 |               0.24 |                  0.19 |                       0.19 |                      -0.14 |            10.29 |
| Giovinazzi 2019      |               0.67 |                  0.14 |                       0.52 |                       0    |            13.81 |
| Alonso 2001          |               0.71 |                  0.53 |                       0.18 |                       0    |            19.47 |
| Alonso 2024          |               0.33 |                  0.12 |                       0    |                       0.21 |             9.42 |
| Kevin Magnussen 2014 |              -0.68 |                  0.05 |                      -0.95 |                       0.21 |             8.79 |
| Alonso 2023          |               0.09 |                  0.14 |                      -0.36 |                       0.32 |             6.86 |
| Alonso 2005          |               0.26 |                  0.05 |                      -0.16 |                       0.37 |             3.95 |
| Alonso 2008          |               0.17 |                 -0.39 |                       0.11 |                       0.44 |             6.89 |
| Alonso 2014          |               0.68 |                  0.11 |                       0.11 |                       0.47 |             6.53 |
| Alonso 2011          |               0.63 |                  0.11 |                       0.05 |                       0.47 |             4.58 |
| Kevin Magnussen 2019 |               0.71 |                  0.1  |                       0.14 |                       0.48 |            11.9  |
| Kevin Magnussen 2023 |               0.86 |                 -0.05 |                       0.32 |                       0.59 |            15.05 |
| Giovinazzi 2021      |               0.5  |                  0.23 |                      -0.32 |                       0.59 |            13.59 |
| Kevin Magnussen 2017 |               1.2  |                  0.35 |                       0.05 |                       0.8  |            14.1  |
| Kevin Magnussen 2022 |               0.23 |                 -0.14 |                      -0.45 |                       0.82 |            12.82 |
| Alonso 2013          |               0.89 |                  0    |                       0.05 |                       0.84 |             6    |
| Alonso 2003          |               1.06 |                  0.19 |                       0    |                       0.88 |             7.88 |
| Kevin Magnussen 2016 |               0.95 |                  0.33 |                      -0.29 |                       0.9  |            17.1  |
| Alonso 2016          |               2.2  |                  0.4  |                       0.7  |                       1.1  |            12.1  |
| Kevin Magnussen 2024 |               1.27 |                  0.14 |                       0    |                       1.14 |            14.64 |
| Alonso 2006          |               1.33 |                  0.06 |                       0    |                       1.28 |             4.28 |
| Alonso 2012          |              -0.2  |                 -1.6  |                       0.05 |                       1.35 |             6.1  |
| Alonso 2004          |               1.44 |                  0.06 |                      -0.17 |                       1.56 |             7.56 |
| Alonso 2015          |               1.56 |                  0.22 |                      -0.22 |                       1.56 |            15.61 |
| Giovinazzi 2020      |               2.71 |                  0.41 |                       0.59 |                       1.71 |            16.65 |
| Kevin Magnussen 2020 |               2.41 |                  0.41 |                       0.18 |                       1.82 |            16.88 |