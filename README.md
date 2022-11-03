# Citi_Bike_Visualizations

## Contributor: Sam Espe

### Overview
This project was created as a submission for Homework #18 in Data Visualization and Analysis Boot Camp. The goal was to use Tableau Public to visualize data from the New York City CitiBike program. The link to my project on Tableau Public is here: https://public.tableau.com/app/profile/sam.espe8652/viz/NYCCitiBikeVisualizations/HowDoCasualUsersandMembersUseCitiBike

### Obtaining the Data
I obtained my data from the New York City CitiBike Data webpage: https://ride.citibikenyc.com/system-data. I was interested in exploring how the COVID-19 pandemic effected ridership, so I elected to use the data from September, 2018 through September, 2022. 

### Cleaning the Data
The CSV file for each month typically had over a million data points, and were too large to upload to GitHub or to use in their entirety in Tableau Public. To solve this problem, I used Python and Pandas in a Jupyter Notebook to clean the data and take a sample to analyze. 

The structure of the published data changed starting at the February, 2021 data set, so I had to create separate functions to clean the data, depending on when it was published. I used the functions to clean the data as well as to ensure that they would be compatible when I merged them to make a larger data set. 

For all of the months of data, I started by taking a random sample of 5,000 data points from each month of raw data. I chose to do the sampling before the cleaning in the interest of saving time and computing power. Cleaning more than a million data points took an inordinate amount of time, and the cleaning process did not remove a large proportion of the raw data. 

#### For data after January, 2021
Once I had the sample, I removed any entries with NaN values, as well as any duplicated entries. I removed columns I wasn't interested in, such as the ID of the starting and ending stations. Once the data were clean, I rounded the latitudes and longitudes to three decimal points. This helped make sure that bikes that started or ended at the same station were counted together, even if they were a few feet off from each other. Additionally, I added a column where I calculated the elapsed time for each ride to match with the data from before January of 2021. Finally, I added two columns at the end of the data frame, as a way to capture the total ridership for each month.

#### For data on or before January, 2021
I started renaming and rearranging the columns of the dataframe to match those of the data sets after January of 2021. These sets had the member or casual user data listed as "Customer" or "Subscriber", so I mapped subscribers as members, and customers as casual users. I then dropped the columns I wasn't interested in, rounded the latitudes and longitudes to three decimal places, and dropped any of the sampled data points that had NaN values or were duplicates. 

Once both sets of data were processed, I concatenated the dataframes together to make one, large data set, and then exported it as a CSV file to upload into Tableau Public.

### Visualizing the Data
I used Tableau Public to create many visualizations of the data, as well as to create two dashboards and one story that would be used to present to administrators at the CitiBike program. I used the latitude and longitude data to make a map that explored which stations were most popular to start trips at. I looked at total monthly ridership over my selected time period, how rides start times were distributed across the hours of the day and across the days of the week.

### Analysis of the Data

#### Dashboard 1 - How Do Casual Users and Members Use CitiBike?
This dashboard examines some differences in how subscribed members and casual users use CitiBike. One trend I noticed is that member trips tend to peak around rush hour, while casual users tend to peak in the late afternoon and evening. I was surprised that casual user count didn't drop off more during the first wave of COVID-19 shutdowns in April and May of 2020.

#### Dashboard 2 - How Did COVID-19 Effect Ridership?
This dashboard looks at how the first waves of the COVID-19 pandemic impacted CitiBike ridership. Looking at the overall monthly trend of usage, it is expected that ridership drops off during the winter and early spring, as the weather is not as nice to bike in. However, by March and April, the ridership usually starts picking up again as the weather gets nicer. By comparing March through June of 2019 with March through June of 2020, we can see that ridership during the spring and early summer months of 2020 was lower than would be expected (exemplified by the 2019 data). The map breaks down the trip starts on a weekly increment between March 1st and May 31st of 2020. We can see the sharp drop-off that happened the week of March 15th, two days after the first round of shut-downs and lock-downs were announced.

#### Story
For the first slide, I looked at which stops were used during each year. By filtering by year, we can see how the range of the CitiBike program has grown between 2018 and 2022.

For the second slide, I looked at which stations were most popular to start from for each month during my selected timeframe. The stations in southern Manhattan seem to be more popular than the rest of the stops.

The third slide displays Dashboard #1, and the fourth slide displays Dashboard #2.
