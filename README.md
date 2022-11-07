# King County Housing Data

<div>
    <img src="data/09112020_2018sea_124804.webp" width="750" align = "center"/>
</div>

## Project Overview

For this project, you will use multiple linear regression modeling to analyze house sales in King County. 

### Business Problem

King County is having a housing crisis!

Okay, well not really. We have been asked by a real estate agency in the area to build a predictive model for the King County housing market; the agency's directive is to establish locations in King County that will return the most investment and have the most profitable features.

### Raw data
We are basing our analysis on King County housing data.

### Multicollinearity
We created a heatmap in order to figure out what features are most correlated to price, we were also able to see if these features were correlated to any other features. Price had the highest correlation to sqft_living, however there were issues with multicollinearity that would further disqualify some of the more correlated features with pricing. 

<div>
    <img src="data/Screenshot 2022-10-31 134423.png" width="700" align = "center"/>
</div>

### Dealing with null data and non-numbers
A curosory look at the remaining features in our dataset show us that there are some objects. These categoricals can be flattened down into numbers using one hot encoder and one other tool. 

<div>
    <img src="data/Screenshot 2022-10-31 135051.png" width="300" align = "center"/>
</div>

### One Hot Encoder
This tool creates dummy categories as features and utilizes boolean values, "0" for False, "1" for True. We will do this for all categorical columns but 'waterfront'.
<div>
    <img src="data/Screenshot 2022-10-31 135431.png" width="700" align = "center"/>
</div>

### Ordinal Encoder
This tool creates boolean values for columns that have binary values (True/False, Yes/No) and creates boolean functions (1,0) thus assigning numerical value to affirmatives. 

### First Model 
Our first model ran with features: bedrooms, bathrooms, sqft_lot, floors, sqft_lot15, waterfront. View, grade, and condition were included as well but in their OHE(One Hot Encoder) formats. 
<div>
    <img src="data/Screenshot 2022-10-31 140951.png" width="700" align = "center"/>
</div>

### Testing Results
Four models were created, the first model had all numeric features: view, waterfront, grade, and condition were omitted in both the first and second models. The third model had all columns numerically represented and the final model utilized scaled results for sqft_lot (square footage of lot) and sqft_lot15 (average square footage of lots of 15 closest neighbors). Our final model addressed ~55% of the variance in the data and gave us an intercept of ~$104,608.41, with a standard deviation of ~$246,892.28

### Feature Testing Results
Based on the final model we were able to predict the pricing of a home that has the following features: 
<div>
    <img src="data/Screenshot 2022-10-31 141951.png" width="700" align = "center"/>
</div>

This combination of features gave us a home price of ~$1,439,837

### First Model
As stated, our first model had all numeric features but did not have any of the categorical features due to categorical features being non-numeric. We chose these features solely based on the fact that they were numeric columns; our first model ran with a .526 R-squared score, suffered from multicollinearity, and still held some features that we would deem unnecessary for our analysis (zipcode, floors, sqft_living, sqft_living15). 
<br><br>


### First Model vs. Final Model
This model performed "better" than our first model, contained more useful information, and did not suffer from the same issues with multicollinearity that our first model did. We log transformed all remaining continuous variables in our final model prior to making any predictions. The final model is the sole model that is capable of making predictions on our dataset. 
<br><br>

## Business Suggestions
Taking a look at the graphs below, we can make some business suggestions to our client as well: there appears to be little return on investment for more than 5 bedrooms, and very little apparent return on investment for properties that have more than 3.5 bathrooms. Taking into account how much a waterfront property goes for, consider building on some kind of waterfront as well for an additional ~$540,106 in price.   

![Screenshot 2022-11-03 172004](https://user-images.githubusercontent.com/108380875/200337247-adda62a1-2587-4551-8a93-e0631a821a43.png)
![Screenshot 2022-11-03 172133](https://user-images.githubusercontent.com/108380875/200337261-c3d895b7-0aaa-46b5-9233-8902762e1dbd.png)

<br><br>
### Conclusion
Our final model took on a significantly different form. The categories chosen were: sqft_lot_log, sqft_lot15_log, bedrooms, bathrooms, waterfront_NO, waterfront_YES, view_AVERAGE, view_EXCELLENT, view_FAIR, view_GOOD, grade_10 Very Good, grade_11 Excellent, grade_12 Luxury, grade_13 Mansion. Our predictive model was built on the back of our final set of data giving us an R-squared score of 0.548. A house, regardless of features was worth $104,608. Per bedroom an additional: ~$30,487, bathroom: ~$124,595, and waterfront property averaging an additional ~$540,106. For grade of house the only columns we could use were: 10 Very Good: ~$399,961, 11 Excellent: ~$708,925, 12 Luxury: ~$1,253,902, 13 Mansion: ~$2,652,976. For homes with a view, graded Fair: ~$28,120, Good: ~$37,460, Average ~$33,250, and Excellent: ~$50,340. Per square foot of lot an additional ~$13,310. For each square foot on average of your 15 closest neighbors there was a negative,- ~$17,688.

