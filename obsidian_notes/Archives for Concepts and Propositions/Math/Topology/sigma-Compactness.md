---
tags:
  - concept
  - math/topology
keywords:
  - sigma_compact
topics:
  - topology
name: sigma-Compact
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  $\sigma$-Compact

>[!important] Definition
>A topological space is **$\sigma$-compact** if it can be covered by *countably many* open sets that are *locally compact*.
>
>That is, for topological space $\mathcal{X}$, there exists a *countable collection* $\mathscr{C} = \{ C_{i} \}_{i=1}^{\infty}$ of open subsets of $\mathcal{X}$, such that  
>$$
>X = \bigcup_{i=1}^{\infty}C_{i}
>$$
>and for each $C_{i} \in \mathscr{C}$, there exists a **compact set** $K_{i}$ containing it, i.e. $$C_{i} \subset K_{i}.$$

- [[Locally Compactness]]
- [[Covering of Set and Open Covering of Topological Set]]
- [[Countable Set and Uncountable Set]]


## Explanation





## Property

>[!important] Proposition
>If $X$ is **locally compact** and **second countable**, then $X$ is **$\sigma$-compact**.

- [[Locally Compactness]]
- [[Second Countablity]]

>[!important] Proposition
>Every **locally compact Lindelöf space** is **$\sigma$-compact**.

- [[Locally Compactness]]
- [[Lindelöf Space]]


>[!important] Proposition
>If $X$ is **$\sigma$-compact**, then $X$ is **Lindelöf Space**; that is *every open covering* of $X$ contains a *countable subcovering*.

- [[Lindelöf Space]]

>[!important]
>We have
>$$
>\text{compactness } \subset \text{$\sigma$-compactness }  \subset \text{Lindelöf  } 
>$$
>$$
>\text{locally compact Lindelöf  } \subset \text{$\sigma$-compactness }  
>$$
>and
>$$
>\text{regular Lindelöf  }  \subset \text{ paracompactness}
>$$

- [[Compactness]]
- [[sigma-Compactness]]
- [[Lindelöf Space]]
- [[Paracompactness]]
- [[Regular Space]]


>[!important] Proposition
>Let $(Y, d)$ be a *metric space*.
>
>If $X$ is **$\sigma$-compact**, then there **exists a metric** for *the topology of compact convergence* on $Y^X$ such that if $Y$ is **complete**, then *$Y^X$* under this topology is **complete**.

^7232d3


- [[Metric Space]]
- [[Metrizable Space]]
- [[Topology of Compact Convergence]]
- [[Complete Metric Space]]




-----------
##  Recommended Notes and References


- [[Lindelöf Space]]
- [[Compactness]]
- [[Covering of Set and Open Covering of Topological Set]]
- [[Locally Compactness]]


- Wikipedia [$\sigma$-compact](https://en.wikipedia.org/wiki/%CE%A3-compact_space)
- [[Topology Book by Munkres]]