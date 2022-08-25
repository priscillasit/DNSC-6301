# Credit Line Increase Model Card

## Basic Information
* Person or organization developing model: 
 Anh Phan, anhntphan@gwu.edu /
 Priscilla Sit, swsit@gwu.edu /
 Ziyin Wang, ziyinprc@gwu.edu 
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

    Name      | Modeling Role  |    Measurement Level      | Description  
------------- | -------------  |  -------------            | -------------
ID            | ID             |  int                      |  unique row indentifier 
LIMIT_BAL	    | input          | float                     | amount of previously awarded credit

* **Source of training data**: GWU Blackboard, email jphall@gwu.edu for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
+ training data (15000 rows and 20 columns)
+ validation data: 7500 rows and 20 columns
