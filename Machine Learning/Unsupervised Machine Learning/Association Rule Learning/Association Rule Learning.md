---
aliases:
  - Association Rule Mining
---
It is a common technique used to discover associations in [Unsupervised Machine Learning](../Unsupervised%20Machine%20Learning.md). This technique is a rule-based ML technique that finds out some very useful relations between parameters of a large dataset. This technique is basically used for market basket analysis that helps to better understand relationship between different products. 

For E.g:
Shopping Stores use algorithms based on this technique to find out the relationship between the sale of one product w.r.t to another's sales based on customer behavior. Like if a customer buys milk, then he may also buy break, eggs, or butter.

### Types of Association Rule Learning Algorithms
- [Apriori Algorithm](Apriori%20Algorithm.md) :- Finds patterns by exploring frequent item combinations step-by-step.
- [FP-Growth Algorithm](FP-Growth%20Algorithm.md) :- An Efficient Alternative to [Apriori Algorithm](Apriori%20Algorithm.md). It quickly identifies frequent patterns without generating candidate sets.
- [Eclat Algorithm](Eclat%20Algorithm.md) :- Uses intersections of itemsets to efficiently find frequent patterns. 
- [Efficient Tree-Based Algorithms](Efficient%20Tree-Based%20Algorithms.md) :- Scales to handle large datasets by organizing data in tree structures.