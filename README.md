# Credit Risk Analysis

This repository demonstrates the application of machine learning models for predicting borrower credit grades based on financial data. The dataset and methods are utilized to develop insights that enable smarter lending decisions.

---

## Overview

### Goals
- Predict borrower creditworthiness using AI models.
- Identify the most impactful features for assessing credit risk.
- Compare the performance of multiple models to find the most accurate and efficient.

### Dataset
- **Name**: Loan Data (88k samples)
- **Size**: 88,738 entries with 74 columns.
- **Key Features**:
  - Loan Amount (`loan_amnt`)
  - Interest Rate (`int_rate`)
  - Debt-to-Income Ratio (`dti`)
  - Employment Length (`emp_length`)
  - Loan Status (`loan_status`)
  - Annual Income (`annual_inc`)

---

## Methodology

1. **Data Cleaning**:
   - Removed irrelevant columns and handled missing values.
   - Created new features: `funded_amnt_to_annual_inc` and `revol_bal_to_annual_inc`.
   - Encoded categorical variables like `term`, `grade`, and `loan_status`.

2. **Exploratory Data Analysis**:
   - Visualized key feature distributions and their relationships to credit grades.
   - Examined correlations between variables.

3. **Model Training**:
   - Split data into training and testing sets.
   - Scaled features using `StandardScaler`.
   - Trained multiple models:
     - Linear Regression: R² score of 93.3%.
     - K-Nearest Neighbors (KNN): Best accuracy with k=9 (64.5%).
     - Random Forest: Testing accuracy of 96.2%.
     - XGBoost: Overall accuracy of 99%.

4. **Feature Importance**:
   - Identified top predictors such as `int_rate`, `installment`, and `loan_amnt`.
   - Visualized feature importance using horizontal bar plots.

---

## Results

### Model Performance
- **Random Forest**: Testing accuracy: 96.2%.
- **XGBoost**: Precision, Recall, and F1-scores close to 1.0 for all classes.
- **Key Feature Importance**:
  - `int_rate` (Interest Rate)
  - `installment`
  - `loan_amnt`

### Insights
- Interest rate (`int_rate`) is the most influential predictor of credit grade.
- Random Forest and XGBoost outperformed other models.
- Transformations like scaling and feature engineering improved model performance.

---

## How to Run
1. Clone this repository.
2. Install dependencies using:
   ```bash
   pip install -r requirements.txt
3. Run the Jupyter Notebook:
bash
jupyter notebook Credit_Risk_Analysis.ipynb
4. Inspect the visualizations and results.

### Future Enhancements
1. Incorporate hyperparameter tuning for Random Forest and XGBoost.
2. Validate with additional datasets.
3. Develop a live dashboard for real-time credit scoring.
