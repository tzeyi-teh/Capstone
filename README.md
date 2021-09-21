# EV Charging Infrastructure in Singapore


## Background

Electric vehicles or EVs have become one of the staples in green technology over the past few years, with countries like the US, China, and Norway already pivoting towards a higher rate of EV adoption. Even though slightly delayed, Singapore has also begun to gradually implement and establish a robust EV infrastructure. According to LTA, the target is to install 60,000 charging points by 2030, with 40,000 of them being the slow charging variant that will be used in HDB car parks and work offices, while fast chargers would be installed at specific locations where the length of stay will be considerably shorter. We can see this plan coming into fruition, with several, recent news articles that mentioned about pilot programmes being awarded for 620 chargers to be installed at around 200 participating public car parks. 


## Problem Statement

The main purpose of this project is to determine if the target set by the government is realistic and achievable, while predicting the number of EV charging stations the different HDB neighbourhoods should look to install, as well as the potential business of this emerging industry.


## Data Import, Cleaning, EDA

Several datasets were obtained through various government sources. For the HDB testing dataset, the HDB car park data from data.gov, and it includes information like address, coordinates, car park type, number of decks/floors, etc. However, a problem with this dataset is that it does not provide any data about the total spaces that each car park has. To help fill out that the missing data, I extracted some data from Parkopedia, which had the total spaces data of around 800 car parks. For the model training datasets, I extracted EV charging station data for the States of California and Washington, and city-owned car park data for the major cities within those states, mainly SF, LA, and Seattle. I chose to obtain data from these 2 states because they have the highest numbers of EV chargers across the country, and the cities are also similar to Singapore.


### Data Dictionary
|Attribute|Variable Type |Dataset|Description|
|---|---|---|---|
|**address**|*Discrete*|HDB_parking_cleaned_planningarea|Address for each HDB car park|
|**x_coord**|*Continuous*|HDB_parking_cleaned_planningarea|X coordinate of car park|
|**y_coord**|*Continuous*|HDB_parking_cleaned_planningarea|Y coordinate of car park|
|**car_park_type**|*Nominal*|HDB_parking_cleaned_planningarea|Type of car park|
|**type_of_parking_system**|*Nominal*|HDB_parking_cleaned_planningarea|Parking system used by car park|
|**short_term_parking**|*Nominal*|HDB_parking_cleaned_planningarea|Availability for short-term parking|
|**free_parking**|*Nominal*|HDB_parking_cleaned_planningarea|Availability of free parking|
|**night_parking**|*Nominal*|HDB_parking_cleaned_planningarea|Availability of night parking|
|**car_park_decks**|*Numerical*|HDB_parking_cleaned_planningarea|Number of decks/storeys within the car park|
|**gantry_height**|*Numerical*|HDB_parking_cleaned_planningarea|Height of gantry entrance|
|**car_park_basement**|*Nominal*|HDB_parking_cleaned_planningarea|Presence of basement car park|
|**car_park_lots**|*Numerical*|HDB_parking_cleaned_planningarea|Total number of car park spaces for the car park|
|**latitude**|*Continuous*|HDB_parking_cleaned_planningarea|Latitude of car park|
|**longitude**|*Continuous*|HDB_parking_cleaned_planningarea|Longitude of car park|
|**planning_area**|*Nominal*|HDB_parking_cleaned_planningarea|Planning area that car park is situated in|
|**Station Name**|*Discrete*|alt_fuel_stations|Name of EV Charging location|
|**Street Address**|*Discrete*|alt_fuel_stations|Address of EV Charging station|
|**City**|*Nominal*|alt_fuel_stations|City of EV Charging location|
|**State**|*Nominal*|alt_fuel_stations|Rates the overall material and finish of the house|
|**Zip**|*Nominal*|alt_fuel_stations|Zip code of the EV Charging station & location|
|**EV Level1 EVSE Num**|*Numerical*|alt_fuel_stations|Number of Level 1 EV chargers|
|**EV Level2 EVSE Num**|*Numerical*|alt_fuel_stations|Number of Level 2 EV chargers|
|**EV DC Fast Count**|*Numerical*|alt_fuel_stations|Number of fast-charging EV stations|
|**Latitude**|*Nominal*|alt_fuel_stations|Latitude of EV charging station|
|**Longitude**|*Nominal*|alt_fuel_stations|Longitude of EV charging station|
|**EV Connector Types**|*Nominal*|alt_fuel_stations|Types of EV connectors available for charging|
|**Facility Type**|*Nominal*|alt_fuel_stations|Type of facility containing EV chargers|
|**EV Pricing**|*Nominal*|alt_fuel_stations|Pricing of EV charging at different locations|
|**Zip**|*Nominal*|City_Owned_Parking_Lots_LA|Zipcodes of car parks in LA|
|**ConvenientTo**|*Nominal*|City_Owned_Parking_Lots_LA|Convenience to facilities nearby|
|**Spaces**|*Numerical*|City_Owned_Parking_Lots_LA|Total parking spaces at each car park in LA|
|**Zip**|*Nominal*|Public_Garages_or_Parking_Lots_Seattle|Zipcodes of car parks in Seattle|
|**DEA_Stalls**|*Numerical*|Public_Garages_or_Parking_Lots_Seattle|Total parking spaces of car parks in Seattle|


