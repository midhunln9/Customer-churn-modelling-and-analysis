# Customer Churn Analysis and Prediction Model

## Project Overview

This project is focused on predicting **customer churn** for a banking institution using a dataset of 10,000 customers. The goal is to identify customers who are likely to leave the bank (churn) so that proactive retention strategies can be developed. By analyzing demographic, financial, and behavioral attributes of the customers, we build predictive models that can help improve customer retention.

### Problem Statement
Customer churn poses a significant financial risk to businesses, especially in the banking sector. The challenge is to accurately predict whether a customer will churn based on various features, including credit score, age, geographical location, and account balance, among others. In this project, we use machine learning models to solve this problem.

## Dataset

The dataset consists of 10,000 rows and 14 columns, including features such as:

- **Credit Score**: Customer's credit score.
- **Geography**: Customer's country of residence (France, Spain, Germany).
- **Gender**: Male or Female.
- **Age**: Customer's age.
- **Tenure**: Number of years the customer has been with the bank.
- **Balance**: Account balance.
- **NumOfProducts**: Number of bank products held by the customer.
- **IsActiveMember**: Whether the customer is actively using the bank's services.
- **EstimatedSalary**: Customer's salary.
- **Exited**: Target variable indicating whether the customer churned (1) or not (0).

The target variable is **Exited**, which we aim to predict using the features.

## Project Workflow

### 1. Data Preprocessing
- **Null and Duplicate Values Check**: No missing or duplicate values were found in the dataset.
- **Feature Selection**: Removed irrelevant features such as `RowNumber`, `CustomerId`, and `Surname` which do not contribute to predicting churn.
- **Class Imbalance**: The dataset showed class imbalance (more customers not churning). We addressed this using **SMOTE** (Synthetic Minority Over-sampling Technique) to balance the dataset.

### 2. Exploratory Data Analysis (EDA)
- **Gender-wise Churn**: More female customers churned than male customers.
- **Geographical Impact**: Customers from Germany had a higher churn rate than those from France and Spain.
- **Product Ownership**: Customers with only one product were more likely to churn, while those with two products had the lowest churn rate.
- **Zero Balance Customers**: Customers with zero balance were more likely to churn.

### 3. Feature Engineering
- **New Features**: Created new features like:
  - **Total_Products**: Grouped customers based on the number of products they hold.
  - **Account_Balance**: Categorized customers with zero balance separately.
- **Log Transformation**: Applied log transformation on skewed features such as `Age` to normalize their distribution.

### 4. Model Building
We implemented and evaluated the following model:

- **Decision Tree Classifier**: Hyperparameter tuning was done using **GridSearchCV** to identify the best parameters for the model. The **best model** was trained using the following parameters:
  - `criterion`: gini
  - `max_depth`: 10
  - `min_samples_split`: 8
  - `splitter`: random

### 5. Model Evaluation
- **Training Accuracy**: 89.85%
- **Testing Accuracy**: 83.65%
- **F1 Score**: 0.84
- **Precision**: 0.84
- **Recall**: 0.84
- **Confusion Matrix**: Shows good performance with minimal false negatives and false positives.
  
### 6. Feature Importance
The most important features identified by the Decision Tree model are:
- **Total_Products**
- **Age**
- **IsActiveMember**
- **Geography**

The least important features are:
- **CreditScore**
- **HasCrCard**
- **Tenure**

## Conclusion
This project demonstrates how machine learning can be used to predict customer churn with reasonable accuracy. Insights from the model can guide banks to focus on high-risk customers (e.g., female customers, zero balance holders, or those from Germany) and develop retention strategies.

---

## Files in the Repository

- `Customer_Churn_Analysis.ipynb`: Jupyter Notebook with the full code implementation.
- `Churn_Modelling.csv`: Dataset used for the analysis.
- `README.md`: This file, explaining the project in detail.

