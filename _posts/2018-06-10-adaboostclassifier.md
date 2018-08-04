---
title: "The beginning of boosting: AdaBoost"
date: 2018-04-05
tags: [Predictive Analytics]
excerpt: "Machine Learning, predictive models, boosting, ensemble learning, classification"
author_profile: false
---
# AdaBoost.M1

Boosting is one of the most powerful ideas introduced in the last twenty years. It was originally designed for classification
problems but can be extended to regression problems as well. It is a method where multiple models are created using a logic
and then combined together to get a prediction which is better than what we could have got using a single strong model.

With respect to the idea of combining multiple models together it is similar to bagging but the way in which boosting
comes up with multiple models is totally different from the way things are done in bagging.

To understand the concept of boosting **intuitively**, we will consider one of the earliest and important boosting algorithm called as **"AdaBoost.M1"** or **"Discrete AdaBoost"**. To understand this algorithm we set a context where our response variable $$Y$$ has two classes $${-1, 1}$$. Note that by making a few changes, AdaBoost can
be extended to a continuous response or a multiclass response as well but for now we will stick to the $${-1, 1}$$ response.

Following is the pseudo code of **AdaBoost.M1** algorithm. We will disect and look at each and every step in detail after that.

![AdaBoost PseudoCode](/images/adaboostm1.png)

## To simplify things a bit, the algorithm:

1. Takes in the following parameters: $$M$$ Total number of iterations/runs of a classifier (Let us stick to decision trees for now so $$M$$ decision trees) & a training data of $$N$$ training samples.
2. Starts off with weighting equally, each of the $$Nth$$ training example by weight $$\frac{1}{N}$$
3. Comes up with the first decision tree $$G_{1}(x)$$ that minimizes a weighted error function given by $$err_{1} = \frac{\sum_{i=1}^{N} (w_{i} \hspace{0.2cm}  I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{1}(x_{i})))}{\sum_{i=1}^{N} w_{i}}$$
4. Calculates an update parameter $$\alpha_{1}$$ for the first tree using $$\log_{}[\frac{1-err_{1}}{err_{1}}]$$ and more generally at each $$ m = 1,2,...,M $$   $$\alpha_{m}$$ is calculated using $$\log_{}[\frac{1-err_{m}}{err_{m}}]$$
5. $$\alpha_{1}$$ updates the weights (i.e. we do what we were doing in Step 2) and the process continues by executing Step 3, 4 and 5.

The above mechanism raises two important questions. Why are the weights assigned to the training examples? And What is the use of $$\alpha_{m}$$??

The answers to these two questions are the key to understanding how and why boosting works.

## 1. Why assign weights to training examples?

Lets look at the first question about the weights. At first, the training samples are weighted, then a tree is fit using the weighted error function. After that, while fitting subsequent trees **$$\alpha_{m}$$ does the job of *reducing/not increasing* the weights of those training examples which were *correctly classified* by the current tree $$G_{m}(x)$$ and *increasing* the weights of those which were *misclassified***. (Do not worry if you don't understand how $$\alpha_{m}$$ updates the weights. We will look at that shortly but just keep in mind at a high level what $$\alpha_{m}$$ does to the weights according to correct classification)

To illustrate why this weight updation works: Once $$G_{1}(x)$$ is fit, we will have $$\alpha_{1}$$ which will update the weights for $$G_{2}(x)$$ accordingly. Now consider the fitting of the next tree $$G_{2}(x)$$. We know that decision tree algorithms choose that feature and that value of the feature which minimizes the error at each split. Our error function is $$err_{1} = \frac{\sum_{i=1}^{N} (w_{i}   I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})))}{\sum_{i=1}^{N} w_{i}}$$. Note the indicator variable $$I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i}))$$. Since we have this indicator in the error function, we can see that the decision tree will try to pick the features for the splits which *correctly classify the highly weighted observations (misclassified by the previous tree)* since if these observations were misclassified again then the indicator variable will take the value of $$1$$ and the high weight $$w_{i}$$ will be considered in the evaluation of error. So the decision tree will be forced to prioritize the previously misclassified examples because if it does not, then the weighted error would cease to come down and converge to a minima. Its like manipulating an algorithm to focus on previous misclassified/ highly weighted examples by including the weights in the loss function. This is why weights are assigned to each training example and are accomodated in the error.

