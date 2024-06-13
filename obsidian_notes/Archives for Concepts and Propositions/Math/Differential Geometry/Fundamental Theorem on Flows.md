---
tags:
  - concept
  - math/differential_geometry
keywords:
  - fundamental_theorem_on_flow
topics:
  - differential_geometry
name: Fundamental Theorem on Flows
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Fundamental Theorem on Flows

>[!important] Fundamental Theorem on Flows
>Let $V$ be a **smooth vector field** on a smooth manifold $M$. 
>
>There is a **unique** **smooth** **maximal flow** $$\theta: \mathfrak{D} \rightarrow M$$
> whose **infinitesimal generator** is $V$. 
> 
> This flow has the following *properties*:
>
>- For each $p \in M$, the curve $$\theta^{(p)}: \mathfrak{D}^{(p)} \rightarrow M$$ is the **unique maximal integral curve** of $V$ *starting at* $p$.
>- If $s \in \mathfrak{D}^{(p)}$,  then $$\mathfrak{D}^{(\theta(s, p))}$$ is the **interval** $$\mathfrak{D}^{(p)} - s = \set{t - s: t \in \mathfrak{D}^{(p)}}.$$
>- For each $t \in \mathbb{R}$, 
>	- the set $M_t$ is **open** in $M$; and 
>	- $\theta_t: M_t \rightarrow M_{-t}$ is a **diffeomorphism** with **inverse flow** $\theta_{-t}$.
>

- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Maximal Integral Curve of Vector Field]]
- [[Integral Curve of Vector Field]]

## Explanation

>[!info]
>This shows that there exists an *one-to-one correspondence* between **smooth vector field** $V$ and a **smooth local flow** $\theta$ on $M$ so that
>- $V$ is the *infinitesimal generator* of $\theta$
>- $\theta^{(p)}$ is the *integral curve* of $V$.


## Corollary








-----------
##  Recommended Notes and References

- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Maximal Integral Curve of Vector Field]]
- [[Integral Curve of Vector Field]]



- [[Global Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]