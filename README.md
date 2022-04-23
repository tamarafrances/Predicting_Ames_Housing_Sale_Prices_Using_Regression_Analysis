# Helping First Time Homebuyers Predict Home Prices in Ames, IA

## Tamara Frances

----
<br> 

### Objective

Using the Ames Housing Dataset, my goal was to create a model that can accurately predict sale price based on a specific list of model features. Ideally, this model would:
* Work better than the null model
* Score well on both seen and unseen data
<br><br>
----
<br>

### Problem Statement

I am a real estate agent currently working with a growing family to help them get a sense of the funds they'll need to purchase a home in Ames, IA. They've outgrown the current apartment they're renting, and with plans to grow their family size, they are eager to move into a larger, functional home in a good neighborhood.

This project aims to predict sale prices of homes in the Ames area given requirements related to those mentioned above, including but not limited to:
* Overall condition
* Neighborhood
* Basement square footage
* Ground living area
* Garage area
<br><br>
----
<br>

### Description of the Data

#### Ames Housing Dataset

The Ames Housing Dataset contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010 ([source](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)).

There are over 80 variables in the dataset covering many aspects of homes in Ames, with 23 nominal, 23 ordinal, 14 discrete, 20 continuous variables, and 2 additional observation identifiers ([source](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt))
<br><br>
----
<br>

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**id**|*int64*|Ames Housing Dataset|Observation identifier|
|**pid**|*int64*|Ames Housing Dataset|Parcel identification number|
|**neighborhood**|*object*|Ames Housing Dataset|Lot size in square feet|
|**bldg_type**|*object*|Ames Housing Dataset|Lot size in square feet|
|**house_style**|*object*|Ames Housing Dataset|Lot size in square feet|
|**overall_cond**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**mo_sold**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**utilities**|*object*|Ames Housing Dataset|Lot size in square feet|
|**lot_area**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**totrms_abvgrd**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**bedroom_abvgr**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**bsmt_full_bath**|*float64*|Ames Housing Dataset|Lot size in square feet|
|**bsmt_half_bath**|*float64*|Ames Housing Dataset|Lot size in square feet|
|**full_bath**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**half_bath**|*int64*|Ames Housing Dataset|Lot size in square feet|
|**bsmtfin_sf_1**|*float64*|Ames Housing Dataset|Type 1 finished square feet|
|**bsmtfin_sf_2**|*float64*|Ames Housing Dataset|Type 2 finished square feet|
|**total_bsmt_sf**|*float64*|Ames Housing Dataset|Total square feet of basement area|
|**1st_flr_sf**|*int64*|Ames Housing Dataset|First floor square feet|
|**2nd_flr_sf**|*int64*|Ames Housing Dataset|Second floor square feet|
|**gr_liv_area**|*int64*|Ames Housing Dataset|Above grade (ground) living area square feet|
|**garage_area**|*float64*|Ames Housing Dataset|Size of garage in square feet|
|**garage_cars**|*float64*|Ames Housing Dataset|Size of garage in square feet|
|**indoor_sqft**|*float64*|Ames Housing Dataset|Total indoor square footage|
|**all_bath**|*float64*|Ames Housing Dataset|Total indoor square footage|
|**saleprice**|*int64*|Ames Housing Dataset|Sale price of home|
<br>

----
<br>

### Exploratory Data Analysis
<br>

**Finding 1: Median Ames housing prices are in the mid $160s**

* There are, however, a few higher priced outliers in the 500k and 600k range that make the data right skewed.

<br>

**Finding 2: Most variables related to home condition and living space have fairly strong positive linear relationships with sale price**

* Basement half baths and overall condition were the two features in the data dictionary that didn't reflect a positive linear relationship

<br>

**Finding 3: Constructed features exhibited some of the strongest positive linear relationships with sale price.**

* Indoor square feet: a combination of the above ground square footage and basement square footage, showed the strongest positive linear correlation to sale price among all features in the data dictionary
* All baths: a combination of half baths and full baths, also exhibited a strong positive linear relationship to sale price
<br><br>

----
<br>

### Preprocessing and Modeling
<br>

I utilized both StandardScaler and OneHotEncoder to to process my data. I isolated the numeric features in my dataset and applied StandardScaler to standardize the scales of the features being used in the upcoming models. I then isolated the categorical features and applied OneHotEncoder to make them numeric to use for modeling.
<br><br>

**I analyzed the performance of three models for this project:**
<br><br>

**Model 1: Linear Regression**
* R2 on test data: 0.877
* MAE on test data: $18,502
<br><br>

**Model 2: Lasso**
* R2 on test data: 0.877
* MAE on test data: $18,510
<br><br>

**Model 3: Ridge**

**Final Prediction Model Selected**
* R2 on test data: 0.876
* MAE on test data: $18,489


<br>

----
<br>

### Conclusion

The R2 score on the test set using the ridge model was 87.6%. Therefore, 87.6% of the variability in sale price is explained by the features in this model. It generalizes well to data that it hadn’t seen before.

The mean absolute error was 18,490 dollars. This model was off by an average of about 18.5k in its predictions. The ridge model is performing much better than the null model that had a mean absolute error of 58,380.

This model would provide added value to the family I'm working with by giving them a more accurate model for sale price predictions focused specifically on their must-haves in a new house.


<br>

----
<br>

### Next Steps

<br>
I chose the Ridge model as my final prediction model based on the mean absolute error and the goals of my problem statement. <br><br>
However, because the models are so close in performance, I would spend more time analyzing the standard deviations between the cross validation scores for each model to get a better sense of which model may be more consistent, and therefore the better model to use.

----
<br>

### Sources

* Benbennick, David. “English:  This Is a Locator Map Showing Story County in Iowa. For More Information, See Commons:United States County Locator Maps.” Wikimedia Commons, 12 Feb. 2006, commons.wikimedia.org/wiki/File:Map_of_Iowa_highlighting_Story_County.svg. Accessed 17 Apr. 2022.

* “House Clipart House 12 Clip Art at Clker Vector Clip - House Clip Art - Free Transparent PNG Clipart Images Download. ClipartMax.com.” ClipartMax.com, www.clipartmax.com/middle/m2i8K9b1G6A0K9H7_house-clipart-house-12-clip-art-at-clker-vector-clip-house-clip/. Accessed 16 Apr. 2022.
