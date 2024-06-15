---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_chain_rule
  - ito_formula
topics:
  - stochastic_process
name: Itô Chain Rule and Itô Formula
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Chain Rule and Itô Formula

>[!important] Proposition (Itô Chain Rule)
>Suppose that $X_{t}$ has a *stochastic differential*
>$$
>dX_{t} = F\,dt + G_{t}\,dW_{t},
>$$
>for $F, G\in \mathbb{L}^2(0,T).$
>
>Assume that $u: \mathbb{R} \times [0,T] \to \mathbb{R}$, $u := u(x, t)$, is *continuous* with *continuous derivatives* $$u_{t} := \frac{\partial}{ \partial t }u, \quad u_{x} := \frac{\partial}{ \partial x}u, \quad u_{x x} := \frac{\partial^2}{ \partial x^2 }u.$$
>
>Then $Y_{t} := u(X_{t}\,,\, t)$ has the **stochastic differential equation**
>$$
>\begin{align*}
>du(X_{t}\,,\,t) &= u_{t}(X_{t}\,,\, t)\,dt + u_{x}(X_{t}\,,\, t)\,dX_{t} + \frac{1}{2}\,u_{x x}(X_{t}\,,\, t)\,G_{t}^2\,dt\\
>&= \left( u_{t} + u_{x}F +  \frac{1}{2}\,u_{x x}\,G_{t}^2\right)\,dt + u_{x}\,G_{t}\,dW_{t}.
>\end{align*}
>$$
>We call the above equation **Itô's Chain Rule** or **Itô's Formula**.


