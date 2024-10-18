---
tags:
  - concept
  - math/differential_equation
  - math/stochastic_process
keywords:
  - generator_sde
  - infinitesimal_generator
  - stochastic_differential_equations
topics:
  - differential_equation
  - stochastic_process
name: Generator of Stochastic Differential Equation
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Infinitesimal Generator of Stochastic Differential Equation


>[!important] Definition
>Let $(X_{t})$ be a *(time-homogeneous) Itô Process*.
>
>The **(infinitesimal) generator** $\mathcal{A}$ of $X_{t}$ is a linear operator $\mathcal{A}: \mathcal{D}_{\mathcal{A}}(x) \to \mathcal{D}_{\mathcal{A}}(x)$ defined by 
>$$
>\begin{align*}
>\left( \mathcal{A}f \right)(x) &:= \lim_{ t \to 0_{+} }   \frac{\mathbb{E}\left[ f(X_{t}) | X_{0} =x \right] - f(x)}{t}.
>\end{align*}
>$$
>
>Denote $\mathcal{D}_{\mathcal{A}}$ be the space of all functions  $f: \mathbb{R}^n \to \mathbb{R}$ that *the limit exists for all $x\in \mathbb{R}^n$.*

^8f9111

- [[Infinitesimal Generator of Markov Process]]
- [[Stochastic Differential Equations]]
- [[Itô Process]]
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media pp 124



### Generator for Time Homogeneous Diffusion Process

>[!important] Proposition
>Let $(X_{t})$ be a $n$-dimensional *time-homogeneous Itô Process* satisfying the SDE 
>$$
>dX_{t} = b(X_{t})\,dt + A(X_{t})\,dW,
>$$
>where $b = (b^1 \,{,}\ldots{,}\,b^n)$, $A = [a^{i,j}]_{n \times m}$ and $(W_{t})$ is an $m$-dimensional Wiener process.
>
>If $f \in \mathcal{C}_{0}^2(\mathbb{R}^n)$, then $f\in \mathcal{D}_{\mathcal{A}}$ and **(infinitesimal) generator** of $X_{t}$ is
>$$
>(\mathcal{A}f) := Lf = b^i\frac{ \partial  }{ \partial x^i }f + c^{i,j}\frac{ \partial^2  }{ \partial x^i\,x^{j} }f
>$$
>where the **partial differential operator** is
>$$
>\begin{align*}
>L &:=  b^i\frac{ \partial  }{ \partial x^i } + c^{i,j}\frac{ \partial^2  }{ \partial x^i\,x^{j} }
>\end{align*} 
>$$ 
>and $$c^{i,j} := \frac{1}{2} \sum_{k=1}^{m} a^{i,k}a^{j,k}.$$
>
>Here we used the **Einstein summation convention** for the vector field.

^ee7d61

- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media pp 126
- [[Positive Semidefinite Operator]]
- [[Time Homogeneous Diffusion and SDE]]
- [[Einstein Summation Convention]]
- [[Partial Differential Equations]]

>[!important] Definition
>The **partial differential operator** 
>$$
>\begin{align*}
>L_{t} &:= \sum_{i}^{n} b^i(x, t)\frac{ \partial  }{ \partial x^i } + \sum_{i,j = 1}^{n}c^{i,j}(x, t)\frac{ \partial^2  }{ \partial x^i\,x^{j} }
>\end{align*} 
>$$ 
>where $$c^{i,j} := \frac{1}{2} \sum_{k=1}^{m} a^{i,k}a^{j,k}$$ is called the **generator** associated with the *stochastic differential equation*
>$$
>dX_{t} = b(X_{t}, t)\,dt + A(X_{t}, t)\,dW.
>$$

^1bd4b1

- [[Introduction to Stochastic Differential Equations by Evans]] pp 115
- [[Positive Semidefinite Operator]]




## Explanation

>[!info]
>The generator $L$ is a (possibly degenerate) **elliptic second-order linear partial differential operator**.

- [[Second-Order Linear Partial Differential Equations]]
- [[Second-Order Elliptic Equation]]

>[!important]
>The **infinitesimal generator** of *SDE* provides a *probabilistic interpretation* of the solution of **PDE**.



>[!important]
>Following [[Itô Chain Rule and Itô Formula]], we can formulate the differential of function $f(X_{t}, t)$ of the *time-homogeneous diffusion process* $(X_{t})$  as
>$$
>\begin{align*}
> d\,f(X_{t}, t) = \left( \frac{ \partial}{ \partial t }f + L\,f  \right)\,dt + \nabla f \cdot A\,dW
>\end{align*}
>$$
>where $$\nabla f = \left( \frac{ \partial}{ \partial x^1}f \,{,}\ldots{,}\,  \frac{ \partial}{ \partial x^n}f\right)$$ is the **gradient** of function and $$\nabla f \cdot A\,dW = \sum_{i=1}^{n}\sum_{j=1}^{m}\,\left( \frac{ \partial f}{ \partial x^i}\, \right)\,a^{i,j}\,W_{j}.$$
>
>The expectation is 
>$$
> \mathbb{E}\left[ f(X_{t}, t) \right] - \mathbb{E}\left[ f(X_{0}, 0) \right] = \int_{0}^{t}\left( \frac{ \partial}{ \partial t }f + L\,f  \right)\,ds
>$$

- [[Gradient of Smooth Map]]
- [[Time Homogeneous Diffusion and SDE]]
- [[Partial Differential Equations]]

## Generator of Brownian Motion

- [[Infinitesimal Generator of Brownian Motion and Laplacian]]



-----------
##  Recommended Notes and References

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Infinitesimal Generator of Markov Process]]

- [[Time Homogeneous Diffusion and SDE]]
- [[Stochastic Differential Equations]]
- [[Stochastic Process]]
- [[Brownian Motion Wiener Process]]

- [[Partial Differential Equations]]

- [[Fourier Series and Fourier Transform]]

- [[Vector Field on Manifold]]
- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]


- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media
- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Introduction to Stochastic Differential Equations by Evans]]
- Wikipedia [Fokker-Planck_equation](https://en.wikipedia.org/wiki/Fokker%E2%80%93Planck_equation)