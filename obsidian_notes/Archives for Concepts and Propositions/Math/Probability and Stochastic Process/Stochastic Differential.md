---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - stochastic_differential
topics:
  - stochastic_process
name: Stochastic Differential
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Itô Stochastic Differential

>[!important] Definition
>Let $(X_{t})$ be a real-valued *stochastic process* satisfying the following *integral equation*
>$$
>X_{t} = X_{s} + \int_{s}^{t}\,F\,du + \int_{s}^{t}\,G\,dW, \quad \text{ a.s.}
>$$
>where $(W_{t})$ is the *Wiener process*, $F, G\in \mathbb{L}^2([0,T])$ are *progressive measurable* and $0 \le s \le t \le T$. 
>
>We say that $X$ satisfies the following **stochastic differential** for  $t \in [0,T]$,
>$$
>dX = F\,dt + G\,dW.
>$$

^222620

- [[Itô Process and Diffusion Process]]
- [[Itô Stochastic Integration]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

## Expansion

>[!important]
>The expression 
>$$
>dX = F\,dt + G\,dW
>$$
>is **symbolic**. It is an **abbreviation** of the *integral equation*.
>
>There is *no real meaning* for $dX$, $dt$ as well as $dW$ in its own. Especially, $W$ is a sample path that is **nowhere differentiable**. 

- [[Sample Path of Brownian Motion]]

>[!important]
>We can think of the stochastic differential as a **limit** of the **discrete time model** to *continuous time*
>$$
>X_{t+1} - X_{t} = F_{t} + G_{t}\,\xi_{t}
>$$
>where $(\xi_{t})$ are *i.i.d standard normal distribution* $\mathcal{N}(0,1)$.

>[!important]
>We see that *the stochastic differential* describes the **incremental behavior** of stochastic process across time.
>
>It is an incremental model.




## Generalization

>[!important] Definition
>Let $(X_{t})$ be a $\mathbb{R}^n$-valued *stochastic process* satisfying the following *integral equation*
>$$
>X_{t} = X_{s} + \int_{s}^{t}\,F\,du + \int_{s}^{t}\,G\,dW, \quad \text{ a.s.}
>$$
>where $(W_{t})$ is the $\mathbb{R}^{m}$-*Wiener process*, $F \in \mathbb{L}_{n}^2([0,T])$ and $G\in \mathbb{L}_{n \times m}^2([0,T])$ are *progressive measurable* and $0 \le s \le t \le T$. 
>
>We say that $X$ satisfies the following **stochastic differential** for  $t \in [0,T]$,
>$$
>dX = F\,dt + G\,dW.
>$$
>that is for $i=1 \,{,}\ldots{,}\,n$,
>$$
>dX^{i} = F^{i}\,dt + \sum_{j=1}^{m}\,G^{i,j}\,dW^{j}.
>$$




-----------
##  Recommended Notes and References


- [[Itô Stochastic Integration]]
- [[Itô Stochastic Integration of Step Process]]
- [[Progressively Measurable Stochastic Process]]
- [[Brownian Motion Wiener Process]]

- [[Itô Chain Rule and Itô Formula]]
- [[Itô Product Rule and Stochastic Integration by Parts]]

- [[Introduction to Stochastic Differential Equations by Evans]]