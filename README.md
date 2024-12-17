
# Credit Risk Analysis

This project demonstrates how machine learning techniques can be used to analyze credit risk, focusing on predicting borrowers' creditworthiness. The dataset comprises various financial attributes, such as loan amounts, interest rates, debt-to-income ratios, and credit statuses, that help model and evaluate financial risks. By using advanced data preprocessing and machine learning models, this project aims to derive meaningful insights that support smarter lending decisions.

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

The purpose of this project is to explore the relationships between borrowers' financial data, and determine their creditworthiness. We use machine learning techniques to create predictive models that estimate the likelihood of a borrower defaulting on their loan. By analyzing a dataset sourced from Kaggle’s Credit Risk Analysis repository, we apply various preprocessing techniques, feature engineering, and model evaluation strategies to predict the borrowers' credit risk grades.

We employ several machine learning models such as XGBoost and Random Forest, which are known for their efficiency in handling complex datasets and imbalanced class distributions. The final objective is to determine which model provides the most accurate predictions and insights into creditworthiness.

---

## How We Picked the Dataset

The dataset for this project was chosen from Kaggle’s Credit Risk Analysis repository. This dataset is well-suited for predicting credit risk, as it contains detailed, real-world financial attributes of borrowers, including:

- **Loan Amount (`loan_amnt`)**: Total loan amount requested by the borrower.
- **Funded Amount (`funded_amnt`)**: The amount funded by the lender.
- **Interest Rate (`int_rate`)**: The interest rate associated with the loan.
- **Debt-to-Income Ratio (`dti`)**: A ratio of the borrower’s monthly debt payments to their monthly income.
- **Employment Length (`emp_length`)**: The number of years the borrower has been employed.
- **Loan Status (`loan_status`)**: The status of the loan, such as “Current,” “Fully Paid,” “Charged Off,” etc.
- **Annual Income (`annual_inc`)**: The borrower’s reported annual income.

The dataset consists of 88,738 entries and 74 columns, which provide sufficient data to train and test various machine learning models for predicting credit risk. We focused on attributes directly related to financial strength, as they were key to determining the borrower’s ability to repay loans.

**Source**: Kaggle Credit Risk Dataset
**Source URL**: https://www.kaggle.com/datasets/ranadeep/credit-risk-dataset/data

---

## Difficulties and Concerns

### 1. **High Dimensionality**:
The dataset initially contained **887,000** rows, many of which were irrelevant or redundant. Having too many columns can introduce noise into the models, making them less efficient and harder to interpret. 

### 2. **Class Imbalance**:
One of the major challenges was the class imbalance present in the dataset. The majority of the loan statuses were "Fully Paid," while the "Default" and "Charged Off" statuses were much less frequent. This imbalance could cause the model to be biased toward predicting the majority class (Fully Paid), making it less sensitive to the minority classes (Default and Charged Off).

### 3. **Data Quality**:
The dataset had several columns with missing values. Some columns had more than 50% of missing values, which posed challenges during the preprocessing stage. We had to decide how to handle these missing values, whether by imputing them with a placeholder or removing the affected rows/columns.

---

## Adjustments Based on Feedback

After receiving feedback from the instructor, we made the following adjustments to improve the project:

### 1. **Focus on Key Financial Attributes**:
We decided to narrow the dataset down to the most relevant columns that could directly affect credit risk prediction. This included focusing on attributes like loan amount, interest rate, debt-to-income ratio, annual income, and loan status.

### 2. **Simplification of the Dataset**:
We removed unnecessary features like `id`, `member_id`, `url`, and other irrelevant columns that would not add value to the prediction of loan default or repayment. This helped in reducing the noise and allowed the models to focus on meaningful patterns in the data.

### 3. **Feature Engineering**:
We employed feature engineering techniques to create new meaningful features. For example, we created the `funded_amnt_to_annual_inc` and `revol_bal_to_annual_inc` features to understand how the loan amount and revolving balance compare to the borrower’s annual income.

### 4. **Handling Missing Data**:
Instead of filling missing values with default values or dropping entire rows with missing data, we used a combination of imputation strategies and dropped columns/rows with excessively missing values to ensure that the dataset was clean and consistent.

---

## How and Why We Removed Data

### 1. **Dropped Columns**:
We removed several columns that provided little to no predictive power, such as:
- `id` and `member_id`: Unique identifiers for borrowers, which do not contain any meaningful predictive information.
- `url`: A link column that was not relevant to the analysis.

### 2. **Dropped Rows**:
Rows with excessive missing values were removed to ensure that the data used in model training was of high quality. We dropped rows that had more than 50% missing data for critical attributes such as `loan_amnt`, `int_rate`, and `loan_status`.

### 3. **Sampling**:
To speed up computation and testing, we worked with a random 15% sample of the dataset. This reduced computational time during model training while still retaining a representative spread of data across different loan types.

---

## Methodology

