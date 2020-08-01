Uber Movement Data

**Problem Statement:**

Uber travel time data has been used for the below analysis. Objective of the analysis is to Predict approximate time to travel between point A to point B at given interval of the day. We have considered 2019 Quarter4 data for the analysis. Data provided by Uber is aggregated at different levels i.e. monthly, weekly, daily and hourly.

**Data Sources and descriptions**
* Uber Movement Data:
  * https://movement.uber.com/explore/bangalore/travel-times/query?si=573&ti=&ag=wards&dt[tpb]=ALL_DAY&dt[wd;]=1,2,3,4,5,6,7&dt[dr][sd]=2020-03-01&dt[dr][ed]=2020-03-31&cd=&sa;=&sdn=&lat.=51.51262&lng.=-0.1658002&z.=12&lang=en-US 
* Time Frame:
  * 2019 – Quarter 4
* Wards data - Bangalore:
  * Bangalore wards file contains the list of wards with their spatial co-ordinates
  * This is in json format
* Aggregated data:
  * Uber provides the data of average time taken to travel between from point A to point B
  * This data has been aggregated at weekly, daily and hourly data
  * This file is in the excel format

**Data Dictionary:**
* Bangalore Wards data
  ![Blr_wards_data](https://user-images.githubusercontent.com/66996144/89106683-675bec00-d449-11ea-9fab-6b2183197970.png)
* Aggregated data
  * Hourly Data:
    ![Hourly_Data](https://user-images.githubusercontent.com/66996144/89106705-bc97fd80-d449-11ea-813f-b0388c4325bf.png)
  * Weekly Data:
    ![Weekly_Data](https://user-images.githubusercontent.com/66996144/89106728-fb2db800-d449-11ea-9c1f-2bd72a9338af.png)
  * Monthly Data:
    ![Monthly_Data](https://user-images.githubusercontent.com/66996144/89106742-0da7f180-d44a-11ea-9e7f-ad56a3b5b6cf.png)
 
Note: All time related fields are in seconds
 
 
**Data Preparation steps for wards data:**
Step 1: Converted json file to csv
Step 2: Prepared data such there are no blank cells in between the range of co-ordinates (refer below image)
Step 3: Final output file is validated against the original input file

_Before cleansing:_
  ![Bfr_Cleaning](https://user-images.githubusercontent.com/66996144/89106762-2f08dd80-d44a-11ea-9d1f-47f372291a30.png)
_After cleansing:_
![After_Cleaning](https://user-images.githubusercontent.com/66996144/89106781-4a73e880-d44a-11ea-8e63-5ae53ccb238e.png)

**Exploratory Data Analysis**
* Wards data:
  ![ED_Wards_Data](https://user-images.githubusercontent.com/66996144/89106852-9de63680-d44a-11ea-920d-dadc7e1f474d.png)
* Sample Data:
  ![Wards_map](https://user-images.githubusercontent.com/66996144/89106903-c110e600-d44a-11ea-9038-1e0356addbe0.png)

Hourly Data:
  ![Hourly_Data_Describe](https://user-images.githubusercontent.com/66996144/89107059-f10cb900-d44b-11ea-9678-2fee2bf61efe.png)
  ![Hourly_Data_Describe1](https://user-images.githubusercontent.com/66996144/89107063-f5d16d00-d44b-11ea-9650-4f78dcb56a39.png)
  
* Derived fields:
  * mean_travel_time_mins from mean_travel_time
  * Standard_deviation_travel_time_mins from Standard_deviation_travel_time
  * Geometric_mean_travel_time_mins from Geometric_mean_travel_time
* Hourly data gives us time taken to travel between 2 points for every hour of the day
* Mean travel time can be 0.5 mins when distance between 2 points are minimum 
* Mean travel time can be 181.2 mins (3 hrs) when distance between 2 points are maximum 

Weekly Data:
  ![Weekly_Data_Describe](https://user-images.githubusercontent.com/66996144/89107191-d25af200-d44c-11ea-94f8-fa9c87122f80.png)
  ![Weekly_Data_Describe1](https://user-images.githubusercontent.com/66996144/89107194-d555e280-d44c-11ea-87d7-63aaf25f3e46.png)

* Derived fields: 
   *  mean_travel_time_mins from mean_travel_time
   *  Standard_deviation_travel_time_mins from Standard_deviation_travel_time
   * Geometric_mean_travel_time_mins from Geometric_mean_travel_time
* Weekly data gives us time taken to travel between 2 points on every day of the week
* Mean travel time can be minimum 1.1 mins when distance between 2 points are minimum 
* Mean travel time can be maximum 117.5 mins when distance between 2 points are maximum 


Let’s dive into actual data with an example:
Choose your travel points:
* Enter the source id: 114
* Enter the destination id: 47

**Correlation:**
 ![Corelation](https://user-images.githubusercontent.com/66996144/89107243-3d0c2d80-d44d-11ea-9f3d-654ab02f2037.png)

**Pair plot:**
 ![Pair_Plot](https://user-images.githubusercontent.com/66996144/89107256-57460b80-d44d-11ea-9cc4-e1c05346f606.png)
 

**Weekly data**
_Basic stats:_
    ![BS_Weekly_desc](https://user-images.githubusercontent.com/66996144/89107337-f79c3000-d44d-11ea-9b81-d9359c5e63d0.png)
    ![BS_Weekly_desc1](https://user-images.githubusercontent.com/66996144/89107340-fff46b00-d44d-11ea-87b2-4e0d13942ae1.png)

Average time to travel across days:
  ![Avg_time_to_travel_week](https://user-images.githubusercontent.com/66996144/89107356-27e3ce80-d44e-11ea-815f-94b82e71aabc.png)
* If we choose to travel from Vijayanagar to Malleshwaram, we require 24 to 27 minutes on average
* There is not much difference in the travel time when compared across days because of the population and attractive shopping places
* Let’s see how does the time vary hours of the day
 
**Hourly data - describe()**
_Basic stats:_
    ![BS_Hourly_desc](https://user-images.githubusercontent.com/66996144/89107387-6f6a5a80-d44e-11ea-8678-feda93372704.png)
    ![BS_Hourly_desc1](https://user-images.githubusercontent.com/66996144/89107390-72fde180-d44e-11ea-8264-aedd48c65076.png)

Average time to travel during hours days:
![Avg_time_to_travel_hourly](https://user-images.githubusercontent.com/66996144/89107405-8c069280-d44e-11ea-9ba5-953435cfd709.png)

* For the same location we choose previously i.e. Vijayanagar to Malleshwaram, we require 15 to 32 minutes on average during different time interval
* Variation in average time is slightly more, this is because of less traffic during early morning and late night which gets densed during office hours
* As expected during late night and early morning we need minimal time whereas peak office hours i.e. 5-7 consume double the time

