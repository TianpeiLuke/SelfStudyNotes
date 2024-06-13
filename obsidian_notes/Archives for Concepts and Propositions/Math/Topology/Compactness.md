---
tags:
  - concept
  - math/topology
keywords:
  - compact_set
topics:
  - topology
name: Compactness
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Compactness


>[!important] Definition
>A topological space $X$ is said to be **compact** if *every open covering* $\mathscr{A}$ of $X$ contains a *finite subcollection* that also *covers* $X$.


## Explanation

>[!important] Theorem 
>Let $X$ be a *topological space*. Then $X$ is **compact** *if and only if* for *every collection* $\mathscr{C}$ of **closed sets** in $X$ having **the finite intersection property (f.i.p.)**, the intersection $\bigcap_{C\in \mathscr{C}}C$ of all the elements of $\mathscr{C}$ is **nonempty**.
> 
> $$
> \begin{align*}
> \bigcap_{\{i = 1 \,{,}\ldots{,}\,n, C_i \in \mathscr{C}\}}C_{i} \neq \emptyset, \quad \forall\, n\text{ is finite} \implies \bigcap_{C \in \mathscr{C}}C \neq \emptyset
> \end{align*}
> $$


>[!info]
>This theorem provides an equivalent definition of compactness.

- [[Finite Intersection Property]]

>[!important] 
>A special case of this proposition occurs when we have a **nested sequence** $$C_1 \supseteq C_2 \,{\supseteq}\ldots{\supseteq}\, C_n \supseteq  \ldots$$ of **closed sets** in a **compact space** $X$. 
> 
> If each of the sets $C_n$ is nonempty, then the collection $\mathscr{C} = \set{C_n}_{n \in \mathbb{N}}$ automatically has **the finite intersection  property**. 
> 
> Then the intersection
>$$ 
> \begin{align*}
> \bigcap_{n \in \mathbb{N}}C_n
> \end{align*}
>$$ 
>is nonempty.

- [[Monotone Sequence of Nested Sets]]
- [[Finite Intersection Property]]


## Properties


- [[Closed Graph Theorem]]

- [[Tychonoff Theorem and Product of Compact Space]]


## Continuous Function on Compact Space


>[!important] Proposition
>Let $f : X \rightarrow Y$ be a **bijective continuous** function. 
>
>If $X$ is **compact** and $Y$ is **Hausdorff**, then $f$ is a **homeomorphism**.

- [[Hausdorff Space]]
- [[Homeomorphism]]

>[!important] Uniform Continuity Theorem
> Let $f: X \rightarrow Y$ be a **continuous map** of the **compact** *metric space* $(X, d_X)$ to *the metric space* $(Y, d_Y)$. 
> 
> Then $f$ is **uniformly continuous**.

- [[Uniform Topology on Metric Spaces]]
- [[Uniform Continuity on Metric Space]]
- [[Uniform Continuity Theorem]]

## Compactness in Metric Space

>[!important] Proposition (Equivalence of Compactness)
>Let $X$ be a **metrizable space**. 
>
>Then the following are **equivalent**:
>
>- $X$ is **compact**.
>- $X$ is **limit point compact**.
>- $X$ is **sequentially compact**.

- [[Limit Point Compactness]]
- [[Sequential Compactness]]

## Concepts related to Compactness


>[!important]
>$$
>\text{compactness } \subset \text{$\sigma$-compactness }  \subset \text{Lindelöf  } 
>$$

- [[Compactness]]
- [[sigma-Compactness]]
- [[Lindelöf Space]]

>[!important]
>$$
>\text{regular Lindelöf  }  \subset \text{ paracompactness}
>$$

- [[Regular Space]]
- [[Lindelöf Space]]
- [[Paracompactness]]

>[!important]
>$$
>\text{locally compactness } + \text{ second countable} \subset \text{$\sigma$-compactness }
>$$

- [[Locally Compactness]]
- [[Second Countablity]]
- [[sigma-Compactness]]



-----------
##  Recommended Notes and References

- [[Covering of Set and Open Covering of Topological Set]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)