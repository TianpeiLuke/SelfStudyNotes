---
tags:
  - concept
  - machine_learning/metrics
  - information_retrieval/relevancy_metric
  - natural_language_processing/metric
  - mean_average_precision
keywords:
  - mean_average_precision
  - average_precision
topics:
  - machine_learning_metrics
  - information_retrieval/metrics
  - natural_language_processing/metrics
name: Mean Average Precision and Average Precision
date of note: 2024-11-25
---
## Concept Definition

>[!important]
>**Name**: Mean Average Precision or MAP and Average Precision

### Average Precision

>[!important] Definition
>Let the set of *relevant documents* for given query $q\in Q$ be $$\mathcal{D}_{R} := \left\{ d_{1}\,{,}\ldots{,}\,d_{m} \right\}$$
>- Assume that for given query $q$, the system *retrieved* $K$ documents.
>
>The **average precision** for given query $q$ is given by 
>$$
>\begin{align*}
>\text{Average Precision}(q) &:= \sum_{k=1}^{K}\text{Precision@k} \cdot (\text{Recall@k} - \text{Recall@(k-1)}) \\[5pt]
>&= \frac{1}{\#\text{ relevant documents}}\sum_{k=1}^{K}\text{Precision@k} \cdot \text{IsRelevant}(k) \\[5pt]
>&= \frac{1}{m}\sum_{s=1}^{m}\text{Precision}(R_{q,s})
>\end{align*}
>$$
>where
>- $R_{q,k}$ be the set of *ranked retrieved documents* for the query $q$ from top *until* the document $d_{k}$. $$(s_{1} \,{,}\ldots{,}\,s_{R_{j,k}}\,, d_{k})$$
>- $|R_{q,k}|$ is the *rank* of *relevant document* $d_{k}$ among $K$ retrieved documents.$$\text{Precision}(R_{q,s}) := \text{Precision@}|R_{q,s}|$$
>- **Average Precision** is the **area under precision-recall curve (AUPRC)**.

- [[Recall and Precision at k]]
- [[Precision-Recall Curve]]
- Wikipedia [Average precision](https://en.wikipedia.org/w/index.php?title=Information_retrieval&oldid=793358396#Average_precision)

>[!info]
>Note that 
>$$
>\begin{align*}
>& \sum_{k=1}^{K}\text{Precision@k} \cdot (\text{Recall@k} - \text{Recall@(k-1)}) \\[5pt]
>&= \sum_{k=1}^{K} \frac{1}{k} \#\{ x_{i}:\; x_{i} \in \mathcal{D}_{R},\;\;  i\le k \}\; \frac{1}{m}\left(\#\{ x_{i}:\; x_{i} \in \mathcal{D}_{R},\;\;  i\le k \} - \#\{ x_{i}:\; x_{i} \in \mathcal{D}_{R},\;\;  i\le k-1 \}\right) \\[5pt]
> &= \sum_{k=1}^{K} \frac{1}{k} \#\{ x_{i}:\; x_{i} \in \mathcal{D}_{R},\;\;  i\le k \}\; \frac{1}{m}\mathbb{1}\{ x_{k} \in \mathcal{D}_{R}\}  \\[5pt]
> &= \frac{1}{m} \sum_{k=1}^{K} \text{Precision@k}\; \cdot \text{IsRelevant}(k)
>\end{align*}
>$$
>
>Also
>$$
>\begin{align*}
>&\frac{1}{m} \sum_{k=1}^{K} \text{Precision@k}\; \cdot \text{IsRelevant}(k) \\[5pt]
>&= \frac{1}{m} \sum_{s=1}^{m} \text{Precision@$k_s$} \\[5pt]
>&= \frac{1}{m} \sum_{s=1}^{m} \text{Precision}(R_{q,s})
>\end{align*}
>$$
>where $$k_{s} := \text{rank of relevant }d_{s}\in \mathcal{D}_{R} := |R_{q, s}|$$


### Mean Average Precision

>[!important] Definition
>Let $Q$ be a set of *queries*. 
>- The set of *relevant documents* for given query $q_{j}\in Q$ is $$\left\{ d_{1}\,{,}\ldots{,}\,d_{m_{j}} \right\}$$ and 
>- Let $R_{j,k}$ be the set of *ranked retrieved documents* for the query $q_{j}$ from top *until* the document $d_{k}$. $$(s_{1} \,{,}\ldots{,}\,s_{R_{j,k}}\,, d_{k})$$
>	- $|R_{j,k}|$ is the **rank** of the *relevant* document $d_{k}$ in the *ordered retrieved list* from query $q_{j}$.
>
>Then the **mean average precision (MAP)** for the *query set* $Q$ is defined as 
>$$
>\begin{align*}
>\text{MAP}(Q) &:=  \frac{1}{|Q|}\sum_{j=1}^{|Q|}\,\text{AP}(q_{j})\\[5pt]
>&= \frac{1}{|Q|}\sum_{j=1}^{|Q|}\, \frac{1}{m_{j}}\sum_{s=1}^{m_{j}}\text{Precision}(R_{j,s}) \\[5pt]
>&= \frac{1}{|Q|}\sum_{j=1}^{|Q|}\, \frac{1}{m_{j}}\sum_{k=1}^{K}\text{Precision@k}(q_{j}) \cdot \text{IsRelevant}(k; q_{j})
>\end{align*}
>$$
>- The MAP value for a test collection is the *arithmetic mean* of *average precision values* for individual query.
>- If a given document $d_{k}$ is *not retrieved at all* $R_{j,k} = \infty$, then the *precision value* is *zero*.

- [[Confusion Table]]
- [[Recall and Precision and F-Measure]]




## Explanation

>[!info]
>The **average precision** $$\text{Average Precision}(q_{j}) := \frac{1}{m_{j}}\sum_{k=1}^{m_{j}}\text{Precision}(R_{j,k}) $$ is defined as the average over the *relevant documents* $d_{k}$ for *given query*
>- the **average precision** is the *sum* over the **ranks** of *relevant documents* in retrieved list.
>
>The **mean average precision** is the average over *different queries* $$\text{Mean Average Precision}(Q) = \frac{1}{|Q|}\sum_{j=1}^{|Q|}\text{Average Precision}(q_{j})$$


>[!info]
>- **Precision** is measured for given threshold
>- **MAP** is measured for a **ranked list** of *retrieved results*.

>[!info]
>To compute the **average precision** for a given query:
>- *rank* the retrieved documents
>- compute the *precision* and *recall* for each retrieved document from *top* to *down*
>	- $$\text{Precision}_{i},\; \text{Recall}_{i}$$
>	- check [[Precision-Recall Curve#Approximate Precision-Recall Curve via Binning]]
>- *save* precision value when the given retrieved document is *relevant* 
>- take *average* of *saved precision values*  $$\text{Avg. Precision} = \frac{1}{|m_{j}|}\sum_{k=1}^{m_{j}}\text{Precision}_{k}$$
>  
>Then the **mean average precision** is average over all queries.  



>[!info]
>For a single query, 
>- the **average precision** approximates the **area under the uninterpolated precision-recall curve (AUPRC)**, 
>- and so the **MAP** is roughly the **average** *area under the precision-recall curve* for a set of queries.

- [[Precision-Recall Curve]]

>[!info]
>Using **MAP**, *fixed* recall levels are **not chosen**, and there is **no interpolation**.

- [[Interpolated Precision and Interpolated Average Precision]]

>[!quote]
>Calculated MAP scores normally *vary widely* across *information needs* when measured within *a single system*, for instance, between $0.1$ and $0.7.$ 
>- Indeed, there is normally more agreement in MAP for an *individual* information need *across systems* than for *MAP scores* for different information needs for the *same system*. 
>- This means that a set of test information needs must be *large and diverse* enough to be representative of system effectiveness across different queries.
>  
>-- [[Introduction to Information Retrieval by Manning]] pp 161  

## MAP vs. NDCG

![[Normalized Discounted Cumulative Gain or NDCG#^f0ab9e]]

- [[Normalized Discounted Cumulative Gain or NDCG]]




-----------
##  Recommended Notes


- [[Learning to Rank]]
- [[Information Retrieval]]

- [[Introduction to Information Retrieval by Manning]] pp 158 - 161
- [[Evaluating Learning Algorithms by Japkowicz]]
- [[Speech and Language Processing by Jurafsky]] pp 297 - 298

- Medium
	- [Recall and Precision at k for Recommender Systems](https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54)

- Youtube
	- [Evaluation 12: mean average precision](https://www.youtube.com/watch?v=pM6DJ0ZZee0)