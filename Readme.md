# Problem Statement

Given that we are real estate consultany firm whose clients are leading estate development company especially in Bangkok and metropolitan Area 
As real estate market is bouncing back from Covid financial crisis. Our clietns trying to explore possibility in launch projects in 2,500 prospective areas (Test Data) given from client as client marketing team wants to know proper pricing in whose areas that actually reflects from existing estate prices. (Train Data) 

So that, the marketing team could get glimpse of margin, worthiness of investment for each projects based on predicted data to ranking priority of prospective areas.

Prospect Audience: Client Marketing Team 


# Plan

we will use multiple linear regression breakdown into 4 structured model
As given data has 23 features in 14,271 rows in trainset
and 2,500 rows with 22 features (price excluded) in test set

Total Feature includes: ['id', 'province', 'district', 'subdistrict', 'address', 'property_type',
       'total_units', 'bedrooms', 'baths', 'floor_area', 'floor_level',
       'land_area', 'latitude', 'longitude', 'nearby_stations',
       'nearby_station_distance', 'nearby_bus_stops', 'nearby_supermarkets',
       'nearby_shops', 'year_built', 'month_built', 'facilities', 'price'],

Numberical Features that we will be using are
total_units, bedrooms, baths, floor_area, floor_level, nearby_stations, nearby_supermarkets, nearby_shops
**Criteria: correlation more than 0.2

with Regularization we will use L1 (Lasso) since it can mute some unneccsary beta if needed

# Model

Model1: Null Model : predicting with avg. value in train set

Model2: Only Latitude & Longitude represent location features + Selected Numeric features + Facility

Model3: Province and District represent location features + Selected Numeric features + Facility
(L1 Regularization Applied)

Model4: Model 2+3 improvement > adding more features, ignore unnecessary features
Added list: (floor_level, land_area, nearby_station_distance)
(L1 Regularization Applied)

# Result

Model1: 
R2 Train: 0
R2 Validation: 0
RMSE Train: 2,179,832 THB
RMSE Test: 2,154,512 THB

Model2:
R2 Train: 0.4806
R2 Validation: 0.5068
RMSE Train: 1,528,639 THB
RMSE Test: 1,609,135 THB

Model3:
R2 Train: 0.6351
R2 Validation: 0.6268
RMSE Train: 1,323,524 THB
RMSE Test: 1,375,577 THB

Model4:
R2 Train: 0.6373
R2 Validation: 0.6316
RMSE Train: 1,319,560 THB
RMSE Test: 1,277,074 THB

# Conclusion

After deploying 4 models, 

Model#4 is surely perform best but might be unrealistic in term of generalization trading off with preciseness improvement from Model#3 — (i.e. 19 features vs 14 features)

Whlist Model#3 has drastic different score from Model#2 given that they have equal no. of features which proof that Province and Subdistrict are better representative of location features than Latitude and Longitude or the latter 2 are needed engineering before fitting with the model.

For further studies, We could dive deep into Latitude & Longitude feature engineering for better prediction are could try fill missing values with other tactics rather than just Avg. value.


Real Estate Developers may focus on floor area (usable area) > land area and try not to squeeze in too much total units as it will be effect the price. In Addition, customer convenience for living (facility, transportation and shop nearby) also plays key roles in  marking up price for real estate project.


# Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**train_df**|dataframe|train.json|Existing estate data of Bangkok and Metropolitan Areas|
|**test_df**|dataframe|test.json|2,500 prospective projects areas|
|**model1**|dataframe|train_df| Null Model (mean of pricing from train_df) |
|**model2**|dataframe|train_df| Model from selective features in train_df believing that Latitude and Longtitude will be sufficient for location based features|
|**test_model2**|dataframe|test_df| Selective features dataframe that correspond with model2 features|
|**model3**|dataframe|train_df| Model from selective features in train_df believing that Province, District and Subdistrict plays major roles in location based features |
|**test_model3**|dataframe|test_df| Selective features dataframe that correspond with model2 features |