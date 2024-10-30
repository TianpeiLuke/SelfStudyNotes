---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_vector_fields
  - local_flow_smooth_manifold
  - generator_flow
topics:
  - differential_geometry
name: Vector Field as Infinitesimal Generator of Local Flow
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Vector Field as Infinitesimal Generator of Local Flow

>[!important] Definition
>If $\theta$ is a *flow*, we define $$\theta_t(p) = \theta^{(p)}(t) = \theta(t, p)$$ whenever $(t, p) \in \mathfrak{D}$, just as for a *global flow*. 
>
>For each $t \in \mathbb{R}$, we also define
>$$
> \begin{align}
> M_t = \set{p \in M: (t, p) \in \mathfrak{D}} 
> \end{align}
>$$  
>so that
>$$
> \begin{align*}
> p \in M_t \iff t \in \mathfrak{D}^{(p)} \iff (t,p) \in \mathfrak{D}.
> \end{align*}
>$$  
>
>If $\theta$ is *smooth*, **the infinitesimal generator of $\theta$** is defined by $$V_p =  (\theta^{(p)})'(0).$$


- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Local Flow on Smooth Manifold]]
- [[Smooth Vector Field on Manifold]]

## Explanation



## Properties


>[!info]
>- $V$ is the **infinitesimal generator of the flow** $\theta$ 
>- then $\theta$ is the **integral curve** of $V$.

>[!important] Proposition
>If $\theta: \mathfrak{D} \rightarrow M$ is a *smooth flow*, then 
>- **the infinitesimal generator** $V$ of $\theta$ is a **smooth vector field**, and 
>- each curve $\theta^{(p)}$ is an **integral curve** of $V$.


- [[Smooth Vector Field on Manifold]]
- [[Integral Curve of Vector Field]]


## Fundamental Theorem on Flows

>[!info]
>Every **vector field** have a **unique maximum flow**, which is also the **maximum integral curve** of that vector field.

![[Fundamental Theorem on Flows#^c359e5]]

- [[Fundamental Theorem on Flows]]



-----------
##  Recommended Notes and References


- [[Vector Field as Infinitesimal Generator of Global Flow]]

- [[Global Flow on Smooth Manifold]]
- [[Integral Curve of Vector Field]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Smooth Vector Field on Manifold]]

- [[Infinitesimal Generator of Markov Process]]
- [[Infinitesimal Generator of Brownian Motion and Laplacian]]


- [[Introduction to Smooth Manifolds by Lee]]