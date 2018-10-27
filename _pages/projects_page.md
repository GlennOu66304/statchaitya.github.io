---
title: false
permalink: /projects/
author_profile: false
---

#  <span style="color:green">  <center> <u> Micro Projects </u> </center>  </span>

### <span style="color:green"> 1. Bank Marketing Analysis: Choosing predictive model having best ROI </span>

[Jupyter notebook](https://github.com/statchaitya/JupyterNotebooks/blob/master/Notebooks/Predictive%20Analytics%20of%20Term%20Deposit%20Subscriptions.ipynb), [Original Data](https://archive.ics.uci.edu/ml/datasets/bank+marketing)

**<u> Brief Summary: </u>** In this small notebook I use 'Cummulative Gains' graph to check which of the two fitted predictive models will give us a better ROI on future Term Deposit campaigns for a bank. Working iteratively to improve the analysis.

**<u> Things learnt: </u>** Using ROI to select predictive models, package 'modelplotpy'


### <span style="color:green"> 2. Shiny R: Visualizing Web KPIs </span>

[Link to the app. Note: App load will take a minute or two](https://statchaitya.shinyapps.io/VisualizingWebKPIsBasicShinyApp/)

**<u> Brief Summary: </u>** This is a basic Shiny app which lets users see how 5 key web performance metrics are doing at a daily and monthly level. Working to make the app better and to add more functionality.

**<u> Things learnt: </u>** Shiny app development, using HTML & CSS in Shiny, deploying Shiny app to the cloud


### <span style="color:green"> 3. Predictive Analytics using Spark Data Frame API </span>

[Github repo](https://github.com/statchaitya/Spark/tree/master/Diabetes%20Readmission), [Jupyter notebook](https://github.com/statchaitya/Spark/blob/master/Diabetes%20Readmission/rf_and_log_reg.ipynb), [Original Data](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008)

**<u> Brief Summary: </u>** Created predictive models in a Big Data environment using Spark. The target variable was Readmission (Y=1) or No Readmission (Y=0). Steps used: Replacing "?" as missing values using RDD.map(), integer-encoding, one hot encoding, Logistic Regression and Random Forest.

**<u> Things learnt: </u>** Worked with Spark.ML Data Frame API, worked with RDDs.

### <span style="color:green"> 4. US Domestic Airline Delays Visualization </span>

**Viewing at 1.5x is advised**

<iframe width="560" height="315" src="https://www.youtube.com/embed/W9KWhqwZqTg" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

### <span style="color:green"> 5. Time Series in R: Predicting Bitcoin Closing Values </span>

[Check out the notebook here](https://github.com/statchaitya/Time-Series-Analysis/blob/master/BitcoinTimeSeriesAnalysis/timeSeriesBitcoin_1.ipynb)

**<u> Brief Summary: </u>** Used Time Series Analysis in R to forecast the daily closing values of Bitcoin. Used exponential smoothing and ARIMA models. Compared all fitted models to naive forecasts and selected the best model. Also check out a small blog on [decisions to be taken before we start a Time Series Analysis project](https://statchaitya.github.io/settingupatimeseriesproject/).

**<u> Things learnt: </u>** Time Series, auto-arima, exponential smoothing.

### <span style="color:green"> 6. Data cleaning: Finding, manipulation and joining external data </span>

[Jupyter notebook](https://github.com/statchaitya/JupyterNotebooks/blob/master/Notebooks/DataManipulation_1.ipynb), [Original Loans Data](https://www.kaggle.com/kiva/data-science-for-good-kiva-crowdfunding), [External Data Souce](http://countrystat.psa.gov.ph/)

**<u> Brief Summary: </u>** In this notebook I execute the task of connecting multiple external data to the analysis table (philp_loans table). The external data was not in the appropriate form for a direct join and neither was main data. So I use text manipulation and joins to bring the data into the right form and then combining it together.

**<u> Things learnt: </u>** Text manipulation/Data cleaning, bringing keys in appropriate form for a join.

---


# <span style="color:red"> <center> <u> Competitions </u> </center> </span>


### <span style="color:red"> 1. BNP Paribas Cardiff Claims Management - Kaggle </span>

#### Rank: 225/2926 (Top 8%)

[Competition home page](https://www.kaggle.com/c/bnp-paribas-cardif-claims-management), [Github Repo of the code](https://github.com/statchaitya/Kaggle/tree/master/Bnp-paribas)

**<u> Things learnt: </u>** Working of bias-variance tradeoff, feature engineering, model tuning and using cross-validation.

### <span style="color:red"> 2. Santander Customer Satisfaction - Kaggle </span>

#### Rank: 540/5123 (Top 11%)

[Competition home page](https://www.kaggle.com/c/santander-customer-satisfaction)

**<u> Things learnt: </u>** AUC-ROC, F-measure, different ways to analyze a binary classification problems, working with class imbalance problem
