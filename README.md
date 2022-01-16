# PyBer_Analysis
Report prepared for Module 5 challenge by Hannah Wikum - January 2022

# Resources
Data Source: city_data.csv, ride_data_csv (provided)
Software: Python 3.7 Anaconda Development Environment with Matplotlib, Jupyter Notebook, Git Bash 2.34.1.windows.1
___
# Overview
## Background
This challenge was completed to analyze fares by city type over time for a ride sharing company to be presented to the CEO, V. Isualize. I was provided two CSV files with data by city and by ride. The city data file included the 120 city names, driver count per city, and the type of city. Much of this analysis revolves around the city type, which contained one of three options: urban, suburban, or rural. The ride data CSV also included 2,375 records for PyBer rides that occurred between January 1 - May 8, 2019. Each row contained the city name, date and time of the ride, total fare, and a 13 digit ride ID.

## Analysis
After inspecting the data, I merged the two files into a DataFrame using a left join to add the city data to the right of the ride data on the common column of city. I used a groupby to get the sum or counts for the following metrics:
  * total rides by city type
  * driver county by city type
  * total fares by city type

Below is a sample of my groupby code that I used to get the total rides by city type. In this case, I grouped the data in the pyber DataFrame by city type and then took a count of the unique ride IDs to find the total rides that occurred for each type of city:

`total_rides_by_type = pyber_data_df.groupby(["type"]).count()["ride_id"]`

After completing all three groupby statements, I also calculated the average fare per ride and average fare by driver (each by city type) so I could make a summary DataFrame.

Here is a look at all of the metrics I described above with formatting in the summary DataFrame:

![image](https://user-images.githubusercontent.com/93058069/149679497-be350ef6-2b86-4f7e-b6fb-d46c4b5aa2d2.png)

The final step of the analysis was to create a multiple ilne plot to show total weekly fares by city type by week. I used another groupby, as well as pivot tables, datetime datatype, resampling, and the df.plot() function to build a chart reflecting ride data from 1/1/19-4/28/19. The final chart can be seen in the 'Results' section.
___
# Results
After completing the analysis it was clear that there are a number of differences in the Pyber's ride-sharing data by city type, including the following:

* **Rural rides have higher fares.**
    As you can see in the summary chart in the 'Analysis' section above, the average (mean) fare per ride in rural cities is $34.62, which is 12% higher than suburban and 41% more than the average urban fares. The below chart shows another visual 
    
    _Box-and-Whisker Plot for Ride Fares by City Type_
    
    ![Fig3](https://user-images.githubusercontent.com/93058069/149680071-5721f978-6eb8-4a35-9c3c-a4ffdbf84082.png)



_describe the differences in ride-sharing data among the different city types using images and the multiple-line chart_

___
# Summary
Based on the results of the analysis, here are three recommendations for the CEO to address disparities among the city type:
  1.
  2.
  3.
