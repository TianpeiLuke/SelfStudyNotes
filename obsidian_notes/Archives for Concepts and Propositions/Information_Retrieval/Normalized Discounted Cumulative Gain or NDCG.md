---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - cumulative_gain
  - normalized_discounted_cumulative_gain
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Cumulative Gain and Normalized Discounted Cumulative Gain
date of note: 2024-01-25
---
## Concept Definition

>[!important]
>**Name**: Normalized Discounted Cumulative Gain or NDCG

>[!important] Definition
>Let $Q$ be a set of queries $Q := \{q_{1}\,{,}\ldots{,}\, q_{|Q|} \}$. 
>
>Define $R(j,d)$ be the *relevance score* of document $d$ for query $q_{j}$. 
>
>Then **normalized discounted cumulative gain (NDCG)** of document $d$ at top $k$ queries is defined as 
>$$
>\text{NDCG}(Q, k) = \frac{1}{|Q|}\sum_{j=1}^{|Q|}Z_{k,j}\;\sum_{m=1}^{k}\; \frac{2^{R(j,m)} - 1}{\log_{2}(1+m)}
>$$
>where
>- $Z_{k,j}$ is a *normalization factor* so that a perfect ranking's NDCG *at $k$* for query $j$ is $1$; i.e. $$Z_{k,j} := \left(\sum_{m=1}^{k}\; \frac{2^{R^{*}(j,m)} - 1}{\log_{2}(1+m)}\right)^{-1}$$
>- For queries for which $k' < k$ documents retrieved, the last summation is done up to $k'$.


- [[Recall and Precision and F-Measure]]
- [[Recall and Precision at k]]
- [[Positive Predictive Value and False Discovery Rate]]
- [[True or False Positive Rate and True or False Negative Rate]]
- [[Confusion Table]]

## Explanation










-----------
##  Recommended Notes

- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 162 - 163
- [[Evaluating Learning Algorithms by Japkowicz]]

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)