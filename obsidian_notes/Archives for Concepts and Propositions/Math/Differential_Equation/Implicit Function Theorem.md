---
tags:
  - concept
  - math/differential_equation
  - math/real_analysis
keywords:
  - implicit_function_theorem
topics:
  - differential_equation
  - real_analysis
name: Implicit Function Theorem
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Implicit Function Theorem

>[!important] Implicit Function Theorem
>Let $f: E\subset \mathbb{R}^{n+m} \to \mathbb{R}^{n}$ be a **continuous differentiable function** on an open subset $E$, such that $$f(x_{0}, y_{0}) = 0$$ for **some point** $(x_{0}, y_{0})\in E$ 
>- Let $$A := \frac{ \partial f}{ \partial (x, y) }(x_{0}, y_{0})  \in \mathbb{R}^{n\times (n+m)}.$$ Note that $$df = A\left[dx, dy\right]^{T} = A_{x}dx + A_{y}dy$$
>- Assume that $$A_{x} := \frac{ \partial f}{ \partial x } $$ is **invertible**
>
>Then there **exists open sets** $U \subset \mathbb{R}^{n+m}$ and $W \subset \mathbb{R}^{m}$, with $(x_{0}, y_{0}) \in U$ and $y_{0}\in W$, such that the following statements are **true**:
>- For **every** $y\in W$,  there **exists a unique** $x$ such that $$(x,y)\in U, \quad \text{ and }\quad f(x, y) = 0$$
>	- In other word, we can *define a function* $g: y \mapsto x$.
>- If there exists some $g$ such that $x$ is defined as $$x = g(y).$$ Then 
>	- $g: W \to \mathbb{R}^{n}$ is a **continuous differentiable** function from $W$ into $\mathbb{R}^{n}$, 
>	- $$g(y_{0}) = x_{0}.$$
>	- The equation $$f(g(y), y) = 0,\quad \forall y\in W$$
>	- The **first-order derivative** of $g$ is given by $$\frac{dg}{dy}(y_{0}) = -\left(A_{x}\right)^{-1}A_{y} := -\left(\frac{ \partial f}{ \partial x } \right)^{-1}\,\frac{ \partial f}{ \partial y}.$$

- [[Differential of a Smooth Map at Point]]
- [[Jacobian Matrix and Jacobian Determinant]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Smooth Map between Euclidean Spaces]]
- [[Space of Continuous Differentiable Functions]]
- [[Principles of Mathematical Analysis by Rudin]] pp 224


## Explanation






-----------
##  Recommended Notes and References

- [[Stable Manifold]]
- [[Smooth Manifold]]
- [[Smooth Map between Euclidean Spaces]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]

- [[Ordinary Differential Equations]]
- [[Inverse Function Theorem]]

- [[Principles of Mathematical Analysis by Rudin]] pp 224
- [[Ordinary Differential Equations by Chicone]] pp 50
- [[Optimization by Vector Space Methods by Luenberger]] pp 187, 266
