---
tags:
  - concept
  - math/set_theory
keywords:
  - nested_sets
topics:
  - set_theory
name: Monotone Sequence of Nested Sets
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Nested Sets

>[!important] Definition
>A **nested** *sequence* of sets $E_{1}, E_{2}, \ldots$ is 
>- **nondecreasing** if $$E_{i}\subseteq E_{i+1}, \forall i$$
>- **nonincreasing**  if $$E_{i}\supseteq E_{i+1}, \forall i.$$


## Explanation

>[!example]
>The subset operation  $\subset$ or $\subsetneq$ is an order relation on $2^X$.

>[!example]
>Note that given any *countable* collection of sets $E_{i}$, $i=1 \,{,}\ldots{,}\,$,  
>$$
>\bigcup_{i=1}^{n}E_{i} \subseteq \bigcup_{i=1}^{n+1}E_{i}
>$$
>and
>$$
>\bigcap_{i=1}^{n}E_{i} \supseteq \bigcap_{i=1}^{n+1}E_{i}.
>$$
>
>In other word, 
>- $\{ \bigcup_{i=1}^{n}E_{i} \}_{n}$ is a **nested** sequence of **monotone increasing** sets.
>- $\{ \bigcap_{i=1}^{n}E_{i} \}_{n}$ is a **nested** sequence of **monotone decreasing** sets.



-----------
##  Recommended Notes and References

- [[Set Operations]]
- [[Simple Order Relation]]