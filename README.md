# Customer Churn Classification Project

**Author**: [David Boyd](mailto:dboyd580@gmail.com)


## Overview

https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset

A telecommunications company wants to identify the leading factors of why a customer cancels their service. By understanding the factors which most strongly contribute to their churn rate they can set up work streams to help mitigate and reduce this effect over time, which will increase the LTV and overall ROI for the company. 

The goal of this project is to build a classifier which predicts whether a customer will churn given specific input metrics, these metrics range from data around location, package plans, usage and charges of plans, and interactions with customer services. As it is more costly to the business to incorrectly label a customer isn’t going to churn, we will be focusing on two key metrics, F1 score and recall, with recall taking precedence. I will be iterating over various models, both simple to more complex ensemble methods to identify which drives the best performance for the metrics defined above.

## Business Problem

For any business customer churn remains a big and prominent issue, but it's not always clear what factors are the biggest drivers to customers who churn. As a result the C-suite executives want to understand what are the key factors from their business which are driving customers to churn so they can create an action plan to mitigate these potential risks and improve customer LTV.


## Data

This project uses the SyriaTel Kaggle dataset, which can be found in `data.csv` in the data folder in this repository. The dataset includes 3,333 entries, and 21 columns.  Here are the columns in the dataset including our target variable, churn:

* `state`- The state in which the account owner resides.
* `account length`
* `area code` - Primary 3 digit area code associated to the account.
* `phone number` - 
* `international plan` - Indicator denoting whether or not the account has an international plan.
* `voice mail plan` - Indicator denoting whether or not the account has an voice mail plan.
* `number vmail messages` - Total number of voicemails for the phone number in question.
* `total day minutes` - Total minutes of calls made during the day.
* `total day calls` - Total number of calls made during the day. 
* `total day charge` - Total charge of calls made during the day.
* `total eve minutes` - Total minutes of calls made during the eve.
* `total eve calls` - Total number of calls made during the eve.  
* `total eve charge` - Total charge of calls made during the eve.
* `total night minutes` - Total minutes of calls made during the night.
* `total night calls` - Total number of calls made during the night.  
* `total night charge` - Total charge of calls made during the night.
* `total intl minutes` - Total minutes of calls made internationally
* `total intl calls` - Total number of calls made internationally.
* `total intl charge` - Total charge of calls made internationally.
* `customer service calls` - The total number of customer service calls made per account.
* `churn` - Target feature

## Method

After loading up the dataset and doing a brief amount of EDA to understand the following:
* What datatypes we were dealing with
* Were there any categorical variables
* Were there any null values, if so what columns featured them and of what datatype would they need to be imputed as
* Were there any categorical variables hidden as numerics
* Were there any outliers within the dataset

After the EDA was complete, I wanted to build several different classification models, ranging from simple decision trees to more in depth ensemble methods. To this first I split the data at a 30/70 level between test & train. I then created relevant functions to both perform feature engineering and also create a function to perform the pipeline needed to transform the data for each model. The types of models I evaluated as a baseline were DecisionTree, RandomForest, LogisitcRegression, AdaBoostClassifier, GradientBoostClassifier and XGBoostClassifier. There were a range of results as can be seen below.

![baseline_model_performance](https://github.com/db495/Customer_churn_classification_project/blob/main/images/baseline_model_performance.png)

From this list we wanted to see if we could improve performance by tuning the hyperparameters, using a GridSearchCV method I decided to only move forward with the DecisionTree, RandomForest & XGBoost options for hypertuning. Then the ROC-AUC curve was plotted out for the best performing model to see how it stands up to the test dataset.

![roc_auc_curve](https://github.com/db495/Customer_churn_classification_project/blob/main/images/roc_auc_curve.png)

Finally I looked to extract which features were the most important in driving customer churn. You can find the results below.

## Evaluation

Once the best model was selected (XGBoost) due to how it performed both on the F1 score and Recall score with the test dataset, it was the least impacted by overfitting. Below you can see both the confusion matrix for that final model and the features which had the biggest impact on predicting whether a customer would churn or not.

![confusion_matrix](https://github.com/db495/Customer_churn_classification_project/blob/main/images/confusion_matrix.png)

![most_imp_features](https://github.com/db495/Customer_churn_classification_project/blob/main/images/most_imp_features.png)

To make sense of the chart above:
X0 = State
X1 = Area Code
X2 = International Plan
X3 = Voicemail Plan

## Conclusions
From the feature importance chart above, we can see the areas that have the biggest influence on customer churn are:

* Not having an international plan in their account
* Not having a voice mail plan in their account
* The total charges per account
* The number of contacts being made to customer services

To set up a clear list of actions for the company, it is now worth performing a more thorough and in depth EDA around those features to identify what thresholds the business wants to set for their operations teams to try and achieve with the goal of reducing overall customer churn.

After these features, we can also see from the dataset that specific area codes and states have a higher influence than others. While it might be worth investigating this aspect, it is worth having caution what actions can be made around this discovery.


