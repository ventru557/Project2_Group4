
# Credit Risk Analysis

Learn how to analyze credit risk using real-world financial data and apply machine learning models to predict borrower creditworthiness. This project showcases how to build, clean, and process datasets, implement models, and derive insights for smarter lending decisions.

---

## Index
1. [Introduction](#introduction)
2. [How We Picked the Dataset](#how-we-picked-the-dataset)
3. [Difficulties and Concerns](#difficulties-and-concerns)
4. [Adjustments Based on Feedback](#adjustments-based-on-feedback)
5. [How and Why We Removed Data](#how-and-why-we-removed-data)
6. [Methodology](#methodology)
7. [Models Used](#models-used)
8. [Results](#results)
9. [Future Enhancements](#future-enhancements)
10. [How to Run](#how-to-run)
11. [Contributing](#contributing)
12. [Acknowledgments](#acknowledgments)

---

## Introduction

This project demonstrates the application of data analysis and machine learning techniques for credit risk assessment. We explore a rich dataset of borrower financial attributes to predict credit grades and identify factors influencing creditworthiness. The ultimate goal is to compare models and optimize performance for real-world applications.

---

## How We Picked the Dataset

The dataset was chosen from a credit risk analysis repository due to its detailed representation of real-world financial attributes. It includes data on borrowers, loan statuses, and credit grades, making it ideal for predictive modeling of financial risk.

---

## Difficulties and Concerns

- **High Dimensionality**: The dataset initially had 74 columns, many of which were irrelevant or redundant.
- **Class Imbalance**: Most entries were categorized as "Fully Paid," which could bias the model.
- **Data Quality**: Some columns had over 50% missing values, complicating the cleaning process.

---

## Adjustments Based on Feedback

Feedback from the instructor highlighted the importance of focusing on:
- Key financial attributes directly affecting credit risk.
- Simplifying the dataset by removing unnecessary features.
- Using additional feature engineering to derive meaningful insights.

---

## How and Why We Removed Data

- **Dropped Columns**: Removed columns like `id`, `member_id`, and `url` as they were irrelevant.
- **Dropped Rows**: Eliminated rows with excessive missing values to ensure data quality.
- **Sampling**: Used 15% of the data for quicker computation while maintaining sufficient diversity.

---

## Methodology

1. **Feature Engineering**:
   - Created new features: `funded_amnt_to_annual_inc` and `revol_bal_to_annual_inc`.
   - Encoded categorical features like `term`, `grade`, and `loan_status`.
2. **Exploratory Data Analysis**:
   - Visualized key feature distributions and relationships.
   - Correlation analysis to identify impactful features.
3. **Model Training**:
   - Split data into training and testing sets.
   - Scaled features using `StandardScaler`.
   - Trained multiple models: XGBoost and Random Forest.

---

## Models Used

### Why XGBoost and Random Forest?
- **XGBoost**:
  - High performance with gradient boosting.
  - Handles missing values and is robust to overfitting.
- **Random Forest**:
  - Ensemble method that performs well on imbalanced datasets.
  - Provides feature importance metrics for interpretability.

---

## Results

### Model Performance
- **Random Forest**: Achieved a testing accuracy of 96.2%.
- **XGBoost**: Delivered near-perfect precision, recall, and F1-scores.

### Key Insights
- `int_rate` (interest rate) is the most influential predictor of credit grade.
- Feature engineering and scaling significantly improved model performance.

---

## Future Enhancements

- Incorporate hyperparameter tuning for Random Forest and XGBoost.
- Validate with additional datasets for broader applicability.
- Develop a live dashboard for real-time credit scoring.

---

## How to Run

1. Clone this repository.
2. Install dependencies using:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook Credit_Risk_Analysis.ipynb
   ```
4. Inspect the visualizations and results.

---

## Contributing

Contributions are welcome! Feel free to fork this repository and submit pull requests for improvements or additional features.

---

## Acknowledgments

Special thanks to our instructors and classmates for their feedback, which greatly improved the project’s focus and results.
