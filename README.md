# Pump_It_Up_Challenge

Pump it up machine learning challenge competition in DataDriven.

Github Link:- https://github.com/nisho06/Pump_It_Up_Challenge

Competition Link:- https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

This repositry contains the code used for submission of Pump it Up: Data Mining the Water Table challenge on DrivenData.

**Best accuracy obtained:- 0.8211**

**Final Rank:- 942 (As of 17th September)**

Following steps were taken to solve the problem

***

## 1) Explatory Data Analysis

Explatory data analysis were done using pandas library function as well as using the graphs plotted with matplotlib library.

The findings gathered through the EDA is as follows;
- The columns with null values were found. ['funder', 'installer', 'subvillage', 'public_meeting', 'scheme_management' ,'permit']. From which the feature 'scheme_name' has about 50% of null values.
- The categorical columns and their cardinality of categories were found. 
  - 'wpt_name' column seems to have categories around 37400.
  - 'recorded_by' column seems to have only one category throughout the whole dataset.
- A graph function was written inorder to obtain how much a particular category of a feature affects the target variable. This helped to differentiate similar features. The features that almost had the same characteristics were as follows.
  - scheme_management, management and management_group
  - quantity and quantity_group
  - source, source_type and source_class
  - water_quality and quality_group
  - payment and pay
  - extraction_type, extrcation_type_group and extraction_type_class
  - waterpoint_type and waterpoint_type_group
- The numerical columns which contain 0 values were obtained. From which 'amount_tsh' seems to have 70% of 0 values which is abnormal.

***

## 2)Preprocessign and Feature Engineering

- The features which has more categories, more null values and most similar characteristic features have been removed as an early step.
- The features that have been dropped were,
  - 'amount_tsh'
  - 'funder'
  - 'num_private'
  - 'region'
  - 'scheme_name'
  - 'recorded_by'
  - 'extraction_type'
  - 'extraction_type_class'
  - 'management'
  - 'payment_type'
  - 'water_quality'
  - 'quantity'
  - 'source_class'
  - 'source'
  - 'waterpoint_type_group'
- An extension to the Imputation has been carried out for the categorical features.
  - A new feature has been created for each respective categorical feature indicating whether the particular feature data was missing or not. (Simple Imputer has been used)
  - Then, the null values of the categorical features have been replaced with the respective most frequent category of the particular categorical feature. (eg:- 'VWC' in scheme_management)
- Categorical feature with abnormal data has been found. Here, 'installer' feature has 0 values. Those values were also also imputed with the most frequent feature.
- The numerical features which has 0 in the particular feature has been imputed with the mean of the particular corresponding feature.
- The target variable has been encoded using Label Encoder.
- Categorical encoding has been done in the CatBoost model itself.

***

## 3) Model and Fine-tuning

- Since Catboost algorithm most probably finding out the best possible hyper parameter as itself, there is no need much hyper paramter tuning. Eventhough, if there is a need to improve performance, more domain knowledge is being required.
  - Categorical features were specified.
  - Model has been trained for 1000 iterations
- Other classification algoithms such as XGBoost, logistic regression and random forest also have been tried out. But didn't gave greater performance than the CatBoost algorithm

***

## 4) Post Processing

SHAP values were generated using Catboost mode, in which the importance of feature for the model training has been gained. According to the analysis, 'quality_group', 'ward' and 'lga' were the feature that have a greater impact and 'gps_height', 'quality_group' and 'latitude' are the features which has the lesser impact on the target variable.

***

## Proof of submission

**DrivenData username:- moracse_170410X**

**Score and the rank of the submission** 

<img width="774" alt="Screenshot 2021-09-17 at 23 18 03" src="https://user-images.githubusercontent.com/47827247/133831927-34efac71-b734-4f3d-9a61-54388369f13b.png">





