---
tags:
  - concept
  - math/measure_theory
keywords:
  - G_delta_set
  - F_sigma_set
topics:
  - measure_theory
name: Gdelta set and Fsigma set
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  $G_{\delta}$ set and $F_{\sigma}$ set


>[!important] Definition
>- $G_{\delta}$ set is defined as a **countable intersection** of *open sets*.
>  $$G_{\delta} := \bigcap_{n=1}^{\infty}G_{n}.$$
>  
>- $F_{\sigma}$ set is defined as a **countable union** of *closed sets*.  
>  $$F_{\sigma} := \bigcup_{n=1}^{\infty}F_{n}.$$

- [[Borel sigma Field]]

## Explanation

>[!info]
>By definition of Topology, 
>- $G_{\delta}$ set is **not necessarily open.** 
>	- Note: a countable **union** of open sets is open.
>- $F_{\sigma}$ set is **not necessarily closed.**
>	- Note: a countable **intersection** of closed set is closed.

- [[Topology of Set]]


>[!info]
>On the other hand, by **complement** property and **countable additivity** property of (Borel) $\sigma$-algebra ,  $G_{\delta}$ set and $F_{\sigma}$ set are **both Borel sets**
>- $F_{\sigma} \in \mathcal{B}$ since it is countable union of a Borel set (closed set)
>- $G_{\delta} \in \mathcal{B}$ since it is complement of a $F_{\sigma}$ set







-----------
##  Recommended Notes and References

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Topology of Set]]


- Wikipedia [G delta set](https://en.wikipedia.org/wiki/G%CE%B4_set)
- Wikipedia [F sigma set](https://en.wikipedia.org/wiki/F%CF%83_set)