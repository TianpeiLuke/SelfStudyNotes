---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
keywords:
  - measure_preserving_transformation
topics:
  - stochastic_process
  - functional_analysis
  - measure_theory
name: Measure Preserving Transformation
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Measure Preserving Transformation

>[!important] Definition
>Let $\mathcal{X}$ be a vector space, and $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space*. 
>
>A *measurable linear transformation*  $T \in \mathcal{L}(\mathcal{X})$ is called **measure preserving** if $$\mu\left(T^{-1}A \right) = \mu(A)$$ for any $A \in \mathscr{F}.$


- [[Vector Space over a Field]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Space of Bounded Linear Operators]]

>[!info]
>It is common to consider only an **invertible measure preserving** $T$. In this case, the inverse $T^{-1}$ is also *measure preserving*.

- [[Bijective Function and Inverse Function]]
- [[General Linear Group]]

## Explanation





## Examples

### Finite Dimensional Space

>[!important] Proposition
>A *linear transformation* $T \in \mathcal{L}(V)$ on real **finite dimensional space** $V$ is **measure preserving** *if and only if* $$T\in \text{SL}(n, \mathbb{R}) := \left\{T:\; \det T = 1  \right\} $$ i.e. $T$ is *invertible* with *determinant* $1$.
>
>Note that for every Borel set $A \in \mathcal{B}[V]$, $$m\left(T^{-1}\,A\right) = \frac{1}{|\det T|} m(A).$$

- [[Special Linear Group]]
- [[Automorphism between Groups]]
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 7

### Lebesgue Measure and Translation

![[Lebesgue Measure#^e5f70d]]

- [[Lebesgue Measure]]

>[!example]
>Any **translation operation** on Euclidean space is **measure preserving transformation** with respect to *Lebesgue measure*.

### Volume-Preserving Flow and Divergence Theorem

![[Divergence Operator of Vector Field on Riemannian Manifold#^380a08]]

![[Divergence Operator of Vector Field on Riemannian Manifold#^d27f04]]

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Local Flow on Smooth Manifold]]
- [[Global Flow on Smooth Manifold]]


>[!example]
>The **smooth flow** $$\theta_{t}: M \to M $$ of vector field $X$ whose divergence $\text{div}(X) = 0$ is a **measure-preserving transformation**.
>$$
> m\left(\theta_{t}^{-1}(D)\right) = m\left(D\right)
>$$
>where $m(\cdot)$ is a *measure* on *Riemannian manifold*.

- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 3



-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Space of Bounded Linear Operators]]

- [[Topological Group]]
- [[Special Linear Group]]
- [[Unitary Group]]
- [[Orthogonal Group]]


- [[Real Analysis by Royden]]
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 3
- [[Functional Analysis by Reed]]
- [[Monte Carlo Statistical Methods by Robert]]

