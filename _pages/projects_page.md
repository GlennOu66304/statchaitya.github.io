---
title:
permalink: /projects/
header:
---
### 1. BNP Paribas Cardiff Claims Management - Kaggle

#### *Rank: 225/2926 (Top 8%)*

[Competition home page](https://www.kaggle.com/c/bnp-paribas-cardif-claims-management)

[Github Repo of the code](https://github.com/statchaitya/Kaggle/tree/master/Bnp-paribas)

I participated in a Kaggle prediction problem in 2016. The dataset was provided by BNP Paribas and the aim of the competition was to predict whether for a claim, the approval can be accelerated leading to faster payments (safe claim) or whether more details regarding the claim must be taken into account in order to rightly process the claim.

Final solution included a tuned ExTra trees model, xgboost model and a ensemble of these two models (average).

### 2. Diabetes readmission prediction using Spark.ml, Spark 2.3.0 (Python API)

[Github repo](https://github.com/statchaitya/Spark/tree/master/Diabetes%20Readmission)

[Jupyter notebook](https://github.com/statchaitya/Spark/blob/master/Diabetes%20Readmission/rf_and_log_reg.ipynb)

In this project I am using PySpark (2.3.0)'s latest ML library Spark.ML to predict whether a diabetic patient
would be readmitted in the future. I am using a dataset from UCI which can be [found here](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008).

The data set has over 1 lakh records of patients who underwent clinical care. The response variable is a 3 category variable having categories ">30" & "<30" which mean that the patient was readmitted and also indicates their age as well as "NO" for no readmission. The problem has been converted to binary classification to predict just the 'readmission' and not the age.

Algorithms used: Logistic Regression & Random Forests. Accuracy = **63%**.


### 3. Santander Customer Satisfaction - Kaggle

#### *Rank: 540/5123 (Top 11%)*

[Competition home page](https://www.kaggle.com/c/santander-customer-satisfaction)

This was a Kaggle competition hosted in 2016. The dataset was provided by Santander bank and the aim of the competition was to predict whether a customer is satisfied or dis-satisfied with their banking experience.

Final solution included an mean ensemble of two xgboost models trained with a different set of features. Set of features which I had come up after trying a lot of combinations of parameters/features.


### 4. Data Visualization: R, ggplot2: Kiva loans prioritization - Kaggle

Kiva.org is a non-profit based out of San Francisco which connects the lenders(us) with needy borrowers throughout the world for personal loans. In early 2018 they provided their loans information on kaggle and challenged kagglers to find out poor regions from the data for which the loans could be prioritized and made available more aggressively than other regions.

I used ggplot2 and other data Visualization packages in R to locate a potential poor segment in Philippines by using the Kiva loans data and some external financial indicators for the sub-regions in philippines.

The documented work done can be found in following **jupyter notebooks**


[Notebook 1 - Loan Characteristics in different continents](https://github.com/statchaitya/Kaggle/blob/master/Kiva/Notebooks/Notebook%201%20-%20Loan%20characteristics%20in%20different%20continents.ipynb)


[Notebook 2 - Borrower profiles and characteristics](https://github.com/statchaitya/Kaggle/blob/master/Kiva/Notebooks/Notebook%202%20-%20Borrower%20profiles%20and%20characteristics.ipynb)


[Notebook 3 - Prioritizing loans in Philippines](https://github.com/statchaitya/Kaggle/blob/master/Kiva/Notebooks/Notebook%203%20-%20Prioritizing%20Loans%20in%20Philippines.ipynb)


[Kaggle home page for Kiva Analysis](https://www.kaggle.com/kiva/data-science-for-good-kiva-crowdfunding/home)

[Github page for kiva analysis](https://github.com/statchaitya/Kaggle/tree/master/Kiva)
