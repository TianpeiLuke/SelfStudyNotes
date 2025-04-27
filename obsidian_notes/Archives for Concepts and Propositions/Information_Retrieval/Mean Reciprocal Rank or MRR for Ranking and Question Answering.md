---
tags:
  - concept
  - natural_language_processing/question_answering
  - natural_language_processing/metric
  - information_retrieval/relevancy_metric
  - information_retrieval/ranking
  - MRR
  - mean_reciprocal_rank
keywords:
  - mean_reciprocal_rank_metric
topics:
  - natural_language_processing/question_answering
  - natural_language_processing/metrics
  - information_retrieval/metrics
name: Mean Reciprocal Rank or MRR for Ranking and Question Answering
date of note: 2024-12-04
---

## Concept Definition

>[!important]
>**Name**: Mean Reciprocal Rank or MRR for Ranking and Question Answering

>[!important] Definition
>The **mean reciprocal rank (MRR)** is a statistic measure for a generation process that produce a *list* of *possible responses* to a query $q$, *ordered* by probability of correctness.
>- It is a metric for *ranked list.*
>
>The **mean reciprocal rank (MRR)** is defined as the *multiplicative inverse* of the *rank* of the *first correct answer*
>$$
>\text{MRR} := \frac{1}{|Q|}\sum_{i=1}^{|Q|} \frac{1}{\text{rank}_{i}}
>$$
>where
>- $\text{rank}_{i}$ is the  *rank* of the *first correct answer* for $i$-th question
>	- e.g. $\text{rank}_{i} = 3$ if the first correct answer is the 3rd answer.
>- $Q$ is the *question set* or *test set*.

- [[Question Answering Problem]]
- [[Order Statistics]]


## Explanation

>[!info]
>The *higher* the MRR score, the *better* the question answering system. 
>- higher MRR score means that the system give *high rank for correct answer*



-----------
##  Recommended Notes and References

- [[Information Retrieval]]

- [[Speech and Language Processing by Jurafsky]] pp 305 - 306
- [[Handbook of Natural Language Processing by Indurkhya]]

- Wikipedia [Mean reciprocal rank](https://en.wikipedia.org/wiki/Mean_reciprocal_rank)