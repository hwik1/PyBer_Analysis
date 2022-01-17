# PyBer_Analysis
Report prepared for Module 5 challenge by Hannah Wikum - January 2022

# Resources
Data Source: city_data.csv, ride_data_csv (provided)

Software: Python 3.7 Anaconda Development Environment with Matplotlib, Jupyter Notebook, Git Bash 2.34.1.windows.1
___
# Overview
## Background
This challenge was completed to analyze fares by city type over time for PyBer, a ride sharing company, to be presented to the CEO, V. Isualize. I was provided two CSV files with data by city and by ride. The city data file included the 120 city names, driver count per city, and the type of city. Much of this analysis revolves around the city type, which contained one of three options: urban, suburban, or rural. The ride data CSV also included 2,375 records for PyBer rides that occurred between January 1 - May 8, 2019. Each row contained the city name, date and time of the ride, total fare, and a 13 digit ride ID.

## Analysis
After inspecting the data, I merged the two files into a DataFrame using a left join to add the city data to the right of the ride data on the common column of city. I used a groupby to get the sum or counts for the following metrics:
  * total rides by city type
  * driver count by city type
  * total fares by city type

Below is a sample of my groupby code that I used to get the total rides by city type. In this case, I grouped the data in the PyBer DataFrame by city type and then took a count of the unique ride IDs to find the total rides that occurred for each type of city:

`total_rides_by_type = pyber_data_df.groupby(["type"]).count()["ride_id"]`

After completing all three groupby statements, I also calculated the average fare per ride and average fare per driver (each by city type) so I could make a summary DataFrame.

Here is a look at all of the metrics I described above with formatting in the summary DataFrame:

   _Summary Metrics by City Type_
   
   ![image](https://user-images.githubusercontent.com/93058069/149679497-be350ef6-2b86-4f7e-b6fb-d46c4b5aa2d2.png)

The final step of the analysis was to create a multiple line plot to show total weekly fares by city type by week. I used another groupby, as well as pivot tables, datetime datatype, resampling, and the df.plot() function to build a chart reflecting ride data from 1/1/19-4/28/19. The final chart can be seen in the 'Results' section.
___
# Results
After completing the analysis it was clear that there are a number of differences in the PyBer's ride-sharing data by city type, including the following:

* **Total Rides:** The majority (68%) of PyBer's rides are coming from urban cities. Just over 26% came from suburban cities, while only 5% were from rural city types. A pie chart visually comparing ride percentage by city type is below. 

    _% of Total Rides by City Pie Chart_
    
    ![Fig6](https://user-images.githubusercontent.com/93058069/149700383-5293faa1-6d86-4c85-a867-4bae06ffe907.png)

* **Total Driver Count:** Urban cities have the most drivers.
    Urban cities not only had the most drivers, but the amount of urban drivers (2,405) actually outnumbered the number of rides taken in urban cities (1,625) during this time period. Rural areas had by far the least amount of drivers, as you can see in the pie chart below.
    
    _% of Total Drivers by City Type Pie Chart_
    
    ![Fig7](https://user-images.githubusercontent.com/93058069/149687438-2ff52748-4bb2-4c42-8e5e-ecabf4a2cbb0.png)

* **Total Fares:** Urban cities are driving 63% of PyBer's total revenue due to the high volume of rides. The percent of total fares is lower than the percent of total rides mentioned above (68% for urban cities) because the average fare per ride is lower. On the other hand, both rural and suburban cities are driving a higher percent of the total fares compared to percent of total rides because the average fare per ride in these city types is higher. The pie chart below illustrates the percent of total fares coming from each city type.

    _% of Total Fares by City Type Pie Chart_

    ![Fig5](https://user-images.githubusercontent.com/93058069/149690500-8a443016-e174-4481-8f0f-248b54ecdd27.png)

* **Average Fare per Ride:** Rural rides have higher average fares per ride.
    As you can see in the summary chart in the 'Analysis' section above, the average (mean) fare per ride in rural cities is $34.62, which is 12% higher than suburban and 41% more than the average urban fares. The below chart shows another visual using box and whisker plots to visually compare the fare results across city types. The median fare (orange line) for rural is clearly higher than suburban, which in turn is higher than urban.
    
    _Box and Whisker Plot for Ride Fares by City Type_
    
   ![Fig3](https://user-images.githubusercontent.com/93058069/149680071-5721f978-6eb8-4a35-9c3c-a4ffdbf84082.png)

* **Average Fare per Driver:** The average fare per driver is lowest in urban cities and highest in rural areas.
    Urban cities had the lowest average fare per driver at $16.57, driven by the amount of drivers. As mentioned above, some of the urban drivers didn't even complete a ride during this time period, but we still used the total urban driver count when dividing total fares by total drivers to get the average fare per driver.

* **Fare by City Type by Week:** When looking at fare data by city type by week, the three city types followed a somewhat similar profile (peak toward the end of February before tapering off the first week of March, but urban and suburban cities saw a steep decline in total fare during the first week of April that did not show up in the same way in rural cities. Urban and suburban cities saw a 66-68% week over week decline in total fares during the first week of April, but rural was only down 11% compared to the prior week. Overall, rural fares were much more stable across March and April than urban or suburban cities, as you can see in the multiple line chart below.

    _Total Fare by City Type by Week Line Chart_
    
    ![PyBer_fare_summary](https://user-images.githubusercontent.com/93058069/149689105-7a9d0ce4-2546-44e9-b82d-c8e371c9138f.png)
___
# Summary
Based on the results of the analysis, here are three recommendations for the CEO to address disparities among the city types:

  1. **Focus on hiring more rural drivers.** Although it is a small portion of the business in terms of total fares, rural drivers are under-represented. Rural drivers make up only 3% of PyBer's total driver count, but supported 5% of rides and 7% of total fares. There were 1.6 rural rides per driver in this data compared to urban cities where the number of drivers outnumbered the number of total rides.

  2. **Change the calculation method for average fare per driver.** Instead of calculating average fare per driver using _total count_ of drivers, calculate the average using drivers by city type _who completed one or more rides_. With the current calculation, it looks like urban drivers have a very low average fare per driver, but we would not expect drivers who did not complete a ride to get a fare credited to them. Assuming a unique driver completed each of the 1,625 rides, the average fare per driver goes from $16.57 to $24.53 ($39,854.38/1,625). That would help tell a more realistic story.

  3. **Add more data to round out the story.** Include data for the average length of trip (distance and/or minutes) to help understand the average fare per ride discrepancy. Are average rural fares higher because there are fewer drivers to fulfill the ride request? Or do the rural trips require drivers to cover more distance in a longer time, hence the higher fare? Layering on average distance or average time per trip would help us understand why the average fare per ride is so different across city types. 
