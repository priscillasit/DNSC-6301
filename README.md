# Credit Line Increase Model Card

## Basic Information
* Person or organization developing model: 
 Anh Phan, anhntphan@gwu.edu /
 Priscilla Sit, swsit@gwu.edu /
 Ziyin Wang, ziyinprc@gwmail.gwu.edu 
* Model date: August, 2022
* Model version: 1.0
* License: MIT
* Model implementation code: [DNSC_6301_Project_team_15.ipynb](https://github.com/tuananh28394/DNSC-6301/blob/2878c85f88399c9da87d59385f475308bb8cef24/DNSC_6301_Project_team_15.ipynb)

## Intended Use
* **Primary intended uses**: This model is an example probability of default classifier, with an example use case for determining eligibility for a credit line increase.
* **Primary intended users**: Group assignment in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope

## Training Data
* **Data Dictionary**:

Name          | Modeling Role | Measurement Level | Description
------------- | ------------- | -------------     | -------------
ID            | ID            | int               | unique row indentifier
LIMIT_BAL     | input         | float             | amount of previously awarded credit
SEX           | demographic information            | int               | 1 = male; 2 = female
RACE     | demographic information         | int             | 1 = hispanic; 2 = black; 3 = white; 4 = asian
EDUCATION           | demographic information            | int               | 1 = graduate school; 2 = university; 3 = high school; 4 = others
MARRIAGE     | demographic information         | int             | 1 = married; 2 = single; 3 = others
AGE           | demographic information          | int               | age in years
PAY_0, PAY_2 - PAY_6     | inputs         | int             | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above
BILL_AMT1 - BILL_AMT6     | inputs         | float             | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005
PAY_AMT1 - PAY_AMT6           | inputs         | float               | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005
DELINQ_NEXT	           | target          | int               | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time

* **Source of training data**: GWU Blackboard, email jphall@gwu.edu for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
 * training data (15000 rows and 20 columns)
 * validation data: 7500 rows and 20 columns

## Test Data
* **Source of test data**: GWU Blackboard, email jphall@gwu.edu for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

## Model details
* **Columns used as inputs in the final model**: 'LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree
* **Software used to implement the model**: Python, scikit-learn
* **Version of the modeling software**: 1.0.2
* **Python version**: 3.7.13
* **Hyperparameters or other settings of your model**:
`DecisionTreeClassifier(ccp_alpha=0.0, class_weight=None, criterion='gini',
                       max_depth=6, max_features=None, max_leaf_nodes=None,
                       min_impurity_decrease=0.0, min_impurity_split=None,
                       min_samples_leaf=1, min_samples_split=2,
                       min_weight_fraction_leaf=0.0, presort='deprecated',
                       random_state=12345, splitter='best')`

## Quantitative analysis
* **Metrics used to evaluate final model: AUC and AIR
* **Final values of data:

 Training | Validation | Test 
------------- | ------------- | -------------
 1 | 2 |3  |


**Correlation Heatmap
![image](https://user-images.githubusercontent.com/112098061/186761364-d52d5f90-e852-4d2e-a8d6-b1e496dbac2c.png)
