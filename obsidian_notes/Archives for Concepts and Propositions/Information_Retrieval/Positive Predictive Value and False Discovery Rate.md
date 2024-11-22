---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - statistics/hypothesis_testing
keywords:
  - positive_predictive_value
  - false_discovery_rate
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Positive Predictive Value and False Discovery Rate
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**: Positive Predictive Value and False Discovery Rate

![[Confusion Table#^16427b]]

- [[Confusion Table]]

>[!important] Definition
>Let $C\in \mathbb{R}^{2\times2}$ be the *confusion table*, where
>- $C_{0,0}$ corresponds to the **true negatives (TN)**
>- $C_{1,1}$ corresponds to the **true positives (TP)**
>- $C_{0,1}$ corresponds to the **false positives (FP)**
>- $C_{1,0}$ corresponds to the **false negatives (FN)**  
>  
>Then 
>- the **positive predictive value (PPV)** is given by $$\text{PPV} = \frac{TP}{FP + TP} = \frac{C_{1,1}}{C_{0,1} + C_{1,1}} := \frac{TP}{PP}$$ 
>- the **false discovery rate (FDR)** is given by $$\text{FDR} = \frac{FP}{FP + TP} = \frac{C_{0,1}}{C_{0,1} + C_{1,1}}:= \frac{FP}{PP}$$ 
>- We have the relation $$\text{PPV} = 1 - \text{FDR}.$$

^2c6fb6

- [[True or False Positive Rate and True or False Negative Rate]]
- [[Recall and Precision and F-Measure]]
- [[Sensitivity and Specificity]]


## Explanation










-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp 66

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)