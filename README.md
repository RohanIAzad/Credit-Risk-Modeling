# Project Overview
This project focuses on developing a Probability of Default (PD) model using the Lending Club dataset (2007-2015). The dataset contains detailed loan information, including borrower characteristics and loan performance. The goal is to predict loan default risk and build a credit scorecard for risk assessment. Lending club is a peer-to-peer lending company. Each row is for one member, their features and whether they paid off, current or defaulting on their loan

# Steps Followed
## 1. Data Preprocessing and Feature Engineering
- Handled missing values and created dummy variables for categorical features.
- Applied Weight of Evidence (WoE) transformation and calculated Information Value (IV) to assess variable significance.
- Selected reference categories based on the lowest WoE values.

## 2. Building the Probability of Default (PD) Model

- Defined the target variable:
  - Good (1): Loan is not in default.
  - Bad (0): Loan is in default.
- Grouped numerical and categorical variables based on WoE distribution.
- Split the dataset into 75% training and 25% test sets.
- Built a Logistic Regression model and selected statistically significant variables.
- Evaluated the model using ROC AUC = 0.6953 (at 0.9 threshold).

## 3. Scorecard Development
- Converted model predictions into a credit score ranging from 300 to 850.
- Transformed logistic regression coefficients into scorecard points using:
   - Variable Score = Variable Coefficient x ((max score - min score) / (max sum coefficients - min sum coefficients))
- Applied matrix multiplication to calculate individual scores.

## 4. Approval & Rejection Analysis
- Derived approval and rejection rates based on PD thresholds.
- At a 10% PD cutoff (90% probability of being good):
- Approval rate: 53.94%
- Rejection rate: 46%

## 5. Model Validation
- Calculated Population Stability Index (PSI) to monitor model drift and assess the need for retraining with new data.

## Key Takeaways
- WoE and IV helped in variable selection and transformation for better predictive power.
- Logistic Regression effectively modeled PD and facilitated scorecard development.
- The scorecard provides a transparent risk assessment framework for loan approvals.
- PSI validation ensures long-term model reliability.
