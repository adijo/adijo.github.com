---
layout: post
title: Machine Learning - Regression
use_math: true
---

In these series of blog posts, I aim to highlight key points in my study of Machine Learning. I will write about key points that I come across from multiple sources, including the [ISLR book](http://www-bcf.usc.edu/~gareth/ISL/) and the [Machine Learning](https://www.coursera.org/specializations/machine-learning) courses on Coursera by the University of Washington. These will serve as notes for myself and I will be glad if it helps other people as well. These notes only serve as a high level summary of the topics and by no means are comprehensive. These notes are also informal in nature; lacking proper terminology or notation at times. This is done intentionally.


### Introduction

*  Consider the case of predicting an output that depends only on one input, $x.$ There is a *true* function associated with whatever phenomenon we are trying to model. Let this function be $f(x) + \epsilon.$ The $\epsilon$ term is noise which is normally distributed with $ 0 $ mean. 
*  We are trying to build a function $f'(x),$ called the *hypothesis* that *approximates* $f(x).$ 
*  Typically, we *train* a model to minimize the *residual sum of squares,* or $\text{RSS}$ for short. This is just the sum of square of errors accumulated between the actual value and predicted value, $ \sum_{i = 0}^n \left(y - f(x) \right)^2.$ Other measures of fit are the $R^2$ statistic, or the goodness of fit. In short, the $R^2$ statistic tries to explain how much of the variability of $ y $ is explained by the variability in $x.$

### Regression
*  The hypothesis function is linear in the coefficients but non-linear with respect to $x.$ This means that features such as $x^3$ or $x^2$ are allowed. We can simply define a new feature $x_3 = x_2^3 + x_1.$
*  Linear regression can be used to model non-linear relationships by transforming the input space. This is called basis function expansion. What this essentially means is that for each $ x_i $ in our input space, we apply a *transformation* by using what is called a basis function $ \phi(x). $
*  The complexity of a model basically captures its *flexibility,* or *expressive power.* This means that the model can have wild looking curves and capture more data points than a simpler model. For example, a quadratic model can fit more data points than a simple line.
*  As the complexity of a model increases, there are two competing sources of error that arise, the *bias* and the *variance.* These are the two sources of error apart from $ \epsilon, $ which is an *irreducible* error.
*  If we make a very flexible model, consisting of very high order polynomials, our model might become susceptible to overfitting the data. A technique called **regularization** is used to reduce the variance of the model.

*ARTICLE IN PROGRESS*

