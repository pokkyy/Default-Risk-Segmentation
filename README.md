# Credit Card Default Risk Segmentation
> Predict and segment credit card clients by default risk to enable proactive management.

This project predicts credit card default probabilities and segments clients by risk level. Beyond a simple yes/no prediction, it highlights which features make someone high-risk, helping decision-makers act before a payment problem occurs.

# 📚 Data Gathering and Preparation
- The default of credit card clients data was collected from the UCI Machine Learning Repository (https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients)
- Contains 25 features including the monthly repayment status, the monthly bill amount statement, demographic information as well as the default payment status.
- Encoded features were remapped for easier interpretation during exploratory analysis.

# 🔍 Exploratory Data Analysis (EDA)
The dataset was first explored in a high-level fashion in order to gain a base understanding of the distribution in the dataset. Notably, the dataset has an imbalance distribution of default payments.
The dataset consists of predominantly females, individuals with at least a university level of education, and individuals who are single. In terms of age, the median found is at 34.

# 🔬 Data Modelling
In preparing the dataset, null values were treated with iterative imputation.

Preprocessing:
- Numerical features → StandardScaler
- Categorical features → One-hot encoding

Stacking Ensemble Model:
- Base learners: XGBoost (gradient boosting), Random Forest (tree ensemble)
- Meta-learner: Logistic Regression for final probability prediction

To efficiently find the best parameters for each model, Optuna was utilised

Performance at optimal threshold (0.60):
| Default Status | F1-Score |
| --- | --- |
| Non-default | 0.80 |
| Default | 0.54 |
Overall accuracy: 0.81

Note: Thresholds were tuned to prioritize correctly identifying defaulters, which is critical in credit risk management.

## ⭐ Feature Importance
Top 10 Features:

| Feature | Importance |
| --- | --- |
| PAY_0 | 0.083389 |
| PAY_2 | 0.012115 |
| PAY_AMT3_log | 0.006542 |
| PAY_3 | 0.005593 |
| MARRIAGE | 0.005315 |
| PAY_AMT1_log | 0.004607 |
| BILL_AMT5 | 0.004044 |
| PAY_AMT4_log | 0.003291 |
| PAY_5 | 0.003049 |
| LIMIT_BAL_log | 0.002849 |

- Feature importance showcases that the very first repayment status highly dictates whether a person would default.
- Subsequent month's repayment status has a similar effect, albeit on a lower scale.
- The highest relevant demographic feature dictates that a person's maritial status plays a key role in their default status.

# 🧩 Segmentation
Using the predicted default probabilities, clients are segmented based on the threshold 0.60:
- Low risk: probability < 0.60
- High risk: probability ≥ 0.60

The findings showcase that a majority of those at a higher risk of default are women, those with a university education, and married individuals.

# 🔑 Key Takeaways
- Repayment behavior is the most important driver of default risk.
- Demographics like marital status provide additional predictive power.
- Threshold tuning allows us to segment clients smartly – it’s not perfect, but it’s actionable and allows for a more targeted approach
- Predicted probabilities enable prioritization within risk groups, which is more actionable than binary predictions alone.