---
tags:
  - concept
  - math/calculus_of_variations
  - math/functional_analysis
keywords:
  - gateaux_derivative_banach
topics:
  - variational_calculus
  - functional_analysis
name: Gateaux Derivative and Weak Derivative in Banach Space
date of note: 2024-10-29
---

## Concept Definition

>[!important]
>**Name**: Gateaux Derivative and Weak Derivative in Banach Space

![[Fréchet Derivative and Strong Derivative in Banach Space#^8e4985]]

- [[Fréchet Derivative and Strong Derivative in Banach Space]]

>[!important] Definition
>Let $(X, \lVert \cdot \rVert)$ be a *Banach space* with norm $\lVert \cdot \rVert$. Denote $X^{*}$ be the dual space, i.e the space of *bounded linear functionals* on $X$.
>
>Assume that $F: V \to \mathbb{R}$ is a *functional* on some open subset $V$ of $X$ and let $u_{0}\in V$.
>
>The functional $F$ is said to be **Gateaux differentiable** *at* $u_{0}$ if there exists some *bounded linear functional* $\ell\in X^{*}$ such that 
>$$
>F(u_{0} + \epsilon h) = F(u_{0}) + \epsilon \ell(h) + o\left(\epsilon\right), \quad \text{ as } \epsilon \to 0 
>$$
>*holds* for *any* $h\in X$, and $|\epsilon| < \epsilon_{0}$ with *sufficiently small* $\epsilon_{0}h > 0$. 
>- In other word, $F$ is **Gateaux differentiable** *at* $u_{0}$ if there exists $\ell\in X^{*}$ such that $$\begin{align*}\lim_{ \epsilon \to 0 } \frac{|F(u_{0} + \epsilon h) - F(u_{0}) - \epsilon \ell(h)|}{\epsilon} = 0, \quad \forall h\in X, |\epsilon| < \epsilon_{0} \end{align*}$$
>
>- We call the *value* $\ell(h)$  as the  **Gateaux derivative** of $F$  *at* $u_{0}$, i.e. $$\delta F(u_{0}, h)  = \ell(h).$$ 
>- The **Gateaux derivative** is also called the **weak derivative** of *functional* $F$.





## Explanation

>[!info]
>The *Gateaux derivative* is the **directional derivative** of *functional* in *function space* where the direction $h$ itself is a function.

- [[Derivation of Smooth Map at point and Tangent Vector]]

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


>[!info]
>- The the  **Fréchet derivative** of a *functional* at a point is a **linear functional** $$DF(u_{0}) \in X^{*}$$
>- And the **Gateaux derivative** of a *functional* at a point is **real-value** $$\delta F(u_{0}, h) \in \mathbb{R}.$$ 
>	- The *Gateaux derivative* can be seen as a **directional derivative** of $F$ along direction $h$.

## Variational Derivative

![[Variational Derivative of Functional#^82443b]]

- [[Variational Derivative of Functional]]




-----------
##  Recommended Notes and References




- [[Banach Space]]


- [[Optimization by Vector Space Methods by Luenberger]] pp 171
- Giaquinta, M. and Hildebrandt, S. (1996) *Calculus of Variations 1. The Lagrangian Formalism*, Grundlehren der Mathematischen Wissenschaften 310. Springer-Verlag, Berlin. pp 10
- Jonathan M. Borwein and Adrian S. Lewis. (2005). *Convex Analysis and Nonlinear Optimization: Theory and Examples*. , Springer. 2nd Edition pp 22, 36, 73, 151 - 157, 160, 240, 245