**So higher the weight of a particular training sample, more the chance of the algorithm finding the right criteria to correctly classify it.**

## 2. What is the use of $$\alpha_{m}$$?

The second important question is, how does $$\alpha_{m}$$ increase the weights of training example misclassified by a classifier $$G_{m}(x)$$ and decrease the weights of correctly classified training examples? Let us look at this by looking at a few cases.

***Case 1***


**Error of $$G_{m}(x)$$ is high**

This means $$err_{m}$$ is high. Lets assume error is 0.9. Then $$\alpha_{m} = \log_{}[\frac{1-err_{m}}{err_{m}}] = \log_{}[\frac{1-0.9}{0.9}] = -0.95424$$

As we can see $$\alpha_{m}$$ turned out to be low. **$$\alpha_{m}$$ is inversely proportional to $$err_{m}$$**

Now let us consider weight updation for the sub-cases of correctly-classified/mis-classified training examples. The formula for weight updation for **any** training example is $$w^{\prime}_{i} = w_{i} * [ \exp(\alpha_{m} * I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})) ] $$.

***Case 1.A***

**Weights of Examples correctly-classified by $$G_{m}(x)$$**

For rightly classified examples, the indicator variable is zero. This implies the exponent term in the weight updation becomes 1 ($$\exp(0) = 1$$). This implies updated weight $$w^{\prime}_{i} = w_{i}$$ i.e. no change.

***Case 1.B***

**Weights of Examples mis-classified by $$G_{m}(x)$$**

For mis-classified examples, the indicator variable is 1. This implies the exponent term in the weight updation becomes
$$\exp(\alpha_{m} * 1) = \exp(-0.95424 * 1) = 1.76404$$. And therefore, $$w^{\prime}_{i} = w_{i} * [ \exp(\alpha_{m} * I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})) ] = w_{i} * 1.76404 > w_{i}  $$

Hence, when error is high, alpha is low and the weights of mis-classified samples are increased for the next iteration of the classifier which means that next classifier will be forced to prioritize the classification of the mis-classified samples.

This is how the combination Error, Alpha and Weights is used to create iteratively better learners.


***Case 2***


**Error of $$G_{m}(x)$$ is low**

This means $$err_{m}$$ is low. Lets assume error is 0.1. Then $$\alpha_{m} = \log_{}[\frac{1-err_{m}}{err_{m}}] = \log_{}[\frac{1-0.1}{0.1}] = +0.95424$$

As we can see $$\alpha_{m}$$ turned out to be high. **$$\alpha_{m}$$ is inversely proportional to $$err_{m}$$**

Now let us consider weight updation for the sub-cases of correctly-classified/mis-classified training examples. The formula for weight updation for **any** training example is $$w^{\prime}_{i} = w_{i} * [ \exp(\alpha_{m} * I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})) ] $$.

***Case 2.A***

**Weights of Examples correctly-classified by $$G_{m}(x)$$**

For rightly classified examples, the indicator variable is zero. This implies the exponent term in the weight updation becomes 1 ($$\exp(0) = 1$$). This implies updated weight $$w^{\prime}_{i} = w_{i}$$ i.e. no change.

***Case 2.B***

**Weights of Examples mis-classified by $$G_{m}(x)$$**

For mis-classified examples, the indicator variable is 1. This implies the exponent term in the weight updation becomes
$$\exp(\alpha_{m} * 1) = \exp(+0.95424 * 1) = 2.59669$$. And therefore, $$w^{\prime}_{i} = w_{i} * [ \exp(\alpha_{m} * I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})) ] = w_{i} * 2.59669 > w_{i}  $$


## Summary

So this is how the Boosting works in essence. Examples are weighted according to their correct classification and weights are updated at each iteration.
