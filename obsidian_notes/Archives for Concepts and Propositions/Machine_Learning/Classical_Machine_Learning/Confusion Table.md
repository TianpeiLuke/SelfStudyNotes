---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - statistics/hypothesis_testing
keywords:
  - confusion_table_metric
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Confusion Table
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**: Confusion Table

>[!important] Definition
>In **predictive analysis**, the **confusion table** or **confusion matrix** or **error matrix** is described as a $2\times 2$ matrix 
>$$
>C \in \mathbb{R}^{2\times 2}
>$$
>where 
>- the *row* corresponds to the instances in an *actual class*
>- the *column* corresponds to the instances in an *predicted class*
>- The *diagonal* of the matrix therefore represents all instances that are *correctly predicted*.
>
>|                   | **predicted** negative | **predicted** positive |
>| ----------------- | ---------------------- | ---------------------- |
>| **actual** negative | $C_{0,0}$              | $C_{0,1}$              |
>| **actual** positive | $C_{1,0}$              | $C_{1,1}$              |
>
>- $C_{0,0}$ corresponds to the **true negatives (TN)**
>- $C_{1,1}$ corresponds to the **true positives (TP)**
>- $C_{0,1}$ corresponds to the **false positives (FP)**
>- $C_{1,0}$ corresponds to the **false negatives (FN)**  
>- The **predicted positives (PP)** is given by the column sum $$\text{PP} := C_{:,1} := C_{0,1} + C_{1,1}$$
>- The **predicted negatives (PN)** is given by the column sum $$\text{PN} :=  C_{:,0} := C_{0,0} + C_{1,0}$$
>- The **actual positive** or **positive (P)** is given by the row sum $$\text{P} := C_{1,:} := C_{1,0} + C_{1,1}$$
>- The **actual negative** or **negative (N)** is given by the row sum $$\text{N} := C_{0,:} := C_{0,0} + C_{0,1}$$

^16427b

- [[Classification Problem]]

### True Positive Rate, False Positive Rate, True Negative Rate, False Negative Rate

![[True or False Positive Rate and True or False Negative Rate#^1ea887]]

- [[True or False Positive Rate and True or False Negative Rate]]

### Positive Predictive Value and False Discovery Rate

![[Positive Predictive Value and False Discovery Rate#^2c6fb6]]

- [[Positive Predictive Value and False Discovery Rate]]


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

- [[Information Retrieval]]

## Multiclass Case

>[!important] Definition
>In **$K$-class case**, the **confusion table** or **confusion matrix** or **error matrix** is described as a $K\times K$ matrix 
>$$
>C \in \mathbb{R}^{K\times K}
>$$
>where 
>- the *row* corresponds to the instances in an *actual class*
>- the *column* corresponds to the instances in an *predicted class*
>- The *diagonal* of the matrix therefore represents all instances that are *correctly predicted*.
>
>|                   | **predicted** class $0$ | **predicted** class $1$  | $\dots$ |  **predicted** class $K-1$  |
>| ----------------- | ---------------------- | ---------------------- | --------------------- | --------------------- |
>| **actual** class $0$ | $C_{0,0}$              | $C_{0,1}$              | $\dots$ | $C_{0,K-1}$              |
>| **actual** class $1$ | $C_{1,0}$              | $C_{1,1}$               | $\dots$ | $C_{0,K-1}$              |
>| $\dots$ |  $\dots$           | $\dots$              | $\dots$ |  $\dots$              |
>| **actual** class $K-1$ | $C_{K-1,0}$              | $C_{K-1,1}$              | $...$ | $C_{K-1,K-1}$              |
>
>- $C_{i,i}$ corresponds to the **true positives (TP)** for *class* $i$
>- $C_{-i,i}$ corresponds to the **false positives (FP)** for class $i$ i.e. $$C_{-i,i} = \sum_{j\neq i}C_{j,i}$$
>- $C_{i,-i}$ corresponds to the **false negative (FN)** for *class* $i$ i.e. $$C_{i,-i} = \sum_{j\neq i}C_{i,j}$$

^69bf3c

- [[Macro-Average and Micro-Average for Multi-Class Metric]]





-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]] pp 155
- [[Speech and Language Processing by Jurafsky]] pp 66
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 147
- [[Elements of Statistical Learning by Hastie]]


- Wikipedia [Confusion_matrix](https://en.wikipedia.org/wiki/Confusion_matrix)

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)