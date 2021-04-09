# A Repository for Collecting Weather Data and Travel Routes for Vacation Planning Using APIs

## Project Overview
#### This project was completed to collect city specific weather data that will allow users to select a range of vacation destinations based on desired weather conditions.
The following steps were conducted in order to generate a final vacation itinerary for travelers.
1.  A list of 2,000 ***random*** latitudes and longitudes was generated.  By using the **citipy** module to identify the nearby city to the rendered coordinates, a list of **779** cities resulted.  
2.  A call was made to **OpenWeatherMap.org** with an API key that collected each city's geographic coordinates and weather conditions in **JSON (JavaScript Object Notation)** format.  This information was then parsed and added to a **Pandas** DataFrame, trimmed to a list of **715** located cities, and written to a *.csv* file.
3.  The recorded .csv file was then read into a new **Python** script in which the user is prompted to input the desired minimum and maximum temperature for their vacation destination.
4.  In this instance, 60°F was set for the minimum temperature and 95°F was set for the maximum temperature, resulting in a list of **379** cities.  Because there were three rows of data that were incomplete, those rows with null values were dropped and final list of **376** cities remained and were added to a new DataFrame with an additional column created to contain a ***Hotel Name*** for each city in the list.
5.  A call was then made to the **Google** gmaps and places to add the hotel name for each city to the DataFrame.  Any cities that did not show a hotel were dropped, and **348** cities remained on the list.  A new *.csv* file was written with the compiled data and an interactive map was generated with markers for each city in the list.
6.  This new .csv file was again read into a new **Python** DataFrame and plotted using **Google** gmaps.  From this map, four cities were selected and their latitude and longitude pairs were retrieved and captured in individual dataframes in order to use those values to generate a directions layer map using gmaps and directions.  In this instance driving directions were requested.
7.  A combined Itinerary DataFrame was made by concatenating each of the city DataFrames and was used to render a final interactive **Google Map** with markers and pop-ups.
 
#### Resources
- Data was collected from OpenWeatherMap.org through the use of an API key
- An API key was generated from Google Cloud Platform in order to use the Maps, Places, and Directions APIs
- Software: Python 3.7.9, Jupyter Notebook 6.1.4, Pandas 1.1.3, Numpy 1.17.0
 
## Results of the weather and mapping APIs
From the original 2,000 latitude and longitude pairs that were randomly generated, 779 cities were identified.  Of these 779 cities, 715 were matched to weather data from the OpenWeatherMap API.  In this exercise, four cities were chosen in the Northeast of the United States according to the desired weather parameters.  These were chosen from 348 cities that had a hotel registered with Google within 5 kilometers of the original randomly generated coordinates.  These cities with their hotel name and current weather conditions at the time of reporting are listed below:
1.  Bloomfield, NJ:  La Quinta Inn & Suites by Wyndham Clifton/Rutherford (current weather:clear sky and 60°F)
2.  Palmer, MA:  Wedgewood Motel (current weather: scattered clouds and 62°F)
3.  Norfolk, MA: Residence Inn by Marriott Boston Norwood/Canton (current weather: clear sky and 64°F)
4.  Plymouth, MA: Rodeway Inn Middleboro-Plymouth (current weather: clear sky and 62°F)



#### 1. Total Rides by City Type
Because of the dense population of cites categorized as ***urban***, total ride volume is inherently greater in these locations than in ***suburban*** or ***rural*** areas.  As shown in the summary dataframe below, the total number of rides in ***urban*** city types is **13 times greater** than the total number of rides in ***rural*** city types. 
#### 2. Total Drivers by City Type
Again, because of the population density being greater in ***urban*** areas, the total number of drivers is significantly greater than in ***rural*** city types.  Here we see an increase of **30 times** the number of drivers.  
#### 3. Total Fares by City Type
The total revenue generated by fares is directly related to the total number of rides.  As shown in the table above, we see almost **10 times** the revenue generated in ***urban*** versus ***rural*** city types.  

![PyBer_fare_summary.png](https://github.com/frostbrosracing/PyBer_Analysis/blob/main/analysis/PyBer_fare_summary.png)
#### 4. Average Fare per Ride by City Type
The average fare per ride is much more closely related than any of the other key metrics obtained in this analysis.  
#### 5. Average Fare per Driver by City Type
Some interesting observations can be made within this summary.  Here we see that even though there is such a significantly smaller revenue total, because there are so few drivers in ***rural*** city types, the average fare per driver is much greater than in ***urban*** city types.  It's here that the recommendations summarized below begin to take shape.

## PyBer Analysis Summary
Based on the analysis, it becomes clear that there's an underserved community in rural city neighborhoods by drivers.  As shown in the **Total Fare by City Type** chart above, ridership is fairly consistent for the period in the study.  This consistency is a key component that will provide a solid foundation for the company as it begins to explore opportunities to close the gap discovered in the coverage areas. 

In order to balance the distribution of driver coverage to different ride areas the following recommendations should be considered with the goal of **increasing overall company revenue**:

1.	A slight decrease in the overall cost to consumers using the PyBer service in rural city types will likely increase demand in those areas.  
2.	Based on the increased demand of rides generated from the adjusted prices in rural areas, it will be necessary to increase the driver availability in those areas.  By offering incentives to drivers who provide that coverage, the overall number of drivers will slightly decrease from the urban areas as they begin to provide service in the outlying areas.
3.	This decrease in total supply of drivers in urban areas will cause an increase in the demand and therefore justify an increase in the total fares, the average fare per driver and consequently help close the gap in total revenue between rural and urban city types.

By putting these recommendations in place, PyBer has the opportunity to increase overall revenue and also invest in **long-term rider loyalty** by gaining exposure to a new customer base previously unserved by the company.
