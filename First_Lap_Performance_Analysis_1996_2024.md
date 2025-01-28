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


![Seasonal Lap 0 performance all entries sorted by drivers season](figures/fig_2x2_seasonal_NOT_filtered_.png?raw=true)

In average positions gained or lost from pit stops, is there are a single instance of a driver gaining 11 positions on average in the first lap -- this is also the only instance of Markus Winkelhock entering a Formula 1 Grand Prix, where he was the only car to switch to Extreme Wet tyres after the formation lap, allowing him to gain eleven positions in one lap - all whom where drivers that took a pit stop at the end of the first lap.

Filtering it to be drivers who had at least five race starts for a season to be considered, cleans up the data by a great deal and makes it far more legible.

![More than five entries per season. Seasonal Lap 0 performance of all drivers](figures/fig_2x2_seasonal_filtered_.png?raw=true)

Just like with the DNF figures (Top right), is there a similar bias in drivers who start close to the front to lose more positions to pit stops than those starting further that - this is as expected.

There is one extreme instance with an average starting position of ~18 that gains close to six places on the first lap, while none of it can be explained by either taking advantage of DNFs or retirements. When adjusted for these factors this drivers average first lap gain is still greater than four places. A value no other driver has even when considering their advantage of DNFs or pit stops.

Overall throughout the past ten or so Formula 1 seasons, I got my own impression that Kevin Magnussen was the best starter I had seen in Formula 1. There have been many instances were he had gained five or six positions by the time he began his second lap, a consistency I had a very stong gut feeling about. While I also held Antonion Giovinazzi to a similar regard. Likewise did Fernando Alonso pull off similar first laps in his less favourable years at McLaren when they were equipped with Honda engines.

# 2.1. Kevin Magnussen, Antonio Giovinazzi and Fernando Alonso

The main observation to make is that all of these drivers are in general performing well on the first lap, when considering *where* in relation to those who started on similar positions. Alonso's 2006 season stands out strikingly alone in the plot adjusted for DNFs and pit stops, overtaking 1.33 cars per race on average and is still a whopping 1.28 when adjusted for DNFs/pits. While his 2012 season had an actual average of -0.2, but excluding entires where he retired or pitted on the first lap, it jumps to 1.50 overtakes on average that year.

![Seasonal Lap 0 performance of Kevin Magnussen and Antonio Giovinazzi](figures/fig_2x2_seasonal_filtered_giovinazzi_kevin_magnussen_alonso.png?raw=true)

Kevin Magnussen and Giovinazzi are rather consistently in the top half relative to their start position, somewhat confirming my bias, I had personally an expectation their statistics would stand out mores significantly. The 2020 season of Giovinazzi came to me as expected, but I had the impression he had performed better in 2021.

## 2.1.1. Data results: Kevin Magnussen, Antonio Giovinazzi and Fernando Alonso.

Table below presents season averages. Positive values signal positions gained, negative values signal positions lost.

$\text{Adjusted for pit and DNF} = \text{Position changes} - \text{Changes due to DNFs} - \text{Changes due to pit stops}$

