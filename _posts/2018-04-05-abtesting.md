---
title: "Log Loss: Explained"
date: 2018-04-05
tags: [Metrics]
excerpt: "Machine Learning, metrics, predictive analytics"
---

## Intuition behind log loss using its formula

![Uncertainty](/images/uncertainty.jpg)

Log loss is used when we have $${0,1}$$ response. This is usually because when we have $${0,1}$$ response, the best models give us values in terms of probabilities.
In simple words, log loss measures the **uncertainty** of the probabilities of your model by comparing them to the true labels. Let us look closely at its formula and see how it measures the **uncertainty**.


Now the question is, your training labels are **0** and **1** but your training predictions are **0.4, 0.6, 0.89, 0.1122 etc..** So how do we calculate a measure of the error of our model ? If we directly classify all the observations having values > 0.5 into 1 then we are at a high risk of increasing the misclassification. This is because it may so happen that many values having probabilities **0.4, 0.45, 0.49** can have a true value of **1**.
This is where **logloss** comes into picture.


Now let us closely follow the formula of **logloss**.


The formula for **logloss** is :
$$logLoss  =  \frac{-1}{N}  \sum_{i=1}^{N}(y_{i}(log{p_{i}})+(1- {y_{i}})log(1-p_{i}))$$

There can be 4 major cases for the values of $$y_{i}$$ and $$p_{i}$$

Case 1 : $$y_{i} = 1 $$ , $$p_{i}$$ = High , $$ 1 - y_{i} = 0$$ , $$1 - p_{i}$$ = Low


Case 2 : $$y_{i} = 1 $$ , $$p_{i}$$ = Low , $$ 1 - y_{i} = 0$$ , $$1 - p_{i}$$ = High


Case 3 : $$y_{i} = 0 $$ , $$p_{i}$$ = Low , $$ 1 - y_{i} = 1$$ , $$1 - p_{i}$$ = High


Case 4 : $$y_{i} = 0 $$ , $$p_{i}$$ = High , $$ 1 - y_{i} = 1$$ , $$1 - p_{i}$$ = Low

*Case 1*:
In this case y = 1 and p = high implies that we have got things right! Because the true value of the response agrees with our high probability. Now look closely.. occurence of *Case 1* will significantly inflate the sum because, Yi * log (Pi) would be high and simultaneously the other term in the summation would be zero since 1 - Yi = 1 - 1 = 0. So more occurrences of Case 1 would inflate the sum and consequently inflate the mean.
Also note that this is possible because if Pi > Pi-1 , log (Pi) > log (Pi-1)


*Case 2*:
In this case y = 1 and p = low. This is a totally undesirable case because our probability of Y being 1 is low but still the true value of Y is 1. Now again looking at the formula closely, the second term in the summation would be zero since 1- yi would be zero. And since p = low, Yi * log (Pi) would not inflate the sum as much as Case 1. So *Case 2* would ultimately not affect the sum a lot.


Similarly the occurrences of *Case 3* would inflate the sum significantly and occurrences of *Case 4* would not.
Now coming back to the main question, how does log loss measure UNCERTAINTY of your model? The answer is simple. Suppose we have more of *Case 1s* and *Case 3s*, then the sum inside the logloss formula would be greater (would tend to increase). This would imply that the mean (/N) would also tend to increase and will be substantially larger in comparison to what it would have been if *Case2s* and *Case4s* got added.


So now this value is as large as possible at Case1s and Case3s which indicates a good prediction. If we multiply it by (- 1) , we would make the value as small as possible. This would now intuitively mean, smaller the value, better is the model i.e. smaller the logloss, better is the model i.e. smaller the UNCERTAINTY, better is the model.
This was as simple as I could get.
