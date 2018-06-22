---
title: "The beginning of boosting: AdaBoost"
date: 2018-04-05
tags: [Predictive Analytics]
excerpt: "Machine Learning, predictive models, boosting, ensemble learning, classification"
---

## Intuitive explaination of AdaBoost

Boosting is one of the most powerful ideas introduced in the last twenty years. It was originally designed for classification
problems but can be extended to regression problems as well. It is a method where multiple models are created using a logic
and then combined together to get a prediction which is better than what we could have got using a single strong model.

With respect to the idea of combining multiple models together it is similar to bagging but the way in which boosting
comes up with multiple models is totally different from the way things are done in bagging.

To understand the concept of boosting **intuitively**, we will consider one of the earliest and important boosting algorithm called as **"AdaBoost.M1"** or **"Discrete AdaBoost"**. To understand this algorithm we set a context where our response variable $$Y$$ has two classes $${-1, 1}$$. Note that by making a few changes, AdaBoost can
be extended to a continuous response or a multiclass response as well but for now we will stick to the $${-1, 1}$$ response.

Following is the pseudo code of **AdaBoost.M1** algorithm. We will disect and look at each and every step in detail after that.

![AdaBoost PseudoCode](/images/adaboostm1.png)

## The initial Pseudo Code steps with a human touch

1. Takes in the following parameters: $$M$$ Total number of iterations/runs of a classifier. Let us stick to decision trees for now so $$M$$ decision trees & a training data of $$N$$ training samples.
2. Starts off with weighting equally, each of the $$N$$ training example by weight $$\frac{1}{N}$$
3. Comes up with the first decision tree $$G_{1}(x)$$ that minimizes a weighted error function given by $$err_{1} = \frac{\sum_{i=1}^{N} (w_{i} \hspace{0.2cm}  I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{1}(x_{i})))}{\sum_{i=1}^{N} w_{i}}$$
4. Calculates an update parameter $$\alpha_{1}$$ for the first tree using $$\log_{}[\frac{1-err_{1}}{err_{1}}]$$ and more generally at each $$ m = 1,2,...,M $$   $$\alpha_{m}$$ is calculated using $$\log_{}[\frac{1-err_{m}}{err_{m}}]$$

The answers to the following two questions are the key to understanding how and why boosting works

## 1. Why assign weights to training examples?

Lets look at the first question about the weights. At first, the training samples are weighted, then a tree is fit using the weighted error function. After that, while fitting subsequent trees **$$\alpha_{m}$$ does the job of *reducing* the weights of those training examples which were correctly classified by the previous tree $$G_{m-1}(x)$$ and *increasing* the weights of those which were misclassified**. So once $$G_{1}(x)$$ is fit, we will have $$\alpha_{2}$$ which will update the weights accordingly. Now consider the fitting of the next tree i.e. $$G_{2}(x)$$. We know that decision tree algorithms choose that feature and that value of the feature which minimizes the error at each split. Our error function is $$err_{1} = \frac{\sum_{i=1}^{N} (w_{i}   I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})))}{\sum_{i=1}^{N} w_{i}}$$. Note the indicator variable $$I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i}))$$. Since we have this indicator in the error function, we can see that the decision tree will try to pick the features for the splits which *correctly classify the highly weighted observations* since if these observations were misclassified then the indicator vaiable will take the value of $$1$$ and the high value $$w_{i}$$ will be considered in the evaluation of error. So the decision tree will be forced to prioritize the previously misclassified examples. This is why weights are assigned to each training example and are accomodated in the error.

**So higher the weight of a particular training sample, more the chance of the algorithm finding the right criteria to correctly classify it.**

## 2. What is the use of $$\alpha_{m}$$?

The second important question is, how does $$\alpha_{m}$$ increase the weights of example misclassified in the previous run of the classifier i.e. $$G_{m-1}(x)$$ and increase the weights of correctly classified samples? Let us look at this by look at a few cases.

***Case 1***


**Error of $$G_{m}(x)$$ is high**

This means $$err_{m}$$ is high. Lets assume error is 0.9. Then $$\alpha_{m} = \log_{}[\frac{1-err_{m}}{err_{m}}] = \log_{}[\frac{1-0.9}{0.9}] = -0.95424$$

As we can see $$\alpha_{m}$$ turned out to be low. **$$\alpha_{m}$$ is inversely proportional to $$err_{m}$$**

Now let us consider a sub-case. The formula for weight updation for any training example is $$w_{i} * [ \exp(\alpha_{m} * I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})) ] $$.

***Case 1.A***

**Weights of Examples rightly classified by $$G_{m}(x)$$**

For rightly classified examples, the indicator variable is zero. This implies the exponent term in the weight updation becomes 1 ($$\exp(0) = 1$$). This implies updated weight $$w^{\prime}_{i} = w_{i}$$ i.e. no change.

***Case 1.B***

**Weights of Examples rightly classified by $$G_{m}(x)$$**

For rightly classified examples, the indicator variable is zero. This implies the exponent term in the weight updation becomes 1 ($$\exp(0) = 1$$). This implies updated weight $$w^{\prime}_{i} = w_{i}$$ i.e. no change.




So as we can see in **Step 1**, each and every training sample is assigned a weight equal to $$\frac{1}{N}$$ where $$N$$ equals the total number of training samples. The idea behind assigning weights is to force the classifier

is this - We will start with equal weight for every training sample, fit a classifier and update the weights in such a way that the misclassified samples will have higher weights and the correctly classified samples would have lower weights than what they previously had. Lets go over each step to understand this. In **Step 2(a)** we will fit a classifier $$G_{1}(x)$$ to the data using the error function $$err_{1} = \frac{\sum_{i=1}^{N} (w_{i}   I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm}  G_{m}(x_{i})))}{\sum_{i=1}^{N} w_{i}}$$ i.e. we will find a classifier which has the minimum error $$err_1$$. Now since each $$w_{i}$$ is equal, whenever there is a misclassification i.e. whenever $$I(y_{i}\hspace{0.2cm}\neq\hspace{0.2cm} G_{m}(x_{i})) = 1 $$ it will be multiplied by the same quantity $$w_{i}\hspace{0.2cm} for\hspace{0.2cm} all\hspace{0.2cm} i = 1,2,....,N$$. So each training sample, be it misclassified or correctly classified by $$G_{1}(x)$$ would contributed equally to the error in the first iteration. Now while fitting the second classifier, if we somehow increased the weights for misclassified samples and decreased them for correctly classified samples note that
