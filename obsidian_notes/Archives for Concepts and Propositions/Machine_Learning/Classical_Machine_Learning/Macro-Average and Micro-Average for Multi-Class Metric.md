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
>The **Micro-averaging** for multi-class metrics computes the total number of true positives (TP), false positives (FP), and false negatives (FN) predictions *across all classes*: 
> 
> - **Total True Positive** is the *sum of true positive* counts across all classes;
> - **Total False Positive** is the *sum of false positive* counts across all classes; 
> - **Total False Negative** is the *sum of false negative* counts across all classes.
>
>The **Micro-averaging Precision** and **Recall** are defined as
>- $$\text{Micro-Average Precision} = \frac{\sum_{c=1}^{K}\text{TP}_{c}}{\sum_{c=1}^{K}\left(\text{TP}_{c} + \text{FP}_{c}\right)}$$
>- $$\text{Micro-Average Recall} = \frac{\sum_{c=1}^{K}\text{TP}_{c}}{\sum_{c=1}^{K} \left(\text{TP}_{c} + \text{FN}_{c}\right)}$$

>[!info]
>In **micro-averaging**, we collect the decisions for all classes into a *single confusion matrix*, and then compute precision and  recall from that table


## Explanation

>[!quote]
>- **Macro-averaging** calculates each class's performance metric (e.g., precision, recall) and then takes the arithmetic mean across all classes. 
>	- So, the macro-average gives equal **weight to each class**, regardless of the number of instances.
>- **Micro-averaging**, on the other hand, aggregates the counts of true positives, false positives, and false negatives across all classes and then calculates the performance metric based on the total counts. 
>	- So, the micro-average gives equal **weight to each instance**, regardless of the class label and the number of cases in the class.
>	  
>-- Tutorial [multi-class-metrics](https://www.evidentlyai.com/classification-metrics/multi-class-metrics)	  

### Pros and cons

>[!quote]
> A suitable metric depends on the specific problem and the importance of each class or instance.
> 
> **Macro-averaging** treats each class equally.
> 
> - It can be useful when **all classes are equally important**, and you want to know how well the classifier performs on average across them. 
> - It is also useful when you have an **imbalanced dataset** and want to ensure each class equally contributes to the final evaluation.
> 
> However, macro averaging can also distort the perception of performance. 
> 
> - For example, it **can make the classifier look “worse”** due to low performance in an unimportant and small class since it will still contribute equally to the overall score. 
> - In the opposite scenario, it **can disguise poor performance** in the critical minority class when the overall number of classes is large. In this case, the “contribution” of each class is diluted. The classifier may still achieve high macro-averaged precision and recall by performing well on the majority classes but poorly on the minority class.
> 
> If classes have unequal importance, measuring precision and recall by class or weighing them by importance might be helpful.
> 
> **Micro-averaging** can be more appropriate when you want to account for the total number of misclassifications in the dataset. It gives equal weight to each instance and will have a higher score when the overall number of errors is low. (If this sounds like accuracy, it is because it is!)
> 
> However, micro-averaging can also **overemphasize the performance of the majority class,** especially when it dominates the dataset. In this case, micro-averaging can lead to inflated performance scores when the classifier performs well on the majority class but poorly (or very poorly) on the minority classes. If the class is small, you might not notice!
> 
> As a result, there is no single best metric. To choose the most suitable one, you need to consider the number of classes, their balance, and their relative importance.
> 
>-- Tutorial [multi-class-metrics](https://www.evidentlyai.com/classification-metrics/multi-class-metrics)	   






-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]] pp 280
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Speech and Language Processing by Jurafsky]] pp 68
- Tutorial [multi-class-metrics](https://www.evidentlyai.com/classification-metrics/multi-class-metrics)

