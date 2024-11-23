---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - statistics/hypothesis_testing
keywords:
  - macro_average
  - micro_average
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Macro-Average and Micro-Average for Multi-Class Metric
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**: Macro-Average and Micro-Average for Multi-Class Metric

![[Confusion Table#^69bf3c]]

- [[Confusion Table]]

![[Recall and Precision and F-Measure#^6fe4b0]]

- [[Recall and Precision and F-Measure]]

>[!important] Definition
>Consider the *multi-class classification task*. There are two ways to compute the metrics
>- We can compute the metrics between each two of $K$ classes i.e. **$1$-$1$ case**
>- We treat the *positive* for a *given class* as **positive**,  and the other classes as **negative**; i.e. **$1$-vs-ALL**

>[!important] Definition
>The **Macro-averaging** for multi-class metrics computes a *simple average* of *1-vs-all metrics* over all *classes*.
>
>The **Macro-averaging Precision** and **Recall** are defined as
>- $$\begin{align*}\text{Macro-Average Precision} &= \frac{1}{K}\sum_{c=1}^{K}\text{Precision}_{c} \\[5pt] &=\frac{1}{K}\sum_{c=1}^{K} \frac{\text{TP}_{c}}{\text{TP}_{c} + \text{FP}_{c}}\end{align*}$$
>- $$\begin{align*}\text{Macro-Average Recall} &= \frac{1}{K}\sum_{c=1}^{K}\text{Recall}_{c} \\[5pt] &= \frac{1}{K}\sum_{c=1}^{K} \frac{\text{TP}_{c}}{\text{TP}_{c} + \text{FN}_{c}}\end{align*}$$

>[!important] Definition
>The **Micro-averaging** computes the total number of true positives (TP), false positives (FP), and false negatives (FN) predictions *across all classes*: 
> 
> - **Total True Positive** is the *sum of true positive* counts across all classes;
> - **Total False Positive** is the *sum of false positive* counts across all classes; 
> - **Total False Negative** is the *sum of false negative* counts across all classes.
>
>The **Micro-averaging Precision** and **Recall** are defined as
>- $$\text{Micro-Average Precision} = \frac{\sum_{c=1}^{K}\text{TP}_{c}}{\sum_{c=1}^{K}\left(\text{TP}_{c} + \text{FP}_{c}\right)}$$
>- $$\text{Micro-Average Recall} = \frac{\sum_{c=1}^{K}\text{TP}_{c}}{\sum_{c=1}^{K} \left(\text{TP}_{c} + \text{FN}_{c}\right)}$$




## Explanation

>[!quote]
>- **Macro-averaging** calculates each class's performance metric (e.g., precision, recall) and then takes the arithmetic mean across all classes. 
>	- So, the macro-average gives equal **weight to each class**, regardless of the number of instances.
>- **Micro-averaging**, on the other hand, aggregates the counts of true positives, false positives, and false negatives across all classes and then calculates the performance metric based on the total counts. 
>	- So, the micro-average gives equal **weight to each instance**, regardless of the class label and the number of cases in the class.
>	  
>-- Tutorial [multi-class-metrics](https://www.evidentlyai.com/classification-metrics/multi-class-metrics)	  








-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]] pp 280
- [[Evaluating Learning Algorithms by Japkowicz]]
- Tutorial [multi-class-metrics](https://www.evidentlyai.com/classification-metrics/multi-class-metrics)

