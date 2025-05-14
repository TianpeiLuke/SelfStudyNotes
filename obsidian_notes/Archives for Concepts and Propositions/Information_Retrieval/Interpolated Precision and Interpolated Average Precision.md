---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - interpolated_average_precision
  - interpolated_precision
keywords:
  - average_precision
  - interpolated_average_precision
  - interpolated_precision
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Interpolated Precision and Interpolated Average Precision
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: Interpolated Precision and Interpolated Average Precision

![[Precision-Recall Curve#^35ccab]]

- [[Confusion Table]]
- [[Recall and Precision and F-Measure]]
- [[Precision-Recall Curve]]

>[!important] Definition
>The **interpolated precision** $p_{\text{interp}}$ *at a given recall level* $r$ is defined as the *highest precision* found for any recall level $r' \ge r$
>$$
>p_{\text{interp}}(r) = \max_{r' \ge r}\;p(r') 
>$$
>- The justification is that almost anyone would be prepared to look at *a few more documents* if it would increase the *percentage* of the *viewed* set that were *relevant*.
>- on average, *precision decreases* as *recall increases*.

>[!info]
>We can compute the **interpolated precision** at given recall level $r$ by copying the *highest level* of *precision* at *right* hand side of the curve from $r$
>- e.g. the red line is the interpolated function

![[precision_recall_curve.png]]

### $11$-point interpolated average precision

>[!important] Definition
>The **$11$-point interpolated average precision** is defined by the average of *interpolated precisions* at *11 recall level* $r \in (0.0,\, 0.1\,{,}\ldots{,}\,0.9,\, 1.0)$ over a set of queries $q\in Q$
>$$
>\text{11-point interpolated average precision}(r) =  \frac{1}{|Q|} \sum_{q\in Q} p_{\text{interp}}(r; q), 
>$$
>where
>- the precision is measured at $11$ recall levels $r \in (0.0,\, 0.1\,{,}\ldots{,}\,0.9,\, 1.0)$ 
>- For each recall level $r$, we can compute the *arithmetic mean* of the *interpolated precision* over multiple queries.
>- This results in the **interpolated precision-recall plot**

![[precision_recall_curve_avg_precision.png]]

### Mean Average Precision

- [[Mean Average Precision and Average Precision]]


## Explanation

>[!info]
>**Average precision** means average over *multiple queries*.









-----------
##  Recommended Notes


- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Speech and Language Processing by Jurafsky]] pp 296, 298

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [Evaluation 10: recall and precision over ranks](https://www.youtube.com/watch?v=H7oAofuZjjE)
	- 