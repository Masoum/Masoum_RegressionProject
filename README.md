# Regression Project 

## Introduction:
For this project, I worked with a (canada_rent.csv) containing rental prices for units in across Canada in 2024.


**My goal is to explore multiple regression models, in order to find a model that predicts the rental price *most* accurately.**
In this project first I tried the Linear Regression Model, the second Model was LassoCV and the third model to try was the Polynomial Feature Model.

### What needs to be done:
1. My analysis needs to include an EDA section. 
2. Clean and prepare your data as necessary.
3. Use Feature-Engineering where necessary.
4. Comparison to at least 3 regression models.
5. Use validation scheme (simple or cross-validation).
6. Explain which features you have chosen for your final model and why.
7. Try the final model by using it to make new predictions on provided input.

#### This was the steps towards the list above:

The datase loaded and 

### Project Submission
- You will upload your completed project in a PUBLIC Github repository in your account.
- Your repository MUST include:
    - a README.md page that includes a description and summary of your analysis.
    - The completed .ipynb notebook with your analysis.
- Your notebook has to be organized and clean. Break down your steps, and follow coding best practices.


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
Dropped irrelevant columns such as 'latitude','longitude','availability_date_numeric','rentfaster_id'.

Converted categorical features using Target Encoding at first the One-Hot Encoding was applied to features
But by encoding we had more that 20K column features that was not been able to be processed. Then by Target Encoding
The encoding process was done.
Scaled numerical features was used by StandardScaler.

#### Feature Engineering

Created new meaningful features ( clean_sq_feet, clean_beds, clean_baths, pets,...).

Applied Polynomial Features for non-linear relationships.

Used SelectKBest (mutual_info_regression) to choose the most relevant features.

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

Selected the top 5 most important features using SelectKBest:
'city', 'type', 'clean_sq_feet', 'clean_beds', 'clean_baths'



All three models was trained on selected features 
Saved the trained model using joblib.dump().

This needs to be Done:

Tested new predictions on rental listings:

new_input = {
    "city": "Montreal",
    "province": "Quebec",
    "lease_term": "12 months",
    "type": "Apartment",
    "furnishing": "Unfurnished",
    "smoking": "No",
    "pets": "Yes",
    "sq_feet": 850,
    "num_beds": 2,
    "num_baths": 1
}

**Final Model Performance:**

Polynomial Regression----	376.72 O ----693710.42 X----832.89 X

LassoCV Regression----	398.46 X----458371.42 O----677.03 O

Linear Regression----	399.0505 X----458467.01 X----677.10 X

🏆 Best Model: LassoCV Regression (Best trade-off between MAE, MSE, and RMSE).

