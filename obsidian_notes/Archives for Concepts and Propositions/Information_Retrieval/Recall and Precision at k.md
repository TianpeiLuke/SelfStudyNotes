---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - recall_at_k
  - precision_at_k
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Recall and Precision at k
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**:  Recall and Precision at k

![[Recall and Precision and F-Measure#^6fe4b0]]

>[!important] Definition
>Let $$(d_{1}\,{,}\ldots{,}\,d_{m})$$ be *top $m$ retrieved result* for query $q$, *ranked* according to predicted relevancy. 
>
>The **precision at $k$** or **precision@k** is defined as the *precision* at *fixed* low levels of retrieved results
>$$
>\text{Precision@k} = \frac{1}{k}\#\{ d_{i}: d_{i}\text{ is relevant to query }q,\, 1 \le i\le k \}
>$$


- [[Precision-Recall Curve]]
- [[Recall and Precision and F-Measure]]
- [[Confusion Table]]

## Explanation

>[!quote]
>- It has the **advantage** of *not* requiring any estimate of the *size* of the *set of relevant documents* 
>- but the **disadvantages** that it is the *least stable* of the commonly used evaluation measures and that it does *not average* well, 
>	- since the *total number* of *relevant documents* for a query has a **strong influence** on precision at $k$.
>	  
>-- [[Introduction to Information Retrieval by Manning]] pp 161	  

- [[R-Precision]]






-----------
##  Recommended Notes

- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 161
- [[Evaluating Learning Algorithms by Japkowicz]]

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [Evaluation 10: recall and precision over ranks](https://www.youtube.com/watch?v=H7oAofuZjjE)