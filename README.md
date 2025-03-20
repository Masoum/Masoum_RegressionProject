**Rental Price Prediction - Regression Analysis**
This project aims to predict rental prices using machine learning regression models. 
The dataset (canada_rent.csv) containing rental prices for units in across Canada in 2024, and the goal is to identify the best regression model for accurate price prediction.

**Project Steps:**

## Exploratory Data Analysis (EDA)

Performed EDA to understand dataset distribution, trends, and relationships.
Used visualizations heatmap to detect relationship.
Identified missing values, outliers, and categorical/numerical feature distributions.




### Data Cleaning & Preparation

Handled missing values using corrolations between target value 'price' and other features.
Dropped irrelevant columns such as 'Link','Address','availability_date_numeric','rentfaster_id'.

Converted categorical features using OneHotEncoding. Scaled numerical features was used by StandardScaler.

#### Feature Engineering

Created new meaningful features ( clean_sq_feet, clean_beds, clean_baths, pets,...).

Applied Polynomial Features for non-linear relationships.

Used SelectKBest (mutual_info_regression) to choose the most relevant features, just to know what features would be chosen.

##### Model Comparison: Evaluating 3 Regression Models

Implemented and compared at least three regression models:

Linear Regression
Polynomial Regression
LassoCV Regression

Used Mean Absolute Error (MAE), Mean Squared Error (MSE), and RMSE to compare model performance.

###### Validation Scheme

Used Train-Test Split (80/20) for quick evaluation.
Applied K-Fold Cross-Validation (5-fold) to ensure model generalization.


####### Feature Selection for the Final Model

Selected all features except 4 ('Link','Address','availability_date_numeric','rentfaster_id')



All three models was trained on selected features 
Saved the trained model using joblib.dump().

Tested new predictions on rental listings:

new_input = {
    "city": "Montreal",
    "province": "Quebec",
    "lease_term": "12 months",
    "type": "Apartment",
    "furnishing": "Unfurnished",
    "smoking": "No",
    "latitude": 51.305962,	
    "longitude": -114.012515,
    "clean_sq_feet": 800,
    "clean_beds": 2,
    "clean_baths": 1.5,
    "pets" : "yes"
}

**Final Model Performance:**

Comparing Models Based on Metrics MAE, MSE, RMSE

Polynomial Regression---- 434.95 ---- 652933.53 ---- 808.04

LassoCV Regression---- 441.48 ---- 523186.30 ---- 723.31

Linear Regression---- 440.94 ---- 522470.48 ---- 722.82

------------------------------------

Polynomial Regression has the lowest MAE, but the highest MSE and RMSE, indicating it occasionally makes very large pricing errors not ideal our target.
LassoCV and Linear Regression both have much lower MSE and RMSE, meaning they make fewer large mistakes.
Linear Regression is slightly better on MSE/RMSE than LassoCV, but they are very close.

-------------------------------------

🏆 Best Model: Linear Regression (Best trade-off between MAE, MSE, and RMSE).

