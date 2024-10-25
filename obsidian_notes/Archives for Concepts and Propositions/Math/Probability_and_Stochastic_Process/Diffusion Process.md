---
tags:
  - concept
  - math/stochastic_process
keywords:
  - diffusion_process
topics:
  - stochastic_process
name: Diffusion Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Diffusion Process

>[!important] Definition
>A *continuous time Markov process* $(X_{t})$ with *transition probability* $p(A, t, x, s)$ is called a **diffusion process** if
>- for any $\epsilon >0$ and $t \ge 0$, $x\in \mathcal{X}$, 
>  $$\lim_{ h \to 0_{+} } \frac{1}{h} \int_{|y- x| > \epsilon} p\left(t, x, t+h, dy\right) = 0$$
>- there exists an *$n$-dimensional vector* $b(x,t) \in \mathbb{R}^n$  and an *$n\times n$ matrix* $A(x, t)\in \mathbb{R}^{n \times n}$ such that for any $\epsilon >0$ and $t \ge 0$, $x\in \mathcal{X}$, 
>	- the *mean of infinitesimal conditional increments* $$\lim_{ h \to 0_{+} } \frac{1}{h} \int_{|y- x| < \epsilon} (y^{i} - x^{i})\; p\left(t, x, t+h, dy\right) = b^{i}(x, t)$$ for $1 \le i\le n$,  
>	- the *covariance of infinitesimal conditional increments* $$\lim_{ h \to 0_{+} } \frac{1}{h} \int_{|y- x| < \epsilon} (y^{i} - x^{i})(y^{j} - x^{j})\; p\left(t, x, t+h, dy\right) = A^{i,j}(x, t)$$ for $1 \le i,j\le n$, 
>
>where $b := (b^1 \,{,}\ldots{,}\,b^n)$ and $A := (A^{i,j})$.
>
>The vector $b$ is called **the drift coefficient** and the matrix $A$ is called **the diffusion matrix**, when $n=1$, we call $A$ the **diffusion coefficient**.


- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- Friedman, A. (1975). *Stochastic differential equations and applications*. Vol.1 pp 114


## Expansion

>[!info]
>The definition of diffusion process includes
>1. **approximately smoothness** $$\mathcal{P}(|X_{t+h} - X_{t}| > \epsilon \;|\; X_{t} = x ) = o(h)$$
>2. **increments within infinitesimal time** $X_{t+h} - X_{t}$ has **mean** $b(x,t)$ only depends on the conditioned state and time $(x, t)$.
>3. **increments within infinitesimal time** $X_{t+h} - X_{t}$ has **covariance** $A(x,t)$ only depends on conditioned state and time $(x, t)$.

>[!info]
>A diffusion process $(X_{t})$ satisfies the SDE
>$$
>dX_{t} = b(X_{t}, t)\,dt + A(X_{t}, t)\,dW_{t}
>$$



## Itô Process and Solution of Stochastic Differential Equation

- [[Ito Process]]
- [[Stochastic Differential]]




-----------
##  Recommended Notes and References

- [[Time Homogeneous Diffusion and SDE]]
- [[Stochastic Differential Equations]]


- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

- Wikipedia [Itô Process](https://en.wikipedia.org/wiki/It%C3%B4_calculus)
- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]