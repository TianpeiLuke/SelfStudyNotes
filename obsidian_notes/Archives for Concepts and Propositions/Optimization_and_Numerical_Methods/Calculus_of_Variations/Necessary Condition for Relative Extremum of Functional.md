---
tags:
  - concept
  - math/calculus_of_variations
  - math/functional_analysis
  - math/differential_equation
keywords:
  - fundamental_lemma_calculus_of_variations
  - weak_extremum_functional
topics:
  - variational_calculus
  - functional_analysis
  - differential_equation
name: Necessary Condition for Relative Extremum of Functional
date of note: 2024-10-30
---

## Concept Definition

>[!important]
>**Name**: Necessary Condition for Relative Extremum of Functional


![[Extremum and Weak and Relative Extremum of Functional#^52d40d]]


>[!important] Theorem
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$, and 
>- $u(x) \in X$ be a vector-valued  *smooth function* in $\Omega$, where $X$ is a subset in the *space of smooth functions* $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$.
>- $u(x)$ is a *parameterized smooth curve* on space $\mathbb{R}^{m}$.
>
>A **necessary condition** of a functional $$J: X \to \mathbb{R}$$ to have an **relative extremum** at $u\in X$ is that its **Gateaux differential** (i.e. *first variation*) **vanishes** at $u$ *in direction to* any admissible $h\in \mathcal{C}_{c}^{1}(\Omega)$ $$\delta J(u, h) =0,\, \quad \forall h\in \mathcal{C}_{c}^{1}(\Omega,\mathbb{R}^{m})$$

^813689

- [[Extremum and Weak and Relative Extremum of Functional]]
- [[Parameterized Curve on Manifold]]

### Euler-Lagrange Equation

![[Fundamental Lemma of the Calculus of Variations#^0510db]]

- [[Fundamental Lemma of the Calculus of Variations]]

>[!important] Definition
>The **necessary condition** for **relative extremum** of $J$ at $u$ where $$J(u) := \int_{\Omega} F(x, u(x),  D u(x)) dx$$ is equivalent to 
>$$
>\begin{align*}
>\int_{\Omega}\sum_{i}\left\{ \frac{ \partial F}{ \partial u^{i}}(x, u, D u) - \text{div}\left( \frac{ \partial F }{ \partial  \nabla u^{i} }  \right)(x, u, D u) \right\}\eta^{i}(x)\,dx  &= 0 \\[5pt]
> \iff \int_{\Omega}\left\{ \sum_{i}F_{u^{i}}\,\eta^{i} + \sum_{j}\sum_{i}F_{\partial_{j}u^{i}}\,\partial_{j}\,\eta^{i} \right\}\,dx & = 0 
\end{align*}
>$$
>for all $\eta \in \mathcal{C}_{c}^{1}(\Omega)$
>- This equation is called the **weak Euler-Lagrange equation** or **Euler-Lagrange equation in weak form**.

- [[Integration by Parts]]
- [[Euler–Lagrange Equations]]

>[!important] Theorem (Euler-Lagrange Equation)
>Suppose that 
>- $\Omega \subset \mathbb{R}^{n}$ is an open set, and
>- that the **Lagrangian** $F\in \mathcal{C}^2$, i.e. **continuously second-order differentiable** , and 
>- that $u = (u^1\,{,}\ldots{,}\,u^{m})$ is a **weak extreme** of  $$J(u) := \int_{\Omega} F(x, u(x), D u(x)) dx,$$ that is,  for all $\eta \in \mathcal{C}_{c}^{1}(\Omega)$,
>$$
>\begin{align*}
>\int_{\Omega}\sum_{i}\left\{ \frac{ \partial F}{ \partial u^{i}}(x, u, D u) - \text{div}\left( \frac{ \partial F }{ \partial  \nabla u^{i} }  \right)(x, u, D u) \right\}\eta^{i}(x)\,dx  &= 0 \\[5pt]
> \iff \int_{\Omega}\left\{ \sum_{i}F_{u^{i}}\,\eta^{i} + \sum_{j}\sum_{i}F_{\partial_{j}u^{i}}\,\partial_{j}\,\eta^{i} \right\}\,dx & = 0 
\end{align*}
>$$
>
>- Moreover, let $u\in \mathcal{C}^2(\Omega, \mathbb{R}^{m})$ be **continuously second-order differentiable** .
>
>Then $u(x)$ satisfies the **Euler-Lagrange equation**
>$$
>\begin{align*}
>\frac{ \partial F}{ \partial u^{i}}(x, u, D u) - \text{div}\left( \frac{ \partial F }{ \partial  \nabla u^{i} }  \right)(x, u, D u) &= 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> \iff \frac{\partial F}{ \partial u^{i}}- \sum_{j=1}^{n}\left(\frac{\partial }{ \partial x^{j}}\frac{\partial  F}{ \partial u_{j}^{i} }\,\right)= 0
\end{align*}
>$$
>for all $x\in \Omega.$ 
>- Here $$Du = [\nabla u^{1}\,{,}\ldots{,}\,\nabla u^{m}]^{T}\in \mathbb{R}^{m\times n},\;\; \nabla u^{i} = (u_{1}^{i} \,{,}\ldots{,}\,u_{n}^{i})^T \in \mathbb{R}^{n},\;\; u_{j}^{i} = \frac{ \partial  }{ \partial x_{j} }u^{i} $$
>- Actually, the same conclusion **holds** if $F_{u^{i}} \in \mathcal{C}$ and $F_{\partial_{j}u^{i}} \in \mathcal{C}^{1}$.

^70ac73

- [[Euler–Lagrange Equations]]


## Explanation



## Necessary Condition for Local Minimum in Euclidean Space

![[Necessary and Sufficient Condition for Local Minimum of Smooth Function#^da6d0c]]

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]



-----------
##  Recommended Notes and References



- [[First Variation of Functional]]
- [[Gateaux Derivative and Weak Derivative in Banach Space]]
- [[Euler–Lagrange Equations]]
- [[Principle of Least Action]]

- [[Banach Space]]


- [[Calculus of Variations by Gelfand]] pp 13
- Giaquinta, M. and Hildebrandt, S. (1996) *Calculus of Variations 1. The Lagrangian Formalism*, Grundlehren der Mathematischen Wissenschaften 310. Springer-Verlag, Berlin. pp 16