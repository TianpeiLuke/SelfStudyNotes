---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - statistics/hypothesis_testing
keywords:
  - roc_curve
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Receiver Characteristic Curve for Binary Classification
date of note: 2024-04-25
---
## Concept Definition

>[!important]
>**Name**: Receiver Characteristic Curve for Binary Classification

![[Confusion Table#^16427b]]

- [[Confusion Table]]

![[True or False Positive Rate and True or False Negative Rate#^1ea887]]

- [[True or False Positive Rate and True or False Negative Rate]]

>[!important] Definition
>For *binary classification*, the **receiver characteristic curve** is given by a plot where
>- $x$-axis is the **true positive rate**
>- and $y$-axis is the **false postive rate**.
>- That is, it is a *TPR-FPR plot*.  

- [[Classification Problem]]



## Explanation



## Approximate ROC with Binning

>[!important] Definition
>The **receiver characteristic curve** can be estimated via *binning*
>- *Require*: binary labeled validation data $\mathcal{D} := \left\{ (x_{n}, y_{n}) \right\}$
>- Evaluate the validation data with model, and assign each test sample $x_{n}$ with a score $p_{n}$
>- *Sort* the validation data in *descending order* according to score 
>- Divide the sorted test data into $K$ *bins*
>	- Denote the cut-off thresholds for each bin as  $$[p^{(0)}, p^{(1)}],\, (p^{(1)}, p^{(2)}] \,{,}\ldots{,}\,(p^{(K-1)}, p^{(K)}]$$
>		- Normally, choose  $p^{(0)}=1,\; p^{(K)} = 0$
>	- Denote $i$-th bin as $$I_{i} := \left\{ x_{n}: p_{n}\in (p^{(i-1)}, p^{(i)}] \right\}, \quad i=1\,{,}\ldots{,}\,K$$
>- Initialize $$\text{TP}_{\le 0} = 0,\;\text{FP}_{\le 0} = 0$$
>- Count the total **actual positive** $$\text{P} = \#\left\{ x_{n}\in \mathcal{D}:\; y_{n} =1 \right\}$$ 
>- For each bin $i=1\,{,}\ldots{,}\,K$:
>	- All test samples with score $\ge p^{(i)}$ are counted as *predicted positive*
>	- Count the **true positive** within bin $i$ as $\text{TP}_{i}$ $$\text{TP}_{i} := \#\left\{ x_{n}\in I_{i}: \; y_{n} = 1 \right\}$$
>	- Count the **false positive** within bin $i$ as $\text{FP}_{i}$ $$\text{FP}_{i} := \#\left\{ x_{n}\in I_{i}: \; y_{n} = 0 \right\}$$
>	- Aggregate **total true positive** for all samples with score $\ge p^{(i)}$ as $$\text{TP}_{\le i} = \text{TP}_{\le i-1} + \text{TP}_{i}$$
>	- Aggregate **total false positive** for all samples with score $\ge p^{(i)}$ as $$\text{FP}_{\le i} = \text{FP}_{\le i-1} + \text{FP}_{i}$$
>	- Compute the **true positive rate** with score $\ge p^{(i)}$ as $$\text{TPR}_{\le i} = \frac{\text{TP}_{\le i}}{P}$$
>	- Compute the **false positive rate** with score $\ge p^{(i)}$ as $$\text{FPR}_{\le i} = \frac{\text{FP}_{\le i}}{P}$$
>- *Return* the list
>	- $$\text{TPR-L} := [\text{TPR}_{\le 1} \,{,}\ldots{,}\,\text{TPR}_{\le K}]$$
>	- $$\text{FPR-L} := [\text{FPR}_{\le 1} \,{,}\ldots{,}\,\text{FPR}_{\le K}]$$


![[Create AUC in SQL#^02c039]]

- [[Create AUC in SQL]]







-----------
##  Recommended Notes


- [[Introduction to Information Retrieval by Manning]] pp 162
- [[Speech and Language Processing by Jurafsky]] pp 66
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Elements of Statistical Learning by Hastie]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 148
- [[Foundations of Machine Learning by Mohri]] pp 239, 255 - 265

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [ROC and AUC, Clearly Explained!](https://www.youtube.com/watch?v=4jRBRDbJemM&t=868s)