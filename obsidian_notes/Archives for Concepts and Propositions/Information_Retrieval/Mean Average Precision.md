---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - mean_average_precision
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Mean Average Precision
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: Mean Average Precision or MAP

>[!important] Definition
>Let $Q$ be a set of *queries*. 
>- The set of *relevant documents* for given query $q_{j}\in Q$ is $$\left\{ d_{1}\,{,}\ldots{,}\,d_{m_{j}} \right\}$$ and 
>- Let $R_{j,k}$ be the set of *ranked retrieved documents* for the query $q_{j}$ from top *until* the document $d_{k}$. $$(s_{1} \,{,}\ldots{,}\,s_{R_{j,k}}\,, d_{k})$$
>	- $|R_{j,k}|$ is the **rank** of the *relevant* document $d_{k}$ in the *ordered retrieved list* from query $q_{j}$.
>
>Then the **mean average precision (MAP)** for the *query set* $Q$ is defined as 
>$$
>\text{MAP}(Q) := \frac{1}{|Q|}\sum_{j=1}^{|Q|}\, \frac{1}{m_{j}}\sum_{k=1}^{m_{j}}\text{Precision}(R_{j,k}) 
>$$
>- If $Q = \left\{ q \right\}$ is a single query, then the **mean average precision** is the *average of precision* for the set of top $k$ documents until and then it is *averaged* over *queries*
>- The MAP value for a test collection is the *arithmetic mean* of *average precision values* for individual query.
>- If a given document $d_{k}$ is *not retrieved at all* $R_{j,k} = \infty$, then the *precision value* is *zero*.

- [[Confusion Table]]
- [[Recall and Precision and F-Measure]]

## Explanation

>[!info]
>The **average precision** $$\text{Average Precision}(q_{j}) := \frac{1}{m_{j}}\sum_{k=1}^{m_{j}}\text{Precision}(R_{j,k}) $$ is defined as the average over the *relevant documents* $d_{k}$ for *given query*
>- the **average precision** is the *sum* over the **ranks** of *relevant documents* in retrieved list.
>
>The **mean average precision** is the average over *different queries* $$\text{Mean Average Precision}(Q) = \frac{1}{|Q|}\sum_{j=1}^{|Q|}\text{Average Precision}(q_{j})$$


>[!info]
>- **Precision** is measured for given threshold
>- **MAP** is measured for a **ranked list** of *retrieved results*.

>[!info]
>To compute the **average precision** for a given query:
>- *rank* the retrieved documents
>- compute the *precision* and *recall* for each retrieved document from *top* to *down*
>	- $$\text{Precision}_{i},\; \text{Recall}_{i}$$
>	- check [[Precision-Recall Curve#Approximate Precision-Recall Curve via Binning]]
>- *save* precision value when the given retrieved document is *relevant* 
>- take *average* of *saved precision values*  $$\text{Avg. Precision} = \frac{1}{|m_{j}|}\sum_{k=1}^{m_{j}}\text{Precision}_{k}$$
>  
>Then the **mean average precision** is average over all queries.  



>[!info]
>For a single query, 
>- the **average precision** approximates the **area under the uninterpolated precision-recall curve (AUPRC)**, 
>- and so the **MAP** is roughly the **average** *area under the precision-recall curve* for a set of queries.

- [[Precision-Recall Curve]]

>[!info]
>Using **MAP**, *fixed* recall levels are **not chosen**, and there is **no interpolation**.

- [[Interpolated Precision and Interpolated Average Precision]]

>[!quote]
>Calculated MAP scores normally *vary widely* across *information needs* when measured within *a single system*, for instance, between $0.1$ and $0.7.$ 
>- Indeed, there is normally more agreement in MAP for an *individual* information need *across systems* than for *MAP scores* for different information needs for the *same system*. 
>- This means that a set of test information needs must be *large and diverse* enough to be representative of system effectiveness across different queries.
>  
>-- [[Introduction to Information Retrieval by Manning]] pp 161  

## MAP vs. NDCG

![[Normalized Discounted Cumulative Gain or NDCG#^f0ab9e]]

- [[Normalized Discounted Cumulative Gain or NDCG]]




-----------
##  Recommended Notes


- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Speech and Language Processing by Jurafsky]] pp 297 - 298

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [Evaluation 12: mean average precision](https://www.youtube.com/watch?v=pM6DJ0ZZee0)