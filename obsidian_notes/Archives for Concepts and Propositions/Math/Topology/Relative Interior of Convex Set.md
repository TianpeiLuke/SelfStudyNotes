---
tags:
  - concept
  - math/convex_analysis
  - math/topology
keywords:
  - relative_interior_convex
topics:
  - convex_analysis
  - topology
name: Relative Interior of Convex Set
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Relative Interior of Convex Set

>[!important] Definition
>The **relative interior** of a set $S$, denoted as $\text{relint}(S)$, is defined as the *interior* within the *affine hull* of $S$.
>
>$$
>\text{relint}(S) := \left\{ x\in \text{aff}(S): \exists \epsilon >0, \text{ such that }B_{\epsilon}(x) \cap \text{aff}(S) \subseteq S \right\} 
>$$
>where $B_{\epsilon}(x):= \{ x: \lVert x \rVert < \epsilon \}$, and $\text{aff}(S)$ is the *affine hull* of $S$
>$$
>\text{aff}(S) := \left\{ \sum_{i=1}^{n}\lambda_{i}x_{i}:\; x_{i} \in S,\;\; \sum_{i=1}^{m}\lambda_{i} = 1  \right\}
>$$


- [[Affine Hull]]

## Explanation

>[!important] Equivalent Definition (Convex Set)
>If $S$ is a **convex set**, the **relative interior** of $S$ can be defined as
>$$
>\text{relint}(S) := \left\{ x\in S: \forall y \in S,\; \exists \lambda > 1, \text{ such that } \lambda x + (1 - \lambda) y \in S \right\} 
>$$ 
>or
>$$
>\text{relint}(S) := \left\{ x\in S: \forall y \neq x \in S,\; \exists z \in S, \text{ such that } x = \lambda z + (1 - \lambda) y, \text{ for some }\lambda \in (0, 1) \right\} 
>$$ 

- [[Convex Set]]

## Comparison to Interior

>[!info]
> - The **interior** of a **point** in an *at least* _one-dimensional **ambient space**_ is **empty**, but its **relative interior** is the **point itself**.
> 
> - The **interior** of a **line segment** in an _at least two-dimensional ambient space_ is **empty**, but its **relative interior** is **the line segment without its endpoints**.
> 
> - The **interior** of a **disc** in an _at least three-dimensional ambient space_ is **empty**, but its **relative interior** is **the same disc** *without* **its circular edge**.

- [[Interior of Set]]

>[!important]
>The concept of **relative interior** is useful when dealing with *sub-manifolds* and *subspaces* within a **higher dimensional ambient space**. 
>
>**Interior** would be **empty** with respect to *the topology* of the higher dimensional *ambient space*. But the *relative interior would not be empty*. 



-----------
##  Recommended Notes and References

- [[Interior of Set]]
- [[Convex Set]]

- [[Convex Analysis by Rockafellar]]
- Wikipedia [Relative interior](https://en.wikipedia.org/wiki/Relative_interior)