### 1. **Feature Engineering**:
We created two new features:
- **`funded_amnt_to_annual_inc`**: The ratio of the funded amount to the borrower’s annual income.
- **`revol_bal_to_annual_inc`**: The ratio of the borrower’s revolving balance to their annual income.

These features were added to help capture more context about the financial relationship between the borrower’s income and their debts.

### 2. **Exploratory Data Analysis (EDA)**:
We visualized the distribution of key features and examined relationships between them. This included looking at correlations between features like interest rate and loan amount, and analyzing their effect on credit grades.

We also used scatter plots and histograms to understand the spread and distribution of key financial metrics. Correlation analysis was performed to identify which features had the most significant relationship with the target variable (`loan_status` or `grade`).

### 3. **Data Preprocessing**:
We handled categorical features by encoding them using techniques like One-Hot Encoding for nominal variables (`loan_status`, `grade`) and Label Encoding for ordinal variables (`term`). Numerical features like `loan_amnt`, `int_rate`, and `dti` were scaled using `StandardScaler` to standardize the range of values.

### 4. **Model Training**:
We trained multiple machine learning models on the processed data:
- **XGBoost**: Known for its efficiency in handling large datasets and its ability to handle missing values.
- **Random Forest**: A robust ensemble method that works well with imbalanced datasets and provides feature importance scores.

Models were evaluated based on their accuracy, precision, recall, F1-scores, and confusion matrices.

---

## Models Used

### 1. **XGBoost**:
XGBoost is an implementation of gradient boosted trees designed for speed and performance. It’s effective in classification tasks with large datasets and missing values. We used XGBoost because it provides:
- **Gradient Boosting**: Improves model performance by building multiple weak learners.
- **Handling of Missing Data**: XGBoost can handle missing values directly during training.
- **Robustness**: Less likely to overfit compared to traditional decision trees.

### 2. **Random Forest**:
Random Forest is an ensemble method that combines several decision trees to improve prediction accuracy. Each tree is trained on a random subset of the data, which helps avoid overfitting. It’s particularly useful for handling imbalanced datasets:
- **Feature Importance**: Random Forest allows us to identify which features are most important for predicting loan status.
- **Accuracy**: It performs well on complex datasets and avoids the problems of individual decision trees.

---

## Results

### Model Performance

- **Random Forest**: Achieved a testing accuracy of **96.2%**. This high accuracy demonstrates that Random Forest effectively classifies loan statuses and can identify default risks. The model also provides valuable insights into feature importance, with high-impact features like `int_rate` (interest rate) playing a key role in prediction.

- **XGBoost**: Delivered near-perfect precision, recall, and F1-scores, with an overall accuracy of **99%**. XGBoost's performance was exceptional, especially when dealing with imbalanced classes. The model's ability to handle missing data and focus on the most significant features made it the best-performing model in this project.
 
|                          |     N_estimators    |     Max_depth    |     Learning_rate    |     Subsample    |     ROC score    |
|--------------------------|---------------------|------------------|----------------------|------------------|------------------|
|     original             |     500             |     6            |     0.1              |     0.8          |     68           |
|     RandomOversampler    |     500             |     6            |     0.1              |     0.8          |     74.96        |
|     RandomSearchCV       |     172             |     9            |     0.1015308        |     0.71314      |     89.89        |
|     GridSearchCV         |     100             |     7            |     0.1              |     0.7          |     79.56        |
  

### Key Insights:
- **Interest Rate (`int_rate`)**: This was the most influential feature in determining loan grade. Higher interest rates are generally associated with higher-risk loans, and this feature emerged as a key determinant in both models.
- **Feature Engineering**: The introduction of new features like `funded_amnt_to_annual_inc` and `revol_bal_to_annual_inc` significantly improved model performance by providing more context on the borrower’s financial situation.

---

## Future Enhancements

- **Hyperparameter Tuning**: We plan to incorporate hyperparameter optimization for Random Forest and XGBoost to improve performance further.
- **Additional Datasets**: We aim to validate our models with additional datasets to ensure that the models generalize well to other types of loans.
- **Real-Time Dashboard**: We are considering developing a live dashboard that can provide real-time credit scoring and loan risk assessments.

---

## How to Run

1. Clone this repository.
2. Install dependencies using:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebooks:
   - `Loan_Status.ipynb`: This notebook handles data cleaning, encoding, and preprocessing.
   - `Grade_model.ipynb`: This notebook focuses on training and evaluating machine learning models.
4. Inspect the visualizations and results generated in each notebook.
5. **Quick Start**: To get started faster, use the **loan_sample.csv** file, which contains 100 rows for a quick test. This will help you explore the tool and see its results without working with the entire dataset.

---

## Contributing

Contributions are welcome! Feel free to fork this repository and submit pull requests for improvements or additional features.

### Contributors:
- Anand Bhagwat
- Usha Hariharan
- Asif Mahmud
- Venkat Varun Thamma

---

## Acknowledgments

Special thanks to our instructors and classmates for their feedback, which greatly improved the project’s focus and results.
