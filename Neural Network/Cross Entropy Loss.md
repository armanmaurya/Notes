---
tags:
  - AI
aliases:
  - logistic loss
  - log loss
---
In [Machine Learning](../Machine%20Learning/Machine%20Learning.md) for classification task, the model predicts the probability of a sample belonging to a particular class. Since each sample can belong to only a particular class, the probability value would be 1 for that particular class and 0 for the other classes. Cross entropy measures the difference between the predicted probability and the true probability.

The Cross-Entropy Loss is derived from the principle of maximum likelihood estimation when applied to the task of classification. Maximizing the likelihood is equivalent to minimizing the negative log-likelihood. In classification, the likelihood function can be expressed as the product of the probabilities of the  correct classes.