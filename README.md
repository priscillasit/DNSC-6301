# Credit Line Increase Model Card

## Basic Information
* Person or organization developing model: 
 Anh Phan, anhntphan@gwu.edu /
 Priscilla Sit, swsit@gwu.edu /
 Ziyin Wang, ziyinprc@gwu.edu 
* Model date: August, 2022
* Model version: 1.0
* License: MIT
* Model implementation code: [DNSC_6301_Project_team_15.ipynb](https://github.com/tuananh28394/DNSC-6301/blob/68544c12319df016ad0f612eb119b5c9b57da7d2/DNSC_6301_Project_team_15.ipynb)

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
  * Training row: 15,000
  * Validation rows: 7,500

## Test Data
* **Source of test data**: GWU Blackboard, email jphall@gwu.edu for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

## Model details
* **Columns used as inputs in the final model**: 'LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree
* **Software used to implement the model**: Python, scikit-learn
* **Version of the modeling software**: 1.0.2 sklearn
* **Python version**: 3.7.13
* **Hyperparameters or other settings of your model**:

`DecisionTreeClassifier(ccp_alpha=0.0, class_weight=None, criterion='gini',
                       max_depth=6, max_features=None, max_leaf_nodes=None,
                       min_impurity_decrease=0.0, min_impurity_split=None,
                       min_samples_leaf=1, min_samples_split=2,
                       min_weight_fraction_leaf=0.0, presort='deprecated',
                       random_state=12345, splitter='best')`

## Quantitative analysis
* **Metrics used to evaluate final model: Training AUC (for depth 6), Validation AUC (for depth 6), Test AUC and AIR**
* **Final values of data:**
  * **Training AUC**: 0.783722	
  * **Validation AUC**: 0.749610
  * **Test AUC**: 0.7438
 
  * **Asian-to-White AIR**: 1.00
  * **Black-to-White AIR**: 0.85
  * **Hispanic-to-White AIR**: 0.83
  * **Female-to-Male AIR**: 1.02
 
 **Historgrams**

![image](https://user-images.githubusercontent.com/112098061/186915250-78e8d0fd-7473-450e-88f9-647138b05c96.png)

The histograms describe the data by their frequency and distribution

**Correlation Heatmap**

![image](https://user-images.githubusercontent.com/112098061/186761364-d52d5f90-e852-4d2e-a8d6-b1e496dbac2c.png)

**Variable Importance**

![image](https://user-images.githubusercontent.com/112098061/186762464-3eccd1cf-5dcb-4036-b17f-4d9c4fd735d9.png)

**Iteration Plot**

![image](https://user-images.githubusercontent.com/112098061/186762616-fb636c4a-5021-43c4-8cdf-77ccb1176fb1.png)


**Decision Tree**

![image](https://user-images.githubusercontent.com/89337445/186931451-99a7f759-bdb9-4a08-9835-d171fa520b50.png)


## Ethical considerations

* **Describe potential negative impacts of using your model**:
- Math or software problems: 
  - As reflected in the varialbe importance barchart, the model relies heavily on the *PAY_0* variable which may neglect other variables' importance and affect the predicted outcome.
  2. Our model depends a lot on the packages we used. The different versions of the package may result in other potential intepretations.
  3. while explicit bias was reduced by not taking demographic data out from the model, there might still be bias hidden in the data
- Real-world risks: who, what, when or how: 
  1. The demographic issues in the model: there are some variables regarding demographic information such as race, gender, age or married status that should be taken into consideration when putting into the model
  2. Local discrimination - the model treats a small number of similar people differently
  3. Data privacy issues

* **Describe potential uncertainties relating to the impacts of using your model**:
- Math or software problems: there are many software tools available but most of them do not consider legality 
- Real-world risks: who, what, when or how?: 
  1. Malicious machine learning attacks e.g. data poisoning, model inversion, training data breaches. These might induce beneficial outcomes from a predictive or pattern recognition model or induce negative outcome for others, which could cause social or commercial chaos
  2. Legal aspect of collecting data: consent from the owners or privacy policies of the organizations possessing the data

* **Describe any unexpected or results**: 
  1. AUC is lower than expected
  2. The model predicts prediction depending on the data we feed to the model. It is unable to predict unexpected conditions if those data was not included in the dataset, for example covid or economic recession
