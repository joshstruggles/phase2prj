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
