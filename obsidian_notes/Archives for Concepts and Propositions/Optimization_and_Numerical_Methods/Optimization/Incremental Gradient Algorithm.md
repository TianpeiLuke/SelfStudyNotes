---
tags:
  - concept
  - optimization/algorithm
  - online_learning/algorithms
keywords:
  - incremental_gradient_algorithm
topics:
  - optimization/algorithm
name: Incremental Gradient Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Incremental Gradient Algorithm

![[Incremental Algorithm#^b32a9f]]

>[!important] 
>The main update for the **Incremental gradient method** can be described as the following
>- For $k=1,\,2 \,{,}\ldots{,}\,$
>	- *Initialize* $\psi_{0,k} = x_{k}$
>	- For $t=1 \,{,}\ldots{,}\,T$
>		- $$\psi_{t,k} = P_{\mathcal{X}}\left( \psi_{t-1, k} - \alpha_{k}\,\nabla f_{t}(\psi_{t-1, k})\right)$$ where $P_{\mathcal{X}}$ is the **projection operator**
>	- Update $$x_{k+1} = \psi_{T, k}$$

- [[Incremental Algorithm]]
- [[Gradient Projection Method]]


## Explanation

>[!important]
>Note that in the *inner iteration*, each time $t$, only **one component function** $f_{t}$ is used to produce the *gradient direction*.

## Examples

>[!example]
>A typical example of incremental gradient algorithm is the **stochastic gradient decent algorithm** where
>$$
>f_{t}(\theta) := f(x_{t}; \theta)
>$$
>Thus
>- sample $x_{t}$
>- update $$\theta_{t+1} = \theta_{t} - \alpha_{t}\,\nabla f_{t}(\theta) := \theta_{t} - \alpha_{t}\,\nabla_{\theta} f(x_{t}; \theta) $$


- [[Stochastic Gradient Descent Algorithm]]
- [[Online Gradient Decent Algorithm]]
- [[Online Mirror Descent Algorithm]]
- [[Follow-The-Leader Algorithm]]
- [[Follow-The-Regularized-Leader Algorithm]]



-----------
##  Recommended Notes and References


- [[Incremental Algorithm]]
- [[Gradient Descent Algorithm]]

- [[Online Convex Optimization]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 84