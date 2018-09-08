---
title: "Time Series - Initial Fundamental Choices"
date: 2018-09-06
tags: [Time Series Forecasting]
excerpt: "Time Series Analysis, Forecasting"
author_profile: false
read_time: false
---

> The main point of this post is just to throw light on things which we might not have considered till now while starting a Time Series project because we have been accustomed to using ready made clean TS datasets (Well, as recent college grad at least I have been till now)

## <center> Difference Between Business and a Local Setup </center>

While doing Time Series analysis just for fun or for practice out of work environment, we are lucky to be directly given a
ready made clean dataset of a univariate time series. The goal then is to just get as good a prediction as possible. But
when starting on a Time Series project in a business environment, we have to think about a lot of things which
might prove to be crucial in the eventual outcome of the project. Out of the many like choice of metric/metrics, time level, handling irregularity, handling missing values etc.. I am trying to cover the first two in this post.

In this post I try to focus on 2 fundamental choices we face while starting a time series project and their relation with the outcome/business decision using an example of a retail store chain. Understanding this simple example will hopefully enable us to think about the metric and time level before we jump into a TS project in a business environment.

## <center> Metrics, Time Granularity and Decisions </center>

> Choice of a metric is important and affects the decisions we want to take

It is important to choose the right metric for a particular goal, because <u>the metric has a direct impact on the goal/ business decisions</u>. To understand this consider an example of a retail store chain. The metric <span style="color:red">Number of item X sold</span> deals with the **<span style="color:green">decision of restocking item X</span>** while the metric <span style="color:red"> Number of visitors entering the store</span> deals with the **<span style="color:green">decision of assignment of Number of personnel on a particular day</span>**. This is a very simple case but in general each <u>different strategic goal might have one or several metrics associated with it</u> and can on the other hand have one or several metrics which are not at all associated with it.. Hence it is important that we keep the potential decisions in mind and start with the appropriate metric/metrics.

> An appropriate time level?

**Short Term**

  Lets consider the same example of a retail store chain. <u>Short term forecasts</u> (Daily in this case. In cases like log files data forecasting, a minute will be short term and an hour will be medium/long term) <u>are much more accurate and can be used to take decisions that make sense on a daily basis</u> ex: Keeping an eye on the product shelves, anticipating a high sale day and allocating more employees on that day etc..

**Medium Term**

  For medium term forecasts (weeks in this case), we can probably think of hiring new people at stores where the sales are to increase and staffing is less. <u>Recruiting takes weeks so this is a good example of a decision to be taken w.r.t medium term forecasts</u>. Even catching products with an increasing trend and planning on how to make more room for them is an example of a medium term decision.

**Long Term**

  If the timeframe of a forecast is long i.e. if we are forecasting for monthly 2 years in the future then these forecasts might help in <u>decisions like increasing the number of stores, enlarging existing store space etc..</u>

Hence, <u>contemplating on the time level of a TS and the potential decisions for our goal accomplishment</u> (given that we have the flexibility to think of multiple time levels) <u>is also the right thing to do.</u>

> One more thing to note is that the forecasts will get less accurate as we go ahead in time. This is a general law.

So if we argue, why can't we use Daily (short term) forecasts to take long term decisions, the answer to that lies in the above general property of a time series.

**Not always will we have to think of these things. Most of the times, the choices would be trivial but in times where you have the flexibility to think about different metrics, time levels and decisions in a business environment, this understanding of their inter-relation would hopefully be useful.**

> *Please leave a comment about what you think (Then I will at least know somebody was here). Cheers! ;)*
