# Tableau - CitiBike July 2023 Analysis
## Project Description  & Background- [![Tableau-Dashboard](https://img.shields.io/badge/Dashboard-Presentation-black?style=flat&logo=atandt)](https://public.tableau.com/views/CitiBike_GalBeeri/CasualRidersDashboard?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link) 

##### Background:
Since 2013, the Citi Bike program has implemented a robust infrastructure for collecting data on the program's utilisation. Each month, bike data is collected, organised, and made public on the [`Citi Bike Data`](https://citibikenyc.com/system-data).

However, while the data has been regularly updated, the team has yet to implement a dashboard or sophisticated reporting process. City officials have questions about the program, so your first task on the job is to build a set of data reports to provide the answers.

##### Project Description:
Analysing CitiBike's wormest month (July) from 2023 to provide insights and explore the following questions:
1. Do members or casuals have higher usage? 
2. Which stations are most popular? What is the average distance travelled overall? 
3. What days of the week are most riders taken on? 
4. What type of bicycle used most? 
5. On average, for how long do users rant a bicycle? 
6. Which zip codes approximately concentrate the largest amount of usage? 

To answer these questions, two dashboards were created for each segment the company posses, members and casual users. Members are users that subscribed for an annual membership (Citi Bike plan  / Lyft Pink plan [pricing](https://citibikenyc.com/pricing)); Casual members = users who purchased 24-hour pass OR 3-day pass. 
### Description of the data: 
There are 13 columns and 3,767,347 records of data from [`CitiBike`](https://s3.amazonaws.com/tripdata/index.html).
##### Columns: 
``` python
# 1. ride_id               
# 2. rideable_type         
# 3. started_at            
# 4. ended_at              
# 5. start_station_name    
# 6. start_station_id      
# 7. end_station_name      
# 8. end_station_id        
# 9. start_lat             
# 10. start_lng             
# 11. end_lat   ---> The lat and lng of the end point for a given ride.            
# 12. end_lng               
# 13. member_casual  --> Segmentation column - identifying members and casual users         
# 14. distance   ---> Defining a function to return the distance betwee two geolocation points given a sphere - Haversine formula
```
        
### Assumption & Note:
**Assumption:**
* **Citibike's July data include multiple geo location per station.** The assumption here is that each station has a "static" geo location as well as "dynamic" geolocations for each bicycle docked in the station (each bicycle has a "tablet" that is docked to the stering wheel). 
**Note:**
* What is the distance metric? The dataset does not include mutiple geolocations to indicate the root of a given ride. Haversine's formula allow us to calculate the distance between two stations, this data is being presented in the dashboard to calculate the average distance for members and casual users. 

##### Members Dashboard 
![members_dashboard](https://github.com/Kokolipa/Tableau_CitiBIke/blob/city_main/Dashboard_Images/Members_Dashboard.png)
----------------------------------------------------------------
##### Casual Members Dashboard 
![casual_members_dashboard](https://github.com/Kokolipa/Tableau_CitiBIke/blob/city_main/Dashboard_Images/Casual_Dashboard.png)
#### Tableau Story
![Main](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExdmJ6eGt3dW5wdzVrY3lmYXhweXFia2V3cDlncTg0NXZnZ3RmY3lzeSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1iqC3KRYMkwlA0kfkX/giphy.gif)




#### Extract: 
* **Data Extraction:** Downloading the zip file from the CitiBike's data source (202307-citibike-tripdata.csv.zip)
* Rendering the data extracted from the zip file to jupyter notebook using Pandas
* Extracting the cleaned data using the zipfile python library using compresssion level 9. 
#### Transform: 
* Removing null values
* Memory optimisation -> Transforming the data types and reducing the bite size for each dtype.
* Manipulation -> Leveraging Harvesine's function to calculate the distance between two geolocations (adding the distance column to the dataset). 
#### Load: 
* Loading the data (CSV) into Tableau, analysing the data, and uploading the visuals to the dashboards.


#### Python Libraries Used:
1. Pandas.
2. os. 
3. math --> radians, sin, cos, sqrt, atan2
4. zipfile 


#### Folder structure
``` yml
.
│   ├── Images 
│   |   ├── CitiBike Logo.png      
│   |   ├── CitiBike_Bike.png          
│   |   ├── customers.png         
│   |   ├── Distance.png        
│   |   ├── docked_bike.png
│   |   ├── Ranting.png       
│   ├── DataTransformation.ipynb     
│   ├── Dashboard_Images
│   |   ├── Casual_Dashboard.png      
│   |   ├── Members_Dashboard.png     
|___README.md
|___.gitignore                
``` 