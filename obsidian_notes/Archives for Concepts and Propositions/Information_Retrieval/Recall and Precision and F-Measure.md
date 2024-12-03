---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - recall_metric
  - precision_metric
  - f_measure_metric
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Recall and Precision and F-Measure
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: Recall and Precision and F-Measure

![[Confusion Table#^16427b]]

>[!important] Definition
>Let $C\in \mathbb{R}^{2\times2}$ be the *confusion table*, where
>- $C_{0,0}$ corresponds to the **true negatives (TN)**
>- $C_{1,1}$ corresponds to the **true positives (TP)**
>- $C_{0,1}$ corresponds to the **false positives (FP)**
>- $C_{1,0}$ corresponds to the **false negatives (FN)**  
>  
>Then 
>- the **recall** is given by $$\text{Recall} = \frac{TP}{TP + FN} = \frac{C_{1,1}}{C_{1,1} + C_{1,0}} := \frac{TP}{P} $$ 
>- the **precision** is given by $$\text{Precision} = \frac{TP}{TP + FP} = \frac{C_{1,1}}{C_{1,1} + C_{0,1}} := \frac{TP}{PP}$$ 
>- the **F-measure** is given by the *weighted harmonic mean* of *precision* and *recall* $$F_{\beta} := \frac{(\beta^2 + 1)\;\text{Precision}\,\text{Recall}}{\beta^2\,\text{Precision} + \text{Recall}} = \frac{1}{\alpha^{1/\text{Precision}} + (1-\alpha)^{1/\text{Recall}}}$$
>	- where $$\beta^2 = \frac{1- \alpha}{\alpha}$$
>	- It is common to choose $\beta=1$,  $$\text{F-measure} := F_{1} := \frac{2\;\text{Precision}\,\text{Recall}}{\text{Precision} + \text{Recall}}$$

^6fe4b0

>[!important] Definition
>In **information retrieval**, the meaning of confusion table is different
>- the *row* corresponds to the **relevancy** of instance
>- the *column* corresponds to the **retrieved decision** by the system
>- The *diagonal* of the matrix therefore represents all instances that are *correctly retrieved or not retreived*.
>
>|                   | **not retrieved**  | **retrieved**  |
>| ----------------- | ---------------------- | ---------------------- |
>| **non-relevant**  | $C_{0,0}$              | $C_{0,1}$              |
>| **relevant**  | $C_{1,0}$              | $C_{1,1}$              |
>
>Then 
>- the **recall** is given by $$\text{Recall} = \frac{\#(\text{relevant item retrieved})}{\#(\text{relevant item})}$$ 
>- the **precision** is given by $$\text{Precision} = \frac{\#(\text{relevant item retrieved})}{\#(\text{retrieved item})}$$ 

- [[Information Retrieval]]

### Binary Decision

>[!important]
>For binary prediction,
>- the **recall** is equal to the **true positive rate.**
>- the **precision** is equal to the **positive predictive value**.

- [[Confusion Table]]
- [[True or False Positive Rate and True or False Negative Rate]]
- [[Positive Predictive Value and False Discovery Rate]]


### Average Precision

- [[Interpolated Precision and Average Precision]]


### Top-K Relevance

- [[Recall and Precision at k]]


## Explanation

>[!info]
>In **information retrieval**, 
>- the **true positive** corresponds to the **relevant**
>- the **predicted negative** corresponds to the **non-relevant**
>- 

- [[Information Retrieval]]

>[!info]
>Both *precision, recall and F-measure* are for **unordered set**.
>
>If we want to evaluate **ordered set**, we would need to use other metrics

- [[Recall and Precision at k]]
- [[Interpolated Precision and Average Precision]]
- [[Normalized Discounted Cumulative Gain or NDCG]]


## Precision-Recall Curve

>[!important] Definition
>The **precision-recall curve** has
>- $x$-axis as *recall*
>- and $y$-axis as *precision*.

- [[Precision-Recall Curve]]


-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]] pp 154 - 156
- [[Speech and Language Processing by Jurafsky]] pp 66
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Artificial Intelligence Modern Approach by Russell]] pp 869

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)