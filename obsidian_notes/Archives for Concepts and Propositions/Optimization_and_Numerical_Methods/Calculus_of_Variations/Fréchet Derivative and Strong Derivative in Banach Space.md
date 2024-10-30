---
tags:
  - concept
  - math/calculus_of_variations
  - math/functional_analysis
keywords:
  - frechet_derivative_banach
  - strong_derivative
topics:
  - variational_calculus
  - functional_analysis
name: Fréchet Derivative and Strong Derivative in Banach Space
date of note: 2024-10-29
---

## Concept Definition

>[!important]
>**Name**: Fréchet Derivative and Strong Derivative in Banach Space

>[!important] Definition
>Let $(X, \lVert \cdot \rVert)$ be a *Banach space* with norm $\lVert \cdot \rVert$. Denote $X^{*}$ be the dual space, i.e the space of *bounded linear functionals* on $X$.
>
>Assume that $F: V \to \mathbb{R}$ is a *functional* on some open subset $V$ of $X$ and let $u_{0}\in V$.
>
>The functional $F$ is said to be **Fréchet differentiable** *at* $u_{0}$ if there exists some *bounded linear functional* $\ell\in X^{*}$ such that 
>$$
>F(u_{0} + h) = F(u_{0}) + \ell(h) + o\left(\lVert h \rVert \right), \quad \text{ as } \lVert h \rVert \to 0 
>$$
>*holds* for *any* $h\in X$, with $u_{0}+h\in V$.
>- In other word, $F$ is **Fréchet differentiable** *at* $u_{0}$ if there exists $\ell\in X^{*}$ such that $$\begin{align*}\lim_{ \lVert h \rVert  \to 0 } \frac{|F(u_{0} + h) - F(u_{0}) - \ell(h)|}{\lVert h \rVert} = 0, \quad \forall h\in X,\; u_{0}+h \in V\end{align*}$$
>
>- We call the *linear functional* $\ell$  as the  **Fréchet derivative** of $F$  *at* $u_{0}$, i.e. $$DF(u_{0}) := F'(u_{0}) = \ell.$$ 
>- The  **Fréchet derivative** is also called the **strong derivative** of *functional* $F$.

^8e4985

- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]


## Explanation

>[!info]
>The the  **Fréchet derivative** of a *functional* at a point is a **linear functional**
>$$
>DF(u_{0}) \in X^{*}
>$$


>[!important]
>It is not hard to prove that **Frechet differentiability** implies **Gateaux differentiability** (and both derivatives coincide), whereas the **converse does not hold**.
>
>$$
>\text{Frechet differentiability } \implies \text{ Gateaux differentiability}
>$$
>-  **Frechet differentiability** means the existence of *tangent space* to *graph* of $F$ at $(u_{0}, F(u_{0}))$ $$\text{Frechet differentiability } \iff  \exists\, T_{(u_{0}, F(u_{0}))}G $$
>-  **Gateaux differentiability** means the existence of *all directional derivative* at $u_{0}$  $$\text{Gateaux differentiability } \iff  \exists\, v(F)\,\; \forall v $$

- [[Tangent Space Definition and Development]]
- [[Graph of Function]]
- [[Gateaux Derivative and Weak Derivative in Banach Space]]



-----------
##  Recommended Notes and References



- [[First Variation and Variational Derivative of Functional]]



- [[Functional Analysis by Reed]]
- [[Calculus of Variations by Gelfand]]
- Giaquinta, M. and Hildebrandt, S. (1996) *Calculus of Variations 1. The Lagrangian Formalism*, Grundlehren der Mathematischen Wissenschaften 310. Springer-Verlag, Berlin. pp 10
- Jonathan M. Borwein and Adrian S. Lewis. (2005). *Convex Analysis and Nonlinear Optimization: Theory and Examples*. , Springer. 2nd Edition pp 153 - 156, 176