---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords: 
topics:
  - functional_analysis
  - linear_algebra
name: 
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Cyclic Vector for Linear Operator in Hilbert Space

>[!important] Definition
>A vector $\psi \in \mathcal{H}$ is called a **cyclic vector** *for* $A$ if *finite linear combinations* of the elements $$\set{A^{n}\psi}_{n=0}^{\infty}$$ are **dense** in $\mathcal{H}$.
>

- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Dense Set]]

>[!important]
>That is, $\psi\in \mathcal{H}$ is *cyclic*, if for any $x\in \mathcal{H}$, any $\epsilon >0$, there exists some $N\in \mathbb{N}$ such that for all $n > N$,
>$$
> \left\lVert x - a_{0}\psi - \sum_{i=1}^{n}a_{i}A^{i}\psi  \right\rVert_{\mathcal{H}} < \epsilon 
>$$
>for some $(a_{0}, \,{,}\ldots{,}\,a_{n})$.

- [[Krylov Subspace and Krylov Matrix]]

## Explanation

>[!info]
>We know from [[Nilpotent Linear Transformation and Matrix]] that
>$$
>\left\{ \psi, A\psi, \ldots A^{n}\psi\right\}
>$$
>for any finite $n$ are linearly independent. 





-----------
##  Recommended Notes and References

- [[Nilpotent Linear Transformation and Matrix]]
- [[Dense Set]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]


- [[Functional Analysis by Reed]]