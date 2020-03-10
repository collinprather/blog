---
title: "Logistic Regression and MLE"
toc: true
comments: true
layout: post
description: Explicitly stating Logistic Regression's statistical origins, for those that jumped directly to Ng's ML course.
categories: [statistics]
---

When traditionally using logistic regression to perform binary classification of a dataset, we make predictions, $\hat{y}$ about the class of each data point by

$$\hat{y}=\sigma(w^Tx+b),$$

where $\sigma(z)=\frac{1}{1+e^{-z}}$. We interpret our prediction $\hat{y}$ as the probability that the given data point is from class 1. Mathematically, $\hat{y}=p(y=1\|x)$.

* if $y=1$: $p(y\|x)=\hat{y}$
* if $y=0$: $p(y\|x)=1-\hat{y}$

We can shrink all of this math into a succint one-liner as follows:

$$p(y|x)=\hat{y}^y(1-\hat{y})^{1-y}$$

Since the log function is monotonically increasing, we can be sure that taking the log of each side of this equation holds the equality. Taking the log of each side, we see that,

$$
\begin{aligned}
\log(p(y|x))&= \log(\hat{y}^y(1-\hat{y})^{1-y})\\
&= y\log(\hat{y}) + (1-y)\log(1-\hat{y})
\end{aligned}
$$

If the algebra here was confusing, check out the [exponent rules](https://www.rapidtables.com/math/number/exponent.html). Interestingly, this is precisely the [log loss function](http://wiki.fast.ai/index.php/Log_Loss) that is used in logistic regression.

Under the assumption that our data points are identically, independently distributed (iid), then minimizing the log loss function over the entire data set is equivalent to performing maximum likelihood estimation of the parameters.

$$log\ p(y)=log\prod_{i=1}^{m}p(y^{(i)}|x^{(i)})$$

Since the [log of a product is equal to the sum of logs](https://mathinsight.org/logarithm_basics),

$$
\begin{aligned}
\log\ p(y) &= \sum_{i=1}^{m}\log\ p(y^{(i)}|x^{(i)})\\
&=\sum_{i=1}^{m} y^{(i)}\log(\hat{y}^{(i)}) + (1-y^{(i)})\log(1-\hat{y}^{(i)})&&\text{as shown above}
\end{aligned}
$$

If you are familiar with machine learning, you'll notice that this is the same as the typical logistic regression cost function, which is usually represented as so

$$
\begin{aligned}
	J(w,b)&=-\frac{1}{m}\sum_{i=1}^{m}\left[ y^{(i)}\log(\hat{y}^{(i)} + (1-y^{(i)})\log(1-\hat{y}^{(i)}) \right]
\end{aligned}
$$

Thus, we've shown that using gradient descent to identify the parameters that minimize the cost function is mathematically equivalent to performing a maximum-likelihood estimation of the parameters!
