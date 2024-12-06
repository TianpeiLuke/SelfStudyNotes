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
>Then the **normalized discounted cumulative gain (NDCG)** of document $d$ at top $k$ queries is defined as 
>$$
>\text{NDCG}(Q, k) = \frac{1}{|Q|}\sum_{j=1}^{|Q|}Z_{k,j}\;\sum_{m=1}^{k}\; \frac{2^{R(j,m)} - 1}{\log_{2}(1+m)}
>$$
>where
>- $Z_{k,j}$ is a *normalization factor* so that a perfect ranking's NDCG *at $k$* for query $j$ is $1$; i.e. $$Z_{k,j} := \left(\sum_{m=1}^{k}\; \frac{2^{R^{*}(j,m)} - 1}{\log_{2}(1+m)}\right)^{-1}$$
>- For queries for which $k' < k$ documents retrieved, the last summation is done up to $k'$.
>- $$\log(1+m)$$ is the *penalty* for the *high ranking* (rank $m$) of *relevant document*.


- [[Recall and Precision and F-Measure]]
- [[Recall and Precision at k]]
- [[Positive Predictive Value and False Discovery Rate]]
- [[True or False Positive Rate and True or False Negative Rate]]
- [[Confusion Table]]

![[ndcg_example.png]]


## Explanation

>[!important] Definition
>The **discounted cumulative gain (DCG)** is given by 
>$$\text{DCG}_{j} := \sum_{m=1}^{k}\; \frac{2^{R(j,m)} - 1}{\log_{2}(1+m)} $$
>

>[!info]
>We can define the *relevance score* based on **ranking** of relevant document $d$.
>
>e.g. $$R(j,m) = \left\{\begin{array}{cl} 1 & \text{if m-th ranked document  in relevant for } q_{j} \\[5pt] 0 & \text{otherwise} \end{array} \right. $$ thus the numerator is $1$ if $d_{m}$ appears in the *top-k* retrieved documents for query $q_{j}$

>[!info]
>**NDCG** is mainly used in **relevance feedback** with **non-binary feedbacks**.

- [[Relevance Feedback for Information Retrieval]]

## Compared with MAP

- [[Mean Average Precision]]

>[!info]
>The **average precision** is the *sum* over **ranks** of **relevant documents**
>- Assume the *best possible ranking* with top $k$ being all relevant
>$$
>\begin{align*}
>\text{Average Precision}_{m} &:= \frac{1}{m}\sum_{k=1}^{m}\text{Precision}(R_{j,k}) \\[5pt] 
>&= \frac{1}{m}\sum_{k=1}^{m} \frac{1}{|R_{j,k}| }\sum_{i=1}^{|R_{j,k}|}R(j,i) \\[5pt] 
>&= \frac{1}{m}\sum_{k=1}^{m} \frac{1}{k}\sum_{i=1}^{k}R(j,i) \\[5pt]
>&= \frac{1}{m}\sum_{i=1}^{m}R(j,i) \sum_{k=i}^{m}\frac{1}{k} \\[5pt] 
>&\to \frac{1}{m}\sum_{i=1}^{m}R(j,i) \int_{i}^{m} \frac{1}{x}dx  \\[5pt] 
>&= \frac{1}{m}\sum_{i=1}^{m}R(j,i)  \log \left( \frac{m}{i} \right)
>\end{align*}
>$$ 
>where $R_{j,k}$ be the set of *ranked retrieved documents* for the query $q_{j}$ from top *until* the document $d_{k}$
>- For best possible ranking $|R_{j,k}| = k$
>
>The **discounted cumulative gain** is given by $$\text{DCG}_{m} := \sum_{i=1}^{m}R(j,i) \frac{1}{\log(i + 1)}$$ 

^f0ab9e




-----------
##  Recommended Notes

- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 162 - 163
- [[Evaluating Learning Algorithms by Japkowicz]]

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [Evaluation 13: MAP vs NDCG](https://www.youtube.com/watch?v=qm1In7NH8WE)