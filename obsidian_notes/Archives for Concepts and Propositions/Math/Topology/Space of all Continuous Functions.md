---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - space_of_continuous_functions
topics:
  - topology
name: The space of all continuous functions
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  The Space of all Continuous Functions from one domain to another

>[!important] Definition
>The space of all **continuous functions** from one topological space $(X, \mathscr{T}_{X})$ to another topological space $(Y, \mathscr{T}_{Y})$ is denoted as $\mathcal{C}(X, Y)$
> $$
> \mathcal{C}(X, Y) = \left\{ f: Y^X:  f^{-1}(U) \in \mathscr{T}_{X}, \text{ for every }U\in \mathscr{T}_{Y} \right\}
> $$

- Note that $Y^X := \{f: X \rightarrow Y\}$ is the space of all mappings from $X$ to $Y$. 
- Special example of $n$-dimensional Euclidean space  $\mathbb{R}^{n}:= \{\iota: [1, \ldots, n] \rightarrow \mathbb{R}\}$ is seen as the space of coordinate functions $\iota$.


## Explanation


## Properties

>[!important] Proposition
>Let $X$ be  a **compact Hausdorff** space. Denote $\mathcal{C}(X)$ as the space of *all continuous* (complex-valued) functions on $X$, endowed with the norm
>$$
>\lVert f \rVert_{\infty} := \sup_{x \in X}\lvert f(x) \rvert.  
>$$ 
>
>Let $\mathcal{C}(X, \mathbb{R})$ be the space of all real-valued continuous functions on $X$.
>
>Then $\mathcal{C}(X)$ is a complex **Banach space** and $\mathcal{C}(X, \mathbb{R})$ is a real **Banach space**.

- [[Compact Hausdorff Space]]
- [[Uniform Topology on Metric Spaces]]
- [[Banach Space]]




-----------
##  Recommended Notes and References

- [[Topology of Set]]
- [[Continuous Function]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)