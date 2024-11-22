---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - statistics/hypothesis_testing
keywords:
  - true_postive_rate
  - true_negative_rate
  - false_positive_rate
  - false_negative_rate
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: True or False Positive Rate and True or False Negative Rate
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**: True or False Positive Rate and True or False Negative Rate

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
>- the **true negative rate (TNR)** is given by $$\text{TNR} = \frac{TN}{TN + FP} = \frac{C_{0,0}}{C_{0,0} + C_{0,1}} := \frac{TN}{N}$$ 
>- the **true positive rate (TPR)** is given by $$\text{TPR} = \frac{TP}{TP + FN} = \frac{C_{1,1}}{C_{1,1} + C_{1,0}} := \frac{TP}{P} $$ 
>- the **false negative rate (FNR)** is given by $$\text{FNR} = \frac{FN}{TP + FN} = \frac{C_{1,0}}{C_{1,1} + C_{1,0}} := \frac{FN}{P}$$ 
>- the **false positive rate (TPR)** is given by $$\text{FPR} = \frac{FP}{TN + FP} = \frac{C_{0,1}}{C_{0,0} + C_{0,1}} := \frac{FP}{N}$$ 
>
>The following equation holds by definition
>- $$\text{FNR} = 1 - \text{TPR}$$ 
>- $$\text{FPR} = 1 - \text{TNR}$$

^1ea887

### Type-I Error and Type-II Error

![[Hypothesis Testing Problem#^1194ca]]

- [[Hypothesis Testing Problem]]

>[!important]
>For binary prediction,
>- **Type-I Error** is equal to the **false positive rate**.
>- **Type-II Error** is equal to the **false negative rate.**

### Precision Recall

>[!important]
>For binary prediction,
>- the **recall** is equal to the **true positive rate.**
>- the **precision** is equal to the **positive predictive value.**

- [[Recall and Precision and F-Measure]]

### Receiver Characteristic Curve for Binary Classification

- [[Receiver Characteristic Curve for Binary Classification]]

## Explanation

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
>








-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]]
- [[Speech and Language Processing by Jurafsky]] pp 66

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)