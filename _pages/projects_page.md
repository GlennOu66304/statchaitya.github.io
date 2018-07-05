---
title: "Projects"
permalink: /projects/
header:
---

Note: Work is in progress for updating the projects. Not all projects have been put up here.

# PREDICTIVE ANALYTICS

## 1. BNP Paribas Cardiff Claims Management - Kaggle

### *Rank: 225/2926 (Top 8%)*

[Competition home page](https://www.kaggle.com/c/bnp-paribas-cardif-claims-management)

[Github Repo of the code](https://github.com/statchaitya/Kaggle/tree/master/Bnp-paribas)

I participated in a Kaggle prediction problem in 2016. The dataset was provided by BNP Paribas and the aim of the competition was to predict whether for a claim, the approval can be accelerated leading to faster payments (safe claim) or whether more details regarding the claim must be taken into account in order to rightly process the claim.

I used several Machine learning algorithms in R and Python to achieve the task.

Final solution included
1. Tuned ExtRa Trees model
2. Tuned XgBoost model
3. Mean stack of these two models

## 2. Diabetes Re-admission prediction using Spark.ml, Spark 2.3.0 (Python API)

[Github repo with instructions to reproduce analysis]()

In this project I am using PySpark (2.3.0)'s latest ML library Spark.ML to predict whether a diabetic patient
would be readmitted in the future. I am using a dataset from UCI which can be [found here](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008).

The data set has over 1 lakh records of patients who underwent clinical care. The response variable is a 3 category variable having categories ">30" & "<30" which mean that the patient was readmitted and also indicates their age as well as "NO" for no readmission. I converted the problem to a binary classification problem indicating "Yes"/"No" for readmission.

The data had a lot of missing values encoded as "?". Spark 2.3.0 has a very high level interface called as DataFrames which are very flexible for data analysis, but still if we need a granular control over the data, we need to use RDDs. I had to use RDDs to map the "?" values to a Python None value.

After appropriate data cleaning, I used Logistic regression and Random Forests to fit a predictive model. My accuracy right now is **63%**.


## 3. Santander Customer Satisfaction - Kaggle

### *Rank: 540/5123 (Top 11%)*

[Competition home page](https://www.kaggle.com/c/santander-customer-satisfaction)

This was a Kaggle competition hosted in 2016. The dataset was provided by Santander bank and the aim of the competition was to predict whether a customer is satisfied or dis-satisfied with their banking experience.

I used several Machine learning algorithms in R and Python to achieve the task.

Final solution included
1. Two XgBoost models tuned on different sets of features
2. Mean stack of these two models
