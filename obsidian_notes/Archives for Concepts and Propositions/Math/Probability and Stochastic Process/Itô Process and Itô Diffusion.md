---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ito_process
topics:
  - stochastic_process
name: Itô Process
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Process

![[Stochastic Differential#^222620]]

>[!important] Definition
>An **Itô process (Itô diffusion)** $(X_{t}, t\in [0,T])$ is a stochastic process that satisfies the following integral equation
>$$
>X_{t} = X_{s} + \int_{s}^{t}\,F\,du + \int_{s}^{t}\,G\,dW, 
>$$
>where $(W_{t})$ is the *Wiener process*, $F, G\in \mathbb{L}^2([0,T])$ are *progressive measurable* and $0 \le s \le t \le T$. 
>
>An Itô process is the solution of the following *stochastic differential equation*:
>$$
>dX_{t} = F(X_{t}, t)\,dt + G(X_{t}, t)\,dW
>$$

- [[Stochastic Differential]]
- [[Stochastic Differential Equations]]
- [[Itô Stochastic Integration]]
- [[Itô Chain Rule and Itô Formula]]

>[!important] Definition
>An *Itô process (Itô diffusion)* $(X_{t}, t\in [0,T])$ is called **time-homogeneous** if it satisfies the stochastic differential equation:
>$$
>dX_{t} = F(X_{t})\,dt + G(X_{t})\,dW
>$$
>where $F$ and $G$ satisfies the **Lipschitz conditions**
>$$\lVert F(x) - F(y) \rVert \le L\lVert x - y \rVert$$ and  $$\lVert G(x) - G(y) \rVert \le L\lVert x - y \rVert$$ for all $t\in [0,T]$, $x, y \in \mathbb{R}^n$

- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]
- [[Lipschitz Continuous Function]]


## Expansion

>[!important]
>A time-homogeneous differential equation is a **global vector field** since its coordinate functions is **independent** with the *position* (i.e. the time $t$) of the vector field

- [[Vector Field on Manifold]]

## Property

>[!important] Proposition
>Let $(X_{t}, t\in [0,T])$ be an **Itô process**.
>
>Then 
>- $X_{t}$ is **$\mathscr{F}_{t}$-adapted** for $t\in [0,T]$
>- $((X_{t}, \mathscr{F}_{t}), t\in [0,T])$ is a **martingale**.

- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Martingale]]



## Markov Property







-----------
##  Recommended Notes and References


- [[Stochastic Differential]]
- [[Itô Stochastic Integration]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

- Wikipedia [Itô Process](https://en.wikipedia.org/wiki/It%C3%B4_calculus)
- [[Introduction to Stochastic Differential Equations by Evans]]
- [[Introduction to Stochastic Calculus by Klebaner]]