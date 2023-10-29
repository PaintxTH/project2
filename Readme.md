# Problem Statement

Given that we are real estate consultany firm whose clients are leading estate development company especially in Bangkok and metropolitan Area 
As real estate market is bouncing back from Covid financial crisis. Our clietns trying to explore possibility in launch projects in 2,500 prospective areas (Test Data) given from client as client marketing team wants to know proper pricing in whose areas that actually reflects from existing estate prices. (Train Data) 

So that, the marketing team could get glimpse of margin, worthiness of investment for each projects based on predicted data to ranking priority of prospective areas.

Prospect Audience: Client Marketing Team 


# Conclusion

After deploying 4 models, 

Model#4 is surely perform best but might be unrealistic in term of generalization trading off with preciseness improvement from Model#3 — (i.e. 19 features vs 14 features)

Whlist Model#3 has drastically different score from Model#2 given that they have equal no. of features which proof that Province and Subdistrict are better representative of location features than Latitude and Longitude or the latter 2 are needed engineering before fitting with the model.

For further studies, We could dive deep onto Latitude & Longitude feature engineering for better prediction

Real Estate Developers may focus on floor area (usable area) > land area and try not to squeeze in too much total units as it will be effect the price. In Addition, customer convenience for living (facility, transportation and shop nearby) also plays key roles in  marking up price for real estate project.


# Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**train_df**|dataframe|train.json|Existing estate data of Bangkok and Metropolitan Areas|
|**test_df**|dataframe|test.json|2,500 prospective projects areas|
|**model1**|dataframe|train_df| Null Model (mean of pricing from train_df |
|**model2**|dataframe|train_df| Model from selective features in train_df believing that Latitude and Longtitude will be sufficient for location based features|
|**test_model2**|dataframe|test_df| Selective features dataframe that correspond with model2 features|
|**model3**|dataframe|train_df| Model from selective features in train_df believing that Province, District and Subdistrict plays major roles in location based features |
|**test_model3**|dataframe|test_df| Selective features dataframe that correspond with model2 features |