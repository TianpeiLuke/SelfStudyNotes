---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_vector_fields
  - global_flow_smooth_manifold
  - generator_flow
topics:
  - differential_geometry
name: Vector Field as Infinitesimal Generator of Global Flow
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Vector Field as Infinitesimal Generator of Global Flow

>[!important] Definition
>If $\theta: \mathbb{R} \times M \rightarrow M$ is a smooth *global flow*, for each $p \in M$ we define a **tangent vector** $V_p \in T_pM$ by
>$$
> \begin{align*}
> V_p &=  (\theta^{(p)})'(0) = d\theta^{(p)}\left(\frac{d}{dt}\Bigr|_{t=0}\right).
> \end{align*} 
>$$ 
>
>The assignment $p \mapsto V_p$ is a *(rough) vector field* on $M$; which is called **the infinitesimal generator** of **the global flow $\theta$**.

- [[Global Flow on Smooth Manifold]]
- [[Smooth Vector Field on Manifold]]

## Explanation



## Properties


>[!info]
>$V$ is the **infinitesimal generator of the flow** $\theta$ if and only if $\theta$ is the **integral curve** of $V$.

>[!important] Proposition
>Let $\theta: \mathbb{R} \times M \rightarrow M$ be a **smooth global flow** on a smooth manifold $M$. 
>
>- The **infinitesimal generator** $V$ of $\theta$ is a **smooth vector field** on $M$; and 
>- each *curve* $\theta^{(p)}$ is **an integral curve** of $V$.

- [[Smooth Vector Field on Manifold]]
- [[Integral Curve of Vector Field]]




>[!info]
>This means that $$(\theta^{(p)})'(t) = V_{\theta^{(p)}(t)}$$ for all $p \in M$ and all $t \in \mathbb{R}$.
>

- [[Global Flow on Smooth Manifold]]


-----------
##  Recommended Notes and References


- [[Global Flow on Smooth Manifold]]
- [[Integral Curve of Vector Field]]

- [[Tangent Vector as Velocity of Smooth Curves]]
- [[Smooth Vector Field on Manifold]]



- [[Introduction to Smooth Manifolds by Lee]]