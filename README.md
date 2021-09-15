# EV Charging Infrastructure in Singapore


## Background

Electric vehicles or EVs have become one of the staples in green technology over the past few years, with countries like the US, China, and Norway already pivoting towards a higher rate of EV adoption. Even though slightly delayed, Singapore has also begun to gradually implement and establish a robust EV infrastructure. According to LTA, the target is to install 60,000 charging points by 2030, with 40,000 of them being the slow charging variant that will be used in HDB car parks and work offices, while fast chargers would be installed at specific locations where the length of stay will be considerably shorter. We can see this plan coming into fruition, with several, recent news articles that mentioned about pilot programmes being awarded for 620 chargers to be installed at around 200 participating public car parks. 


## Problem Statement

The main purpose of this project is to determine if the target set by the government is realistic and achievable, while predicting the number of EV charging stations the different HDB neighbourhoods should look to install, as well as the potential business of this emerging industry.


## Data Import, Cleaning, EDA



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
|**Zip**|*Ordinal*|alt_fuel_stations|Zip code of the EV Charging station & location|
|**EV Level1 EVSE Num**|*Numerical*|alt_fuel_stations|Original construction date|
|**EV Level2 EVSE Num**|*Numerical*|alt_fuel_stations|Remodel date (same as construction date if no remodeling or additions)|
|**EV DC Fast Count**|*Numerical*|alt_fuel_stations|Type of roof|
|**Latitude**|*Nominal*|Ames Housing|Roof material|
|**Longitude**|*Nominal*|Ames Housing|Exterior covering on house|
|**EV Connector Types**|*Nominal*|Ames Housing|Exterior covering on house (if more than one material)|
|**Facility Type**|*Nominal*|Ames Housing|Masonry veneer type|
|**EV Pricing**|*Nominal*|Ames Housing|Masonry veneer area in square feet|
|**Exter Qual**|*Ordinal*|Ames Housing|Evaluates the quality of the material on the exterior |
|**Exter Cond**|*Ordinal*|Ames Housing|Evaluates the present condition of the material on the exterior|
|**Foundation**|*Nominal*|Ames Housing|Type of foundation|
|**Bsmt Qual**|*Ordinal*|Ames Housing|Evaluates the height of the basement|
|**Bsmt Cond**|*Ordinal*|Ames Housing|Evaluates the general condition of the basement|
|**Bsmt Exposure**|*Ordinal*|Ames Housing|Refers to walkout or garden level walls|

## Modelling

## Analysis



## Conclusions & Recommendations

