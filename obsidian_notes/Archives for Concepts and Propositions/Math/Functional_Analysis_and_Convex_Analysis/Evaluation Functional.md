---
tags:
  - concept
  - math/functional_analysis
keywords:
  - evaluational_functional
topics:
  - functional_analysis
name: Evaluation Functional
date of note: 2024-06-03
---

## Concept Definition

>[!important]
>**Name**: Evaluation Functional

>[!important] Definition
>Let $X$ be a *vector space* over field $F$, and $\mathcal{H} = F^{X}$ be the space of $F$-valued functions on $X$.  
>
>For given $x\in X$, a *linear functional* $$\delta_x: \mathcal{H} \rightarrow F$$ is called an **evaluation functional** if 
>$$
> \begin{align*}
> \delta_x(f) = f(x), \quad \forall f \in \mathcal{H}
> \end{align*}
>$$  
>That is, $\delta_x$ *evaluates* each function $f \in \mathcal{H}$ *at a point* $x$.

- [[Vector Space over a Field]]
- [[Function]]


## Explanation

>[!info]
>$\delta_x$ is a linear functional since the space of all functions formed a *vector space* over $F$.


>[!important]
>We can represent the **evaluational functional** on *Banach space* via [[Canonical Dual Pairing]].
>
>That is, for fixed $x\in X$ and $f\in X^{*}$
>$$
>\delta_{x}(f) = \left\langle f , x \right\rangle := f(x)
>$$
>where $\left\langle \cdot , \cdot \right\rangle: X^{*} \times X \to \mathbb{R}$


- [[Canonical Dual Pairing]]

>[!important]
>In general, $\delta_{x}$ **may be not continuous** as it may not be **bounded**.

- [[Bounded Linear Functional]]
- [[Dual Space of Hilbert Space]]

## Delta Function

- [[Delta Function]]




-----------
##  Recommended Notes and References

- [[Bounded Linear Functional]]
- [[Linear Map]]

- [[Vector Space over a Field]]
- [[Dual Space of Hilbert Space]]
- [[Canonical Dual Pairing]]


- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Topology Book by Munkres]]