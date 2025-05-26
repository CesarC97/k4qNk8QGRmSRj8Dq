## Introduction
The primary objective of this project is developing a robust machine learning system that leverages information coming from call center data in the European banking market. Additionally, this machine learning system will offer high success outcomes while offering interpretability for clients to make informed decisions. It needs to be predicted whether or not a customer will subscribe to a term deposit.

## Data Description
The data comes from direct marketing efforts of a European banking institution. The marketing campaign involves making a phone call to a customer, often multiple times to ensure a product subscription, in this case a term deposit. Term deposits are usually short-term deposits with maturities ranging from one month to a few years.

- age : age of customer (numeric)
- job : type of job (categorical)
- marital : marital status (categorical)
- education (categorical)
- default: has credit in default? (binary)
- balance: average yearly balance, in euros (numeric)
- housing: has a housing loan? (binary)
- loan: has personal loan? (binary)
- contact: contact communication type (categorical)
- day: last contact day of the month (numeric)
- month: last contact month of year (categorical)
- duration: last contact duration, in seconds (numeric)
- campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
- y: has the client subscribed to a term deposit? (binary)

## Exploratory Data Analysis
- The dataset has 40,000 observations and 14 variables
- There are 5 numerical variables (age, balance, day, duration, and campaign), 5 categorical variables (job, marital, education, contact, and month), and 4 binary variables(default, housing, loan, and y)
- There are no missing values
- The proportion of clients that did not subscribe to a term deposit (92.8%) is relatively higher than the clients that did (7.2%)

## Imbalance Challenge
There is an imbalance due to the proportion of the clients that did not subscribe to a term deposit (92.8%) overweights the clients that did (7.2%). The methods considered for this imabalance challenge are Random Undersampling, Synthetic Minority Over-sampling Technique (SMOTE), Sythetic Minority Over-sampling Technique and Edited Nearest Neighbor (SMOTE-ENN), and Sythetic Minority Over-sampling Technique and Tomek links (SMOTE-Tomek).

## Stage 1: Before Calls
In order to predict the customer's interest in a term deposit based on their profile, the related features day ,month, duration, campaign, and contact need to be excluded for model implementation. The four balanced datasets obtained from previous step will be considered. The models implemented are Pycaret compare models and TPOT models.

## XGBoost Model and Optuna
XGBoost (Extreme Gradient Boosting) is a popular machine learning algorithm designed for both classification and regression tasks. It is an optimized implementation of gradient boosting, which is a type of ensemble learning method that combines the predictions of multiple base learners (usually decision trees) to improve accuracy and robustness.
Using Optuna to optimize hyperparameters for an XGBoost model is a great approach for finding the best model configuration. Optuna is a powerful hyperparameter optimization library that uses Bayesian optimization to search for the optimal set of hyperparameters. The training dataset obtained from the SMOTE-Tomek balancing method will be used for the model implementation.

The duration time that can potentially be saved is 1,750,417 seconds (29,173.62 minutes)
The recall score for class 1 is 0.87, which means that the model correctly identifies 87% of the actual positive cases (subscribers)
The duration time that can potentially be saved at the cost of losing around 13% of the subscriptions is about 486.23 hours (20.25 days).
This model works very effectively identifying potential term deposit subscribers before making calls, and it saves a lot of human effort as well.

## Stage 2: After Calls
In this stage, the calls have been made already; now every single feature of the datasets is considered to develop a robust machine learning system. The focus will be on precision for the subscribers.

- The duration time that can potentially be saved is 5,461,944 seconds (91,032.4 minutes)
- The recall score for class 1 is 0.97, which means that when the model predicts a customer will subscribe to a term deposit, the prediction is correct 97% of the time.
- The duration time that can potentially be saved at the cost of losing 3% of the subscriptions is about 1,517.20 hours (63.22 days).
- This model works very effectively identifying potential term deposit subscribers after the calls are made, and it saves a lot of human effort as well.

## Clustering Techniques
In this final step of the project, the main focus is performing some clustering techniques to figure out the variables that potentially help the model to correctly predict the term deposit susbcribers.

There are some average characteristics in 3 different clusters that best idetify potential subscribers:

- Clients older than 40 years
- Clients with management jobs
- Married clients
- Clients that do not have credit in default
- Clients that have a housing loan
- Clients that do not have a personal loan
- Clients that us a cellular as a contact communication type

## Conclusion
- The dataset has 40,000 observations and 14 variables, there are 5 numerical variables (age, balance, day, duration, and campaign), 5 categorical variables (job, marital, education, contact, and month), and 4 binary variables(default, housing, loan, and y), there are no missing values, and the proportion of clients that did not subscribe to a term deposit (92.8%) is relatively higher than the clients that did (7.2%)
- It can be noticed the clients that tend to not subscribe to a term deposit share some common characteristics with the clients that tend to do so, such as married clients, clients with secondary education, clients that use cellular as contact communication type, clients with May as the last month of contact; it happens to notice that there are no records of September as the last month of contact, clients that have no credit in default, clients that have a housing loan, etc.
- The methods considered for the imabalance challenge created four different balanced training datasets that were considered to determine whether or not a client will subscribe to a term deposit
- In Stage 1 (Before Calls), the XGBoost model's performance yielded significant results, and it worked very effectively identifying potential term deposit subscribers before making calls, which saves a lot of human effort as well
- In Stage 2 (After Calls), the model predicts a customer will subscribe is correct more than 90% of the time, and saves a lot of human effort
- The different clustering techniques performed yielded 3 different clusters with common variables that are potentially significant to determine the subscription of a client

[Tableau Public](https://public.tableau.com/app/profile/cesar.corral/vizzes)
