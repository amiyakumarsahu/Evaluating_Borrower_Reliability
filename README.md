# Evaluating_Borrower_Reliability
##  Table of Contents
1. [Installation](#Installation)
2. [Description](#Description)
3. [Data](#Data)
4. [File Descriptions](#File-Descriptions)
5. [Results](#Results)

## Installation
- Python 3.7.2
- Libraries: 
  - [NumPy](http://www.numpy.org/)
  - [Pandas](http://pandas.pydata.org)
  - [matplotlib](http://matplotlib.org/)
  - [seaborn](https://seaborn.pydata.org/)
  - [scikit-learn](http://scikit-learn.org/stable/)

You will also need to have software installed to run and execute an [iPython Notebook](http://ipython.org/notebook.html)

## Description
Credit risk management remains a significant challenge for banks given the inefficient data management, limited view of risk measures, lack of risk assessment tools, and less than intuitive visualization process into the borrowers’ ability to pay back. A thorough assessment of the borrowers’ capability and complete understanding of loan loss reserve is crucial to managing credit risk exposure and mitigating losses. In this scenario, traditional scorecards by themselves are no longer enough to determine credit lending.
This project compares the performances of few algorithms to determine the credit worthiness of customers. The dataset that has been used in this project contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005. The 3 machine learning algorithms used in this project are Logistic Regression, Decision Tree Classification, and Random Forest Classification. For comparison of the performances of these models, ROC Curve and Cross Validation Accuracy has been used.

## Data 
`default of credit card clients.xls` - This dataset contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005.
Dataset Source : [Taiwan Bank Dataset](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)

This research employed a binary variable, default payment (Yes = 1, No = 0), as the response variable. This study reviewed the literature and used the following 23 variables as explanatory variables:
X1: Amount of the given credit (NT dollar): it includes both the individual consumer credit and his/her family (supplementary) credit.
X2: Gender (1 = male; 2 = female).
X3: Education (1 = graduate school; 2 = university; 3 = high school; 4 = others).
X4: Marital status (1 = married; 2 = single; 3 = others).
X5: Age (year).
X6 - X11: History of past payment. We tracked the past monthly payment records (from April to September, 2005) as follows: X6 = the repayment status in September, 2005; X7 = the repayment status in August, 2005; . . .;X11 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; . . .; 8 = payment delay for eight months; 9 = payment delay for nine months and above.
X12-X17: Amount of bill statement (NT dollar). X12 = amount of bill statement in September, 2005; X13 = amount of bill statement in August, 2005; . . .; X17 = amount of bill statement in April, 2005. 
X18-X23: Amount of previous payment (NT dollar). X18 = amount paid in September, 2005; X19 = amount paid in August, 2005; . . .;X23 = amount paid in April, 2005.


## File Descriptions

You can find the results of the analysis in the following iPython Notebook Notebook:


Alterinatively, run one the following commands in a terminal after navigating to the top-level project directory `predicting_creditworthiness/` (that contains this README):

```bash
ipython notebook Credit_Worthiness_of_customer.ipynb.ipynb
```  
or
```bash
jupyter notebook Credit_Worthiness_of_customer.ipynb.ipynb
```

This will open the iPython Notebook software and project file in your browser.

## Results

To identify the creditworthy applicants, we performed the following steps:

  **Step 1: Preprocessing**
  - Removed certain collumns either due to low variability or no logical connection with the target.
  - Cleaned data of ambiguous data values in some rows.
  - Split the data into training and testing sets with `train_test_split()` 
  
  **Step 2: Data Visualization**
  - Calculating the target (Default) percentage (Yes, No).
  - Describing the data for mean, median, etc for all individual collumns.
  - Graphically Representing the dependency of various collumns on target (Default).

  **Step 3: Creating a Training and Predicting Pipeline**
  - Initialized and fit classification models:
    - `LogisticRegression()`
    - `DecisionTreeClassifier()`
    - `RandomForestClassifier()`
  - Implemented `LogisticRegression()` on Original Data, Standardized Data and Data obtained post Recursive Feature Elimination and obtained a confusion matrix for along with the respective accuracy
  - Implemented `DecisionTreeClassifier()` on standardized data and obtained a confusion matrix along with the accuracy.  
  - Implemented `RandomForestClassifier()` on standardized data and improved the result by employing Hyperparameterization via `RandomSearchCV()` for the following parameters `n_estimators`, `max_features` and `max_depth` and obtained a confusion matrix along with the accuracy.
  
  **Step 4: Comparison of Model Performance**
  - Plotted a Receiver operating characteristic (ROC) Curve to predict which model is better distinguishing between positive and negative class  
  - K-fold Cross Validation was implemented to check which model provided the least bias and avoided overfitting of data