- [[Itô Process and Diffusion Process]]
- [[Stochastic Differential]]
- [[Itô Stochastic Integration]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

>[!important]
>The Ito's Chain Rule implies
>$$
>Y_{t} - Y_{s} = \int_{s}^{t}\left(u_{t}(X_{t}\,,\, t)\,+ u_{x}(X_{t}\,,\, t)\, +  \frac{1}{2}\,u_{x x}(X_{t}\,,\, t)\,G_{t}^2\,\right)\,dt +  \int_{s}^{t} u_{x}(X_{t}\,,\, t)\,G_{t}\,dW_{t},
>$$
>*almost surely* $\omega\in \Omega.$


## Generalization

>[!important] Proposition (Itô Chain Rule)
>Suppose that $X_{t}$ has a *stochastic differential*
>$$
>dX^{i}_{t} = F^{i}\,dt + G^{i}_{t}\,dW_{t},
>$$
>for $F^i, G^i\in \mathbb{L}^2(0,T),$  and $i=1 \,{,}\ldots{,}\,n.$
>
>Assume that $u: \mathbb{R}^{n} \times [0,T] \to \mathbb{R}$, $u := u(x, t)$, is *continuous* with *continuous derivatives* $$u_{t} := \frac{\partial}{ \partial t }u, \quad u_{x_{i}} := \frac{\partial}{ \partial x_{i}}u, \quad u_{x_{i} x_{j}} := \frac{\partial^2}{ \partial x_{i} x_{j} }u.$$
>
>Then the **Itô's Chain Rule** or **Itô's Formula** for $Y_{t} := u(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)$ is
>$$
>\begin{align*}
>du(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\,t) &= u_{t}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,dt \\
>&\quad + \sum_{i=1}^{n} u_{x_{i}}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,dX^{i}_{t} \\
>&\quad + \frac{1}{2}\,\sum_{i=1}^{n}\sum_{j=1}^{n}u_{x_{i} x_{j}}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,G^i_{t}\,G^{j}_{t}\,dt
>\end{align*}
>$$


>[!important] Proposition (General Case in $n$-dimensional space)
>Suppose that $X_{t}$ has a *stochastic differential*
>$$
>dX^{i}_{t} = F^{i}\,dt + \sum_{j=1}^{m}G^{i,j}_{t}\,dW^{j}_{t},
>$$
>for $F^i, G^{i,j}\in \mathbb{L}^2(0,T),$  and $i=1 \,{,}\ldots{,}\,n,$ $j=1 \,{,}\ldots{,}\,m.$
>
>Assume that $u: \mathbb{R}^{n} \times [0,T] \to \mathbb{R}$, $u := u(x, t)$, is *continuous* with *continuous derivatives* $$u_{t} := \frac{\partial}{ \partial t }u, \quad u_{x_{i}} := \frac{\partial}{ \partial x_{i}}u, \quad u_{x_{i} x_{j}} := \frac{\partial^2}{ \partial x_{i} x_{j} }u.$$
>
>Then the **Itô's Chain Rule** or **Itô's Formula** for $Y_{t} := u(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)$ is
>$$
>\begin{align*}
>du(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\,t) &= u_{t}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,dt \\
>&\quad + \sum_{i=1}^{n} u_{x_{i}}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,dX^{i}_{t} \\
>&\quad + \frac{1}{2}\,\sum_{i=1}^{n}\sum_{j=1}^{n}u_{x_{i} x_{j}}(\left(X_{t}^1 \,{,}\ldots{,}\, X_{t}^n \right)\,,\, t)\,\sum_{k=1}^{m}G^{i,k}_{t}\,G^{j,k}_{t}\,dt
>\end{align*}
>$$

### Compact Form via Generator

- [[Infinitesimal Generator of Stochastic Differential Equation]]

>[!important] Itô Formula (Generator)
>Let $(X_{t})$ be a $n$-dimensional *time-homogeneous Itô Process* satisfying the SDE 
>$$
>dX_{t} = b(X_{t})\,dt + A(X_{t})\,dW,
>$$
>where $b = (b^1 \,{,}\ldots{,}\,b^n)$, $A = [a^{i,j}]_{n \times m}$ and $(W_{t})$ is an $m$-dimensional Wiener process.
>
>And let $L$ be the **(infinitesimal) generator** of $X_{t}$,  
>$$
>Lu: = b^i\frac{ \partial  }{ \partial x^i }u + c^{i,j}\frac{ \partial^2  }{ \partial x^i\,x^{j} }u
>$$
>where $\boldsymbol{C} = [c^{i,j}] = \boldsymbol{A}^T\boldsymbol{A}.$ Ant it follows the [[Einstein Summation Convention]].
>
>For any function $u(x, t)$ that is *twice continuously differentiable* at $x$ and *once continuous differentiable* at $t$,  $X_{t}$ satisfies the following SDE 
>$$
>du\left(X_{t}, t\right) = \left(L\,u + \frac{ \partial  }{ \partial t }u\right) (X_{t}, t)\, dt +   \left(\nabla u(X_{t}, t) \right)^T\,\boldsymbol{A}(X_{t}, t)\,dW_{t}
>$$



## Expansion

>[!info]
>For each $\omega\in \Omega$, the *sample path* is *continuous* for $$u_{t}(X_{t}\,,\, t)\,, \quad  u_{x}(X_{t}\,,\, t)\,, \quad u_{x x}(X_{t}\,,\, t).$$

>[!important]
>As simpler form of the chain rule is
>$$
>d\,u\left( X_{t}, t \right) = u_{t}dt + u_{x_{i}}dX^i + \frac{1}{2}u_{x_{i} x_{j}}dX^{i}\,dX^{j}
>$$
>then use the following formula
>$$
>\begin{align*}
>(dt)^2 &= 0\\
>dt\,dW^k &=0, \quad k=1 \,{,}\ldots{,}\,m\\
>dW^k\,dW^l &= \delta_{k,l}\,dt, \quad k,l=1 \,{,}\ldots{,}\,m
>\end{align*}
>$$



## Proof

- [[Itô Product Rule and Stochastic Integration by Parts]]




-----------
##  Recommended Notes and References

- [[Stochastic Integral of Brownian Motion]]
- [[Itô Product Rule and Stochastic Integration by Parts]]

- [[Itô Stochastic Integration]]
- [[Itô Stochastic Integration of Step Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]



- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]