### Data Cleaning

During the data cleaning stage, I dealt with the missing data within the HDB car park dataset by using KNN imputation to fill up the missing information accordingly. I also made use of an API to convert the coordinates into latitude and longitude before I extracted the planning area of each car park. I also dropped all the surface car park rows as the imputation done for them were not as consistent, and the total spaces of these type of car parks can vary based on land area. As for the training dataset, it was mainly a merge between the EV charging and city-owned car parks datasets. Before joining, I first grouped the EV chargers by zip code, and then used the same KNN imputation method to determine the missing spaces. I also used one-hot encoding on the parking types, given it is a categorical feature. The model will also be run based on the slow chargers as fast chargers are generally not recommended for mass installation due to its higher costs.


## Modelling

Once all the pre-processing was done, I went ahead with the train-test split and ran the data through several machine learning algorithms. For this part, I utilised the Pipeline to include the StandardScaler to standardise the features and passed them through the following classification models:

- K-Nearest Neighbours (KNN)
- Random Forest
- Decision Tree
- Support Vector Machines (SVM)

Through some hyperparameter tuning of the various models, the KNN model performed the best, with an accuracy score of 81.5%. This was obtained under the conditions of 13 neighbors, using the ‘distance’ weight method, and also the Manhattan distance. I chose to make use of this model to go ahead with the predictions for the EV charging stations. 


## Analysis

After fitting the model with the HDB dataset, I exported the dataframe and used Tableau to visualise some of the findings. I grouped the predicted data by neighbourhood, to see the total car park spaces and predicted number of EV charging stations within each neighbourhood. The top 8 neighbourhoods which have the highest predicted number of charging stations are:

1. Woodlands
2. Sengkang
3. Jurong West
4. Punggol
5. Tampines
6. Choa Chu Kang
7. Sembawang
8. Bukit Panjang

However, there were some discrepancies in the corresponding number of EV charging stations, with Sengkang having more EV chargers than Woodlands, Punggol having more chargers than Jurong West, and Choa Chu Kang having more than Tampines. From a separate bar chart, I grouped the types of multi-storey car parks by neighbourhood and observed that newer neighbourhoods like Punggol, Sengkang and Choa Chu Kang have more car parks categorised as "Others" as compared to the other areas. Based on the model predictions, the other types of car parks will contain a higher number of EV chargers compared to the MSCPs, and that’s why we can see that these neighbourhoods would have more charging stations when compared to the neighbourhoods that have slightly more parking spaces. It was also observed that half of the EV-ready towns chosen by the government are also consistent with the predictions, with them being Punggol, Jurong West, Choa Chu Kang, and Sembawang. Tengah, which is still under development, will also be a part of the EV-ready towns with its moniker of the first smart and sustainable town in Singapore. An interactive map of each individual MSCP in Singapore can be found in the link below:

https://public.tableau.com/app/profile/tze.yi.teh/viz/MSCPsinSingaporewithpredictedEVchargingpoints/Sheet1?publish=yes

The predictions actually only make up to about 9% of the national target but it can definitely be used as a baseline to be followed moving forward, as the predictions are surprisingly consistent with the pilot programme that the government has set up, with 3 charging stations per car park. I also made some cost analysis based on the model predictions and found out that for slow chargers, a Level 2 charging point costs around $2000 to install, preliminary installations would cost around 6 million dollars, excluding those that have already been awarded. Just to give everyone some context, this would mean that 80 million dollars will need to be invested into reaching the target, meaning there is clearly still a lot of business that is surrounding this. 


## Limitations & Further Improvements

The project also didn’t come without its limitations. The training dataset was limited to data from city-owned car parks, and it would be helpful to include more data from various types of car parks in Singapore and obtaining more accurate representation of spaces for the surface car parks, as they make up half of the total car parks in Singapore. These points will be considered to help improve the accuracy of the model moving forward. 


## Conclusions & Recommendations

In conclusion, the model helped justify the country's strategy and efforts at EV charging deployment, to a certain extent, given the similarities in targetted neighbourhoods that are to be transformed into EV-ready towns, and consistency in the ratio of EV charger installation compared to the pilot programme. With the inclusion of more data to train the model based on the successful infrastructure in EV-ready cities within the US, and more car park information in Singapore outside of the HDB car parks, the model predictions will certainly improve and help in enhancing the rollout strategy of the EV charging infrastructure in Singapore.