<table><thead><tr><th>Season</th><th>Driver</th><th>d (Position change)</th><th>d (DNFs)</th><th>d (Pit stops)</th><th>d (DNF / Pit adjusted)</th><th>Start Position</th></tr></thead><tbody><tr><td rowspan="rowspan_placeholder_2010">2010</td><td>Alonso</td><td>-1.11</td><td>0.11</td><td>-0.47</td><td>-0.65</td><td>5.79</td></tr><tr><td rowspan="rowspan_placeholder_2021">2021</td><td>Alonso</td><td>0.05</td><td>0.23</td><td>0.36</td><td>-0.55</td><td>10.41</td></tr><tr><td rowspan="rowspan_placeholder_2009">2009</td><td>Alonso</td><td>-0.53</td><td>-0.41</td><td>0.29</td><td>-0.44</td><td>8.88</td></tr><tr><td rowspan="rowspan_placeholder_2007">2007</td><td>Alonso</td><td>-0.29</td><td>0.00</td><td>0.06</td><td>-0.31</td><td>3.18</td></tr><tr><td rowspan="rowspan_placeholder_2018">2018</td><td>Kevin Magnussen</td><td>0.24</td><td>0.19</td><td>0.19</td><td>-0.21</td><td>10.29</td></tr><tr><td rowspan="rowspan_placeholder_2017">2017</td><td>Alonso</td><td>0.00</td><td>0.16</td><td>0.21</td><td>-0.12</td><td>12.68</td></tr><tr><td rowspan="rowspan_placeholder_2019">2019</td><td>Giovinazzi</td><td>0.67</td><td>0.14</td><td>0.52</td><td>0.00</td><td>13.81</td></tr><tr><td rowspan="rowspan_placeholder_2001">2001</td><td>Alonso</td><td>0.71</td><td>0.53</td><td>0.18</td><td>0.00</td><td>19.47</td></tr><tr><td rowspan="rowspan_placeholder_2023">2023</td><td>Kevin Magnussen</td><td>0.86</td><td>-0.05</td><td>0.32</td><td>0.11</td><td>15.05</td></tr><tr><td rowspan="rowspan_placeholder_2014">2014</td><td>Kevin Magnussen</td><td>-0.68</td><td>0.05</td><td>-0.95</td><td>0.12</td><td>8.79</td></tr><tr><td rowspan="rowspan_placeholder_2024">2024</td><td>Alonso</td><td>0.33</td><td>0.12</td><td>0.00</td><td>0.21</td><td>9.42</td></tr><tr><td rowspan="rowspan_placeholder_2005">2005</td><td>Alonso</td><td>0.26</td><td>0.05</td><td>-0.16</td><td>0.39</td><td>3.95</td></tr><tr><td rowspan="rowspan_placeholder_2023">2023</td><td>Alonso</td><td>0.09</td><td>0.14</td><td>-0.36</td><td>0.40</td><td>6.86</td></tr><tr><td rowspan="rowspan_placeholder_2021">2021</td><td>Giovinazzi</td><td>0.50</td><td>0.23</td><td>-0.32</td><td>0.47</td><td>13.59</td></tr><tr><td rowspan="rowspan_placeholder_2014">2014</td><td>Alonso</td><td>0.68</td><td>0.11</td><td>0.11</td><td>0.47</td><td>6.53</td></tr><tr><td rowspan="rowspan_placeholder_2008">2008</td><td>Alonso</td><td>0.17</td><td>-0.39</td><td>0.11</td><td>0.47</td><td>6.89</td></tr><tr><td rowspan="rowspan_placeholder_2011">2011</td><td>Alonso</td><td>0.63</td><td>0.11</td><td>0.05</td><td>0.47</td><td>4.58</td></tr><tr><td rowspan="rowspan_placeholder_2019">2019</td><td>Kevin Magnussen</td><td>0.71</td><td>0.10</td><td>0.14</td><td>0.50</td><td>11.90</td></tr><tr><td rowspan="rowspan_placeholder_2017">2017</td><td>Kevin Magnussen</td><td>1.20</td><td>0.35</td><td>0.05</td><td>0.75</td><td>14.10</td></tr><tr><td rowspan="rowspan_placeholder_2003">2003</td><td>Alonso</td><td>1.06</td><td>0.19</td><td>0.00</td><td>0.80</td><td>7.88</td></tr><tr><td rowspan="rowspan_placeholder_2013">2013</td><td>Alonso</td><td>0.89</td><td>0.00</td><td>0.05</td><td>0.84</td><td>6.00</td></tr><tr><td rowspan="rowspan_placeholder_2022">2022</td><td>Kevin Magnussen</td><td>0.23</td><td>-0.14</td><td>-0.45</td><td>0.84</td><td>12.82</td></tr><tr><td rowspan="2">2016</td><td>Kevin Magnussen</td><td>0.95</td><td>0.33</td><td>-0.29</td><td>0.88</td><td>17.10</td></tr><tr><td>Alonso</td><td>2.20</td><td>0.40</td><td>0.70</td><td>1.00</td><td>12.10</td></tr><tr><td rowspan="rowspan_placeholder_2024">2024</td><td>Kevin Magnussen</td><td>1.27</td><td>0.14</td><td>0.00</td><td>1.19</td><td>14.64</td></tr><tr><td rowspan="rowspan_placeholder_2006">2006</td><td>Alonso</td><td>1.33</td><td>0.06</td><td>0.00</td><td>1.28</td><td>4.28</td></tr><tr><td rowspan="rowspan_placeholder_2020">2020</td><td>Giovinazzi</td><td>2.71</td><td>0.41</td><td>0.59</td><td>1.50</td><td>16.65</td></tr><tr><td rowspan="rowspan_placeholder_2012">2012</td><td>Alonso</td><td>-0.20</td><td>-1.60</td><td>0.05</td><td>1.50</td><td>6.10</td></tr><tr><td rowspan="rowspan_placeholder_2004">2004</td><td>Alonso</td><td>1.44</td><td>0.06</td><td>-0.17</td><td>1.65</td><td>7.56</td></tr><tr><td rowspan="rowspan_placeholder_2020">2020</td><td>Kevin Magnussen</td><td>2.41</td><td>0.41</td><td>0.18</td><td>1.80</td><td>16.88</td></tr><tr><td rowspan="rowspan_placeholder_2015">2015</td><td>Alonso</td><td>1.56</td><td>0.22</td><td>-0.22</td><td>1.92</td><td>15.61</td></tr></table>


# 2.2. Red Bull (2021-2024), Max Verstappen and Sergio Perez

