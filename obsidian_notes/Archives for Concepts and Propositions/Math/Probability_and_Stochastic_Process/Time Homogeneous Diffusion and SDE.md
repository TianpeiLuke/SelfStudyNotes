---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_process
  - time_homogeneous_sde
topics:
  - stochastic_process
name: Time Homogeneous Diffusion and SDE
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Time Homogeneous Diffusion and SDE

![[Stochastic Differential#^222620]]

>[!important] Definition
>An *Itô process (Itô diffusion)* $(X_{t}, t\in [0,T])$ is called **time-homogeneous** if it satisfies the stochastic differential equation:
>$$
>dX_{t} = b(X_{t})\,dt + A(X_{t})\,dW
>$$
>where $b$ and $A$ satisfies the **Lipschitz conditions**
>$$\lVert b(x) - b(y) \rVert \le L\lVert x - y \rVert$$ and  $$\lVert A(x) - A(y) \rVert \le L\lVert x - y \rVert$$ for all $t\in [0,T]$, $x, y \in \mathbb{R}^n$

^375885

- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]
- [[Lipschitz Continuous Function]]

>[!important] Definition
>A *homogeneous linear SDE* is **time-homogeneous** if both drift coefficient and diffusion coefficient *does not depend on time $t$* explicitly
>$$
>dX_{t} = b(X_{t})\,dt + A(X_{t})\,dW
>$$

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 156


## Expansion

>[!important]
>A time-homogeneous differential equation is a **global vector field** since its coordinate functions is **independent** with the *position* (i.e. the time $t$) of the vector field

- [[Vector Field on Manifold]]

## Property



## Stationary Process

>[!important] Theorem
>Assume that there is a **unique weak solution** to the *time-homogeneous SDE* 
>$$
>dX_{t} = b(X_{t})\,dt + A(X_{t})\,dW.
>$$
>
>Then the **transition probability function** of the solution $$P(y, t, x, s) =P(y, t − s, x, 0)$$ depends **only** on $t − s$.
>
>In other word, the weak solution of above SDE is a **stationary process**. 


- [[Markov Transition Kernel and Transition Function]]
- [[Weak Solution to Stochastic Differential Equation]]

## Generator 

>[!important]
>Following [[Ito Chain Rule and Ito Formula]], we can formulate the differential of function $f(X_{t}, t)$ of the *time-homogeneous Ito process* $(X_{t})$  as
>$$
>\begin{align*}
> d\,f(X_{t}, t) = \left( \frac{ \partial}{ \partial t }f + L\,f  \right)\,dt + \nabla f \cdot A\,dW
>\end{align*}
>$$
>where 
>$$
>\begin{align*}
>L &:=  b^i\frac{ \partial  }{ \partial x^i } + c^{i,j}\frac{ \partial^2  }{ \partial x^i\,x^{j} }
>\end{align*} 
>$$ 
>and
>$$\nabla f = \left( \frac{ \partial}{ \partial x^1}f \,{,}\ldots{,}\,  \frac{ \partial}{ \partial x^n}f\right)$$ is the **gradient** of function and $$\nabla f \cdot A\,dW = \sum_{i=1}^{n}\sum_{j=1}^{m}\,\left( \frac{ \partial f}{ \partial x^i}\, \right)\,a^{i,j}\,W_{j}.$$
>
>The expectation is 
>$$
> \mathbb{E}\left[ f(X_{t}, t) \right] - \mathbb{E}\left[ f(X_{0}, 0) \right] = \int_{0}^{t}\left( \frac{ \partial}{ \partial t }f + L\,f  \right)\,ds
>$$

- [[Infinitesimal Generator of Stochastic Differential Equation]]

## Forward and Backward Equation


- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]




-----------
##  Recommended Notes and References

- [[Ito Process]]

- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Ito Stochastic Integration]]
- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]
- [[Brownian Motion Wiener Process]]

- Wikipedia [Itô Process](https://en.wikipedia.org/wiki/It%C3%B4_calculus)
- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]