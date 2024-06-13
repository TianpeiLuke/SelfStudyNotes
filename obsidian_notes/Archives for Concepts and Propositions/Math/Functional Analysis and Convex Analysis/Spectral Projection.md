---
tags:
  - concept
  - math/functional_analysis
keywords:
  - spectral_projection
topics:
  - functional_analysis
name: Spectral Projection
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Projection

>[!important] Definition
>Let $A$ be a *bounded self-adjoint* operator and $S$ be a *Borel set* of $\mathbb{R}$. Let $\widehat{\phi}: B(\mathbb{R}) \to \mathcal{L}(\mathcal{H})$ be the map of functional calculus so that $$f \mapsto \widehat{\phi}(f) := f(A).$$
>
>A *functional calculus* defined as 
>$$ 
> \begin{align*}
> P_{S} := \mathbb{1}_{S}(A) = \widehat{\phi}\left(\;\mathbb{1}\left\{ \lambda\in \sigma(A) \cap S  \right\}\;\right) \in \mathcal{L}(\mathcal{H})
> \end{align*}
>$$  
>is called a **spectral projection** of $A$. 

^50c777

>[!info]
>This project operator is *induced* by the indicator / *characteristic function* on **spectrum**  via the **functional calculus**. Hence the name "spectral" projection.

- [[Spectral Theorem in Functional Calculus Form]]

>[!info]
>It is result of applying the **characteristic function** of set $S$, $$\mathbb{1}_{S}(x),$$ on *operator* $A$ via **functional calculus.**

- [[Spectral Theorem in Functional Calculus Form]]

## Explanation

>[!important]
>$P_{S}$ is an **orthogonal projection operator** since the characteristic function $\mathbb{1}_{S}(x)$ satisfies
>$$
>\mathbb{1}_{S}(x)^2 = \mathbb{1}_{S}(x).
>$$

- [[Projection Operator in Hilbert Space]]



## Simple Functional Operator


>[!info]
>Note that
>$$
>\sum_{i=1}^{n}g(\lambda_{i})P_{S_{i}}
>$$
>has one-to-one correspondence of the **simple integral of simple function** on *spectrum*
>$$
>\sum_{i=1}^{n}g(\lambda_{i})\mathbb{1}_{S_{i}}
>$$

- [[Simple Integral of Simple Functions]]


## Projection Operator as Measure

- [[Projection-Valued Measure]]




-----------
##  Recommended Notes and References

- [[Projection Operator in Hilbert Space]]
- [[Projection Map onto Linear Subspace]]


- [[Functional Analysis by Reed]]