Like in Fernando Alonso's good years, does Max Verstappen consistently perform like the best who start at similar positions. His 2021 season is especially notworthy, his only first lap retirement of te year lowers his overall seasonal value by -0.82 and his first lap pit stops reduces his position by -0.27 on average. When these races are excluded does he overtake 0.43 cars per race on the first lap, with a starting position that only allows him to overtake 1-2 cars per race. A number Perez narrowly tops in the same year of 0.43, when he had seven cars to overtake on average.

![Seasonal Lap 0 performance of Max and Sergio](figures/fig_2x2_seasonal_filtered_max_verstappen_perez.png?raw=true)

In their years together, has Max Verstappen on average throughout the season gained positions, when his own DNFs and retirements are excluded, but also his overtakes on other cars. In 2023 and 2024 - Serio Perez generally lost positions even when he started on average around 9th place.

## 2.2.1. Seasonal results: Max Verstappen and Sergio Perez in Red Bull Racing (2021-2024)


<table><thead><tr><th style="text-align: left;">Season</th><th style="text-align: left;">Driver</th><th style="text-align: right;">d (Position change)</th><th style="text-align: right;">d (DNFs)</th><th style="text-align: right;">d (Pit stops)</th><th style="text-align: right;">d (DNF / Pit adjusted)</th><th style="text-align: right;">Start Position</th></tr></thead><tbody><tr><td rowspan="2" style="text-align: left;">2021</td><td style='text-align: left;'>Max Verstappen</td><td style='text-align: right;'>-0.73</td><td style='text-align: right;'>-0.82</td><td style='text-align: right;'>-0.27</td><td style='text-align: right;'>0.40</td><td style='text-align: right;'>2.86</td></tr><tr><td style='text-align: left;'>Perez</td><td style='text-align: right;'>0.00</td><td style='text-align: right;'>-0.55</td><td style='text-align: right;'>0.09</td><td style='text-align: right;'>0.43</td><td style='text-align: right;'>8.00</td></tr><tr><td rowspan="2" style="text-align: left;">2022</td><td style='text-align: left;'>Max Verstappen</td><td style='text-align: right;'>0.45</td><td style='text-align: right;'>0.09</td><td style='text-align: right;'>0.00</td><td style='text-align: right;'>0.33</td><td style='text-align: right;'>3.36</td></tr><tr><td style='text-align: left;'>Perez</td><td style='text-align: right;'>-0.50</td><td style='text-align: right;'>0.09</td><td style='text-align: right;'>-0.68</td><td style='text-align: right;'>0.20</td><td style='text-align: right;'>4.82</td></tr><tr><td rowspan="2" style="text-align: left;">2023</td><td style='text-align: left;'>Max Verstappen</td><td style='text-align: right;'>0.32</td><td style='text-align: right;'>0.05</td><td style='text-align: right;'>0.05</td><td style='text-align: right;'>0.24</td><td style='text-align: right;'>3.18</td></tr><tr><td style='text-align: left;'>Perez</td><td style='text-align: right;'>-0.73</td><td style='text-align: right;'>-0.59</td><td style='text-align: right;'>-0.32</td><td style='text-align: right;'>-0.19</td><td style='text-align: right;'>9.23</td></tr><tr><td rowspan="2" style="text-align: left;">2024</td><td style='text-align: left;'>Max Verstappen</td><td style='text-align: right;'>0.33</td><td style='text-align: right;'>0.00</td><td style='text-align: right;'>0.00</td><td style='text-align: right;'>0.33</td><td style='text-align: right;'>3.54</td></tr><tr><td style='text-align: left;'>Perez</td><td style='text-align: right;'>-0.46</td><td style='text-align: right;'>-0.42</td><td style='text-align: right;'>0.00</td><td style='text-align: right;'>-0.05</td><td style='text-align: right;'>9.38</td></tr></table>



# 2.3. Ferrari (2010-2014), Fernando Alonso, Felipe Massa and Kimi Raikkonen
![Seasonal Lap 0 performance of Ferrari (2010-2014)](figures/fig_2x2_seasonal_filtered_alonso_Massa_raikkonen.png?raw=true)


## 2.3.1. Seasonal results: Fernando Alonso, Felipe Massa and Kimi Raikkonen (2010-2014)
<table ><thead><tr><th>Season</th><th>Driver</th><th>d (Position change)</th><th>d (DNFs)</th><th>d (Pit stops)</th><th>d (DNF / Pit adjusted)</th><th>Start Position</th></tr></thead><tbody><tr><td rowspan="2">2010</td><td>Alonso</td><td>-1.11</td><td>0.11</td><td>-0.47</td><td>-0.65</td><td>5.79</td></tr><tr><td>Massa</td><td>-1.32</td><td>-0.47</td><td>-1.79</td><td>1.13</td><td>7.74</td></tr><tr><td rowspan="2">2011</td><td>Alonso</td><td>0.63</td><td>0.11</td><td>0.05</td><td>0.47</td><td>4.58</td></tr><tr><td>Massa</td><td>0.42</td><td>0.05</td><td>0.00</td><td>0.37</td><td>5.79</td></tr><tr><td rowspan="2">2012</td><td>Alonso</td><td>-0.20</td><td>-1.60</td><td>0.05</td><td>1.50</td><td>6.10</td></tr><tr><td>Massa</td><td>1.00</td><td>0.35</td><td>-0.50</td><td>1.33</td><td>9.85</td></tr><tr><td rowspan="2">2013</td><td>Alonso</td><td>0.89</td><td>0.00</td><td>0.05</td><td>0.84</td><td>6.00</td></tr><tr><td>Massa</td><td>0.26</td><td>0.00</td><td>0.16</td><td>0.11</td><td>7.95</td></tr><tr><td rowspan="2">2014</td><td>Alonso</td><td>0.68</td><td>0.11</td><td>0.11</td><td>0.47</td><td>6.53</td></tr><tr><td>Raikkonen</td><td>0.42</td><td>-0.11</td><td>0.05</td><td>0.50</td><td>9.37</td></tr></table>


# 2.4. The greatest first lap performers ever. Jos Verstappen, Jan Magnussen and Scott Speed


![Seasonal Lap 0 performance of Jos the Boss, Scott Speed and JMAG](figures/fig_2x2_seasonal_filtered_verstappen_speed_magnussen.png?raw=true)


<table><thead><tr><th style="text-align: left;">Season</th><th style="text-align: left;">Driver</th><th style="text-align: right;">d (Position change)</th><th style="text-align: right;">d (DNFs)</th><th style="text-align: right;">d (Pit stops)</th><th style="text-align: right;">d (DNF / Pit adjusted)</th><th style="text-align: right;">Start Position</th></tr></thead><tbody><tr><td rowspan="rowspan_placeholder_2006" style="text-align: left;">2006</td><td style='text-align: left;'>Speed</td><td style='text-align: right;'>1.17</td><td style='text-align: right;'>0.06</td><td style='text-align: right;'>0.28</td><td style='text-align: right;'>0.88</td><td style='text-align: right;'>16.17</td></tr><tr><td rowspan="rowspan_placeholder_1997" style="text-align: left;">1997</td><td style='text-align: left;'>Magnussen</td><td style='text-align: right;'>1.06</td><td style='text-align: right;'>0.47</td><td style='text-align: right;'>-0.18</td><td style='text-align: right;'>0.93</td><td style='text-align: right;'>15.82</td></tr><tr><td rowspan="rowspan_placeholder_2000" style="text-align: left;">2000</td><td style='text-align: left;'>Verstappen</td><td style='text-align: right;'>1.94</td><td style='text-align: right;'>0.71</td><td style='text-align: right;'>0.12</td><td style='text-align: right;'>1.12</td><td style='text-align: right;'>13.94</td></tr><tr><td rowspan="rowspan_placeholder_1996" style="text-align: 
left;">1996</td><td style='text-align: left;'>Verstappen</td><td style='text-align: right;'>1.31</td><td style='text-align: right;'>-0.25</td><td style='text-align: right;'>0.25</td><td style='text-align: right;'>1.64</td><td style='text-align: right;'>14.06</td></tr><tr><td rowspan="rowspan_placeholder_1997" style="text-align: left;">1997</td><td style='text-align: left;'>Verstappen</td><td style='text-align: right;'>2.82</td><td style='text-align: right;'>0.82</td><td style='text-align: right;'>0.18</td><td style='text-align: right;'>1.94</td><td style='text-align: right;'>19.65</td></tr><tr><td rowspan="rowspan_placeholder_2007" style="text-align: left;">2007</td><td style='text-align: left;'>Speed</td><td style='text-align: right;'>2.60</td><td style='text-align: right;'>0.10</td><td style='text-align: right;'>0.10</td><td style='text-align: right;'>2.25</td><td style='text-align: right;'>17.70</td></tr><tr><td rowspan="rowspan_placeholder_1998" style="text-align: left;">1998</td><td style='text-align: left;'>Magnussen</td><td style='text-align: right;'>3.57</td><td style='text-align: right;'>1.14</td><td style='text-align: right;'>-0.14</td><td style='text-align: right;'>2.83</td><td style='text-align: right;'>18.71</td></tr><tr><td rowspan="rowspan_placeholder_2001" style="text-align: left;">2001</td><td style='text-align: left;'>Verstappen</td><td style='text-align: right;'>5.76</td><td style='text-align: right;'>1.00</td><td style='text-align: right;'>0.18</td><td style='text-align: right;'>4.59</td><td style='text-align: right;'>18.00</td></tr></table>
