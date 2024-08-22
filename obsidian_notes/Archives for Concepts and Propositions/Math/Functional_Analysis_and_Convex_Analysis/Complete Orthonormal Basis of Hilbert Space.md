---
tags:
  - concept
  - math/functional_analysis
keywords:
  - complete_orthonormal_basis
topics:
  - functional_analysis
name: Complete Orthonormal Basis
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**:  Complete Orthonormal Basis

>[!important] Definition
>If $S$ is an *orthonormal set* in a *Hilbert space* $\mathcal{H}$ and *no other orthonormal set* contains $S$ as a *proper subset*, then $S$ is called **an orthonormal basis** (or a **complete orthonormal system**) for $\mathcal{H}$.

- [[Orthogonality in Inner Product Space]]

## Explanation

>[!important] Theorem
>Every *Hilbert space* $\mathcal{H}$ has an **orthonormal basis**.

>[!info]
>Consider the collection $\mathscr{C}$ of all orthonormal sets in $\mathcal{H}$.
>- $\mathscr{C}$ is a **partially ordered** set with respect to the inclusion relation $$S_{1} \subset S_{2} \implies S_{1} \prec S_{2}.$$
>
>- $\mathscr{C}$ is non-empty since if $v\in \mathcal{H}$ is any nonzero element in $V$, the set $\{ v / \lVert v \rVert \}$ is an *orthonormal set*.
>
>Let $\{ S_{\alpha}, \alpha \in A \}$ be any **linearly ordered subset** of $\mathscr{C}$. 
>
>Then $$\bigcup_{\alpha\in A}S_{\alpha}$$ is also an *orthonormal set* and $$\bigcup_{\alpha\in A}S_{\alpha} \supseteq S_{\alpha}, \quad \forall \alpha\in A,$$ which is an *upper bound* of $\{ S_{\alpha}, \alpha \in A \}.$
>
>By **Zorn's lemma**, since any linearly ordered subset has an upper bound, then the collection has a **maximal element**, i.e. there exists $$S \in \mathscr{C}$$ such that for every $C \in \mathscr{C}$, $C \subseteq S.$
>
>That is, $S$ is an *orthonormal set* and it is *not properly contained* in any orthonormal set. Hence, $S$ is an **orthonormal basis**. Q.E.D.

- [[Gram-Schmidt Orthogonalization]]
- [[Strict Partial Order Relation]]
- [[Supremum and Infimum of Sets]]
- [[Upper Bound and Supremum of Set]]
- [[Zorn Lemma]]



-----------
##  Recommended Notes and References

- [[Coordinate Representation in Hilbert Space and Fourier Coefficients]]

- [[Orthogonality in Inner Product Space]]
- [[Basis of Vector Space]]
- [[Hilbert Space]]