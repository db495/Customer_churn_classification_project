# Customer Churn Classification

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

## Methods



## Evaluation



## Conclusions
From the feature importance chart above, we can see the areas that have the biggest influence on customer churn are:

* Not having an international plan in their account
* Not having a voice mail plan in their account
* The total charges per account
* The number of contacts being made to customer services

To set up a clear list of actions for the company, it is now worth performing a more thorough and in depth EDA around those features to identify what thresholds the business wants to set for their operations teams to try and achieve with the goal of reducing overall customer churn.

After these features, we can also see from the dataset that specific area codes and states have a higher influence than others. While it might be worth investigating this aspect, it is worth having caution what actions can be made around this discovery.


