---
tags:
  - concept
  - math/differential_equation
  - math/stochastic_process
keywords:
  - generator_sde
  - brownian_motion
topics:
  - differential_equation
  - stochastic_process
name: Infinitesimal Generator of Brownian Motion and Laplacian
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Infinitesimal Generator of Brownian Motion and Laplacian

![[Infinitesimal Generator of Stochastic Differential Equation#^ee7d61]]


>[!important] Definition
>Let $b \equiv 0$ and $A = I$, we have the stochastic equation
>$$
>dX_{t} = dW_{t}
>$$
>So the **generator** of $W_t$ is
>$$
>\mathcal{A}f := \frac{1}{2}\sum_{i=1}^{n}\frac{ \partial^2 }{ \partial (x^i)^2 }f 
>$$ 
>i.e. it is the **Laplace partial differential equation** 
>$$
>\mathcal{A} := \frac{1}{2} \Delta
>$$
>where $\Delta$ is the **Laplacian operator**.

^143824

- [[Laplace Equation and Poisson Equation]]

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Brownian Motion Wiener Process]]

- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Vector Field on Manifold]]





## Explanation





-----------
##  Recommended Notes and References


- [[Stochastic Differential Equations]]

- [[Ito Stochastic Integration]]
- [[Stochastic Process]]
- [[Brownian Motion Wiener Process]]


- [[Introduction to Stochastic Calculus by Klebaner]]
- Wikipedia [Fokker-Planck_equation](https://en.wikipedia.org/wiki/Fokker%E2%80%93Planck_equation)