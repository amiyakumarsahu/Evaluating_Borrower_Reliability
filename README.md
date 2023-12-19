# Evaluating_Borrower_Reliability
##  Table of Contents
1. [Installation](#Installation)
2. [Description](#Description)
3. [Data](#Data)
4. [Results](#Results)

## Installation
- Python 3.11.4
- Libraries: 
  - [NumPy](http://www.numpy.org/)
  - [Pandas](http://pandas.pydata.org)
  - [matplotlib](http://matplotlib.org/)
  - [seaborn](https://seaborn.pydata.org/)
  - [scikit-learn](http://scikit-learn.org/stable/)


## Description
Credit risk management remains a significant challenge for banks given the inefficient data management, limited view of risk measures, lack of risk assessment tools, and less than intuitive visualization process into the borrowers’ ability to pay back. A thorough assessment of the borrowers’ capability and complete understanding of loan loss reserve is crucial to managing credit risk exposure and mitigating losses. In this scenario, traditional scorecards by themselves are no longer enough to determine credit lending.
This project compares the performances of a few algorithms to determine the creditworthiness of customers. The dataset that has been used in this project contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005. The 3 machine learning algorithms used in this project are Logistic Regression, Decision Tree Classification, and Random Forest Classification. For comparison of the performances of these models, ROC Curve and Cross-Validation Accuracy have been used.

## Data 
`credit card clients.xlsx` - This dataset contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005.
Dataset Source : [Taiwan Bank Dataset](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)

This research employed a binary variable, default payment (Yes = 1, No = 0), as the response variable. This study reviewed the literature and used the following 23 variables as explanatory variables:
X1: Amount of the given credit (NT dollar): it includes both the individual consumer credit and his/her family (supplementary) credit.
X2: Gender (1 = male; 2 = female).
X3: Education (1 = graduate school; 2 = university; 3 = high school; 4 = others).
X4: Marital status (1 = married; 2 = single; 3 = others).
X5: Age (year).
X6 - X11: History of past payments. We tracked the past monthly payment records (from April to September, 2005) as follows: X6 = the repayment status in September, 2005; X7 = the repayment status in August, 2005; . . .; X11 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; . . .; 8 = payment delay for eight months; 9 = payment delay for nine months and above.
X12-X17: Amount of bill statement (NT dollar). X12 = amount of bill statement in September, 2005; X13 = amount of bill statement in August, 2005; . . .; X17 = amount of bill statement in April, 2005. 
X18-X23: Amount of previous payment (NT dollar). X18 = amount paid in September, 2005; X19 = amount paid in August, 2005; . . .;X23 = amount paid in April, 2005.


## Results

To identify the creditworthy applicants, we performed the following steps:

  **Step 1: Preprocessing**
  - Removed certain columns either due to low variability or no logical connection with the target.
  - Cleaned data of ambiguous data values in some rows.
  - Split the data into training and testing sets with `train_test_split()` 
  
  **Step 2: Data Visualization**
  - Calculating the target (Default) percentage (Yes, No).
  - Describing the data for mean, median, etc for all individual columns.
  - Graphically Representing the dependency of various columns on target (Default).

  **Step 3: Creating a Training and Predicting Pipeline**
  - Initialized and fit classification models:
    - `LogisticRegression()`
    - `DecisionTreeClassifier()`
    - `RandomForestClassifier()`
  - Implemented `LogisticRegression()` on Original Data, Standardized Data, and Data obtained post-Recursive Feature Elimination and obtained a confusion matrix along with the respective accuracy
  - Implemented `DecisionTreeClassifier()` on standardized data and obtained a confusion matrix along with the accuracy.  
  - Implemented `RandomForestClassifier()` on standardized data and improved the result by employing Hyperparameterization via `RandomSearchCV()` for the following parameters `n_estimators`, `max_features` and `max_depth` and obtained a confusion matrix along with the accuracy.
  
  **Step 4: Comparison of Model Performance**
  - Plotted a Receiver operating characteristic (ROC) Curve to predict which model is better at distinguishing between positive and negative class  
  - K-fold Cross Validation was implemented to check which model provided the least bias and avoided overfitting of data
