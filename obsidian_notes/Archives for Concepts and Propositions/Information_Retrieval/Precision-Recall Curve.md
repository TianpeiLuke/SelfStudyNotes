---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
keywords:
  - precision_recall_curve
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Recall and Precision at k
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**:  Recall and Precision at k

![[Recall and Precision and F-Measure#^6fe4b0]]

![[Recall and Precision and F-Measure#^eb0990]]

>[!important] Definition
>The **precision-recall curve** depicts the *tradeoff* of *recall* vs. *precision* when the number of *retrieved items* changes
>- *High precision* is achieved if the number of retrieved items  is *decreased*
>- *High recall* is achieved if the number of retrieved items  is *increased*
>  
>We can control the number of *retrieved items* by changing the cut-off threshold of the model.

- [[Recall and Precision and F-Measure]]
- [[Confusion Table]]

>[!important] Definition
>The **precision-recall curve** is *non-smooth*:  
>- the curve jags *up* and to the *right*.
>- if $(k+1)$-th *retrieved* document is **irrelevant**, then 
>	- the *recall* is the *same* as the *top*-$k$ documents
>	- the *precision* is *decreased* compared to that of the *top*-$k$ documents
>- if $(k+1)$-th *retrieved* document is **relevant**, then 
>	- both the *recall* and *precision* are *increased* compared to that of the *top*-$k$ documents

^35ccab


![[precision_recall_curve.png]]

### Approximate Precision-Recall Curve via Binning

>[!important] Definition
>The **precision-recall curve** can be estimated via *binning*
>- *Require*: binary labeled validation data $\mathcal{D} := \left\{ (x_{n}, y_{n}) \right\}$
>- Evaluate the validation data with model, and assign each test sample $x_{n}$ with a score $p_{n}$
>- *Sort* the validation data in *descending order* according to score 
>- Divide the sorted test data into $K$ *bins*
>	- Denote the cut-off thresholds for each bin as  $$[p^{(0)}, p^{(1)}],\, (p^{(1)}, p^{(2)}] \,{,}\ldots{,}\,(p^{(K-1)}, p^{(K)}]$$
>		- Normally, choose  $p^{(0)}=1,\; p^{(K)} = 0$
>	- Denote $i$-th bin as $$I_{i} := \left\{ x_{n}: p_{n}\in (p^{(i-1)}, p^{(i)}] \right\}, \quad i=1\,{,}\ldots{,}\,K$$
>- Initialize $$\text{TP}_{\le 0} = 0,\;\text{PP}_{\le 0} = 0$$
>- Count the total **actual positive** $$\text{P} = \#\left\{ x_{n}\in \mathcal{D}:\; y_{n} =1 \right\}$$ 
>- For each bin $i=1\,{,}\ldots{,}\,K$:
>	- All test samples with score $\ge p^{(i)}$ are counted as *predicted positive*
>	- Count the **true positive** within bin $i$ as $\text{TP}_{i}$ $$\text{TP}_{i} := \#\left\{ x_{n}\in I_{i}: \; y_{n} = 1 \right\}$$
>	- Count the **predictive positive** within bin $i$ as $\text{PP}_{i}$ $$\text{PP}_{i} := |I_{i}|$$
>	- Aggregate **total true positive** for all samples with score $\ge p^{(i)}$ as $$\text{TP}_{\le i} = \text{TP}_{\le i-1} + \text{TP}_{i}$$
>	- Aggregate **total predictive positive** for all samples with score $\ge p^{(i)}$ as $$\text{PP}_{\le i} = \text{PP}_{\le i-1} + \text{PP}_{i}$$
>	- Compute the **recall** with score $\ge p^{(i)}$ as $$\text{Recall}_{\le i} = \frac{\text{TP}_{\le i}}{P}$$
>	- Compute the **precision** with score $\ge p^{(i)}$ as $$\text{Precision}_{\le i} = \frac{\text{TP}_{\le i}}{\text{PP}_{\le i}}$$
>- *Return* the list
>	- $$\text{Recall-L} := [\text{Recall}_{\le 1} \,{,}\ldots{,}\,\text{Recall}_{\le K}]$$
>	- $$\text{Precision-L} := [\text{Precision}_{\le 1} \,{,}\ldots{,}\,\text{Precision}_{\le K}]$$

>[!info]
>This applies when $K=N$ i.e. the size of bin is $1$.

>[!important]
>The **Area Under Precision-Recall Curve (AUPRC)** is the same as the **average precision**.

- [[Mean Average Precision and Average Precision]]


## Explanation


>[!info]
>It is useful to remove the jiggles by adding *interpolated precision.*

- [[Interpolated Precision and Interpolated Average Precision]]

>[!info]
>The **area under precision-recall curve (AUPRC)** is equal to **average precision.**

>[!info]
>We have a *precision-recall curve* for **each query** $q$.








-----------
##  Recommended Notes

- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 158
- [[Evaluating Learning Algorithms by Japkowicz]]

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)
	- [Comprehensive Guide to Ranking Evaluation Metrics](https://towardsdatascience.com/comprehensive-guide-to-ranking-evaluation-metrics-7d10382c1025)

- Youtube
	- [Evaluation 11: interpolated recall-precision plot](https://www.youtube.com/watch?v=yjCMEjoc_ZI)