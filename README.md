# Credit Card Default Risk Segmentation
> This project aims to segment the risk probability of credit card default and classify features of those who are high risk of defaulting.

# Methodology
## Data Gathering and Preparation
The default of credit card clients data was collected from the UCI Machine Learning Repository (https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients). Containing 25 features including the monthly repayment status, the monthly bill amount statement, demographic information as well as the default paymemt status.
Encoded features were remapped to better interpreat the value during exploratory data analysis

## Exploratory Daa Analysis (EDA)
An EDA is first conducted to analyse the distribution of the dataset. Notably, the dataset has an imbalance distribution of default payments.
The dataset consists of predominantly females, individuals with at least a university level of education, and individuals who are single. In terms of age, the median found is at 34.

## Data Modelling
In preparing the dataset, null values were treated with iterative imputation.

For preprocessing, standard scaler was used for numerical values while one hot encoding was used for categorical

The method used for this project was an emsemble stack. The base models are:
- XGBoost: Gradient boosting mode
- Random Forest: Decision tree ensemble
Logistic regression was utilised as a meta learner for the final probability prediction

To efficiently find the best parameters for each model, Optuna was utilised

At a threshold of 0.5, the results showcased that while the model was efficient at finding non-defaulters, achieving an f1-score of 0.84, the model had trouble identifying defaulters, having an f1-score of 0.53. To mitigate this and properly catch the defaulters, the threshold was result here pls

# Findings