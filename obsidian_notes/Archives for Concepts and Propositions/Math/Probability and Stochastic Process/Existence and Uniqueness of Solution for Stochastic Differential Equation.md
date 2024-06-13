---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - stochastic_differential_equations
  - existence_uniqueness_solution
topics:
  - differential_equation
  - stochastic_process
name: Existence and Uniqueness of Solution for Stochastic Differential Equation
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Existence and Uniqueness of Solution for Stochastic Differential Equation

>[!important] Theorem
>Suppose that $b: \mathbb{R}^n \times [0,T] \to \mathbb{R}^n$ and $A: \mathbb{R}^n \times [0,T] \to \mathbb{M}^{n\times m}$ are both *continuous function* and satisfies the following conditions:
>- **Uniformly Lipschitz** with respect to $x$: $$\lVert b(x, t) - b(y, t) \rVert \le L\lVert x - y \rVert$$ and  $$\lVert A(x, t) - A(y, t) \rVert \le L\lVert x - y \rVert$$ for all $t\in [0,T]$, $x, y \in \mathbb{R}^n$
>- **Bounded**: $$\lVert b(x, t) \rVert  \le L(1 + \lVert x \rVert )$$ and $$\lVert A(x, t) \rVert  \le L(1 + \lVert x \rVert )$$ for all $t\in [0,T]$, $x \in \mathbb{R}^n$
>
>for some constant $L$.
>
>Let $X_{0}$ be any $\mathbb{R}^n$-valued *random variable* such that 
>- $X_{0}$ is **square integrable** i.e. $$ \mathbb{E}\left[ \lVert X_{0} \rVert^2 \right] < \infty$$ and
>- $X_{0}$ is **independent with** $$\mathscr{F}_{0}^{+} := \sigma\left( W_{t} - W_{0},\; t >0 \right)$$ where $(W_{t})$ is a $m$-dimensional **Brownian motion**
>  
>Then there exists a **unique solution** $X \in \mathbb{L}_{n}^2(0,T)$ of the *stochastic differential equation*: 
>$$
>\left\{ 
>\begin{align*}
>dX(t) &= b\left( X(t), t\right)\,dt + A\left( X(t), t \right)\,dW, \quad t\in [0,T]\\
>X(0)&= X_{0}.
>\end{align*}
>\right.
>$$


- [[Stochastic Differential Equations]]
- [[Lipschitz Continuous Function]]


## Explanation

>[!important]
>The **uniqueness** of $X\in \mathbb{L}_{n}^2(0,T)$ is defined by the equality of **sample path** **almost surely**.
>$$
> \hat{X}(\omega, \cdot) = X(\omega, \cdot), \; \omega\text{-a.s.}
>$$
>or, equivalently,
>$$
>\mathcal{P}\left( \bigcap_{t\in [0,T]}\left[\hat{X}(\cdot, t) = X(\cdot, t)  \right] \right) = 1.
>$$






-----------
##  Recommended Notes and References

- [[Stochastic Differential Equations]]

- [[Lipschitz Continuous Function]]
- [[Contraction Function]]
- [[Contraction Map Principle]]
- [[Borel-Cantelli Lemma]]


- [[Introduction to Stochastic Differential Equations by Evans]]