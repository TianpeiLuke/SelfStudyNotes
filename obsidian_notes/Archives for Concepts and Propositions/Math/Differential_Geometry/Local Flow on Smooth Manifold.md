---
tags:
  - concept
  - math/differential_geometry
keywords:
  - local_flow_smooth_manifold
topics:
  - differential_geometry
name: Local Flow on Smooth Manifold
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Local Flow on Smooth Manifold

>[!info]
>We have seen that *__every smooth global flow__ gives rise to a __smooth vector field__* whose *integral curves* are precisely *the curves defined by the flow*. 

- [[Vector Field as Infinitesimal Generator of Global Flow]]

>[!important]
>**Conversely**, however, it is **not true** that every smooth vector field is the infinitesimal generator of a smooth global flow.

>[!important] Definition
>If $M$ is a manifold, a **flow domain** for $M$ is an *open subset* $\mathfrak{D} \subseteq \mathbb{R} \times M$ with the *property* that 
>- for each $p \in M$, the set $$\mathfrak{D}^{(p)} = \set{t \in \mathbb{R}: (t, p) \in \mathfrak{D}}$$ is an **open interval** *containing $0$*.

![[flow_domain.png]]

>[!important] Definition
> A **flow** on $M$ is a *continuous map* $$\theta: \mathfrak{D} \rightarrow M,$$ where  $\mathfrak{D} \subseteq \mathbb{R} \times M$ is a *flow domain*, that satisfies the following **group laws**:
>$$  
> \begin{align}
> &\theta(0, p) =p, \quad \forall p \in M  \\
> &\theta(t, \theta(s, p)) = \theta(t+s, p), \quad \forall s \in \mathfrak{D}^{(p)}, \; t \in \mathfrak{D}^{(\theta(s, p))},\; (\text{i.e. }t+s \in \mathfrak{D}^{(p)})  
> \end{align}
>$$  

- [[Topological Group Action]]
- [[Group]]

![[local_flow.png]]

>[!info]
>We sometimes call $\theta$ a **local flow** to distinguish it from a *global flow* as defined earlier. 
>
>The unwieldy term **local one-parameter group action** is also used.

- [[Global Flow on Smooth Manifold]]


## Explanation





## Fundamental Theorem on Flows

- [[Fundamental Theorem on Flows]]
- [[Local Flow on Smooth Manifold]]
- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Maximal Integral Curve of Vector Field]]

## Naturality of Local Flow under Smooth Transformation

>[!important] Proposition
>Suppose $M$ and $N$ are smooth manifolds, $F: M \rightarrow N$ is a *smooth map*,  $X \in \mathfrak{X}(M)$, and $Y \in \mathfrak{X}(N)$.  
>
>Let $\theta$ be the **(local) flow** *of* $X$ and $\eta$ the **(local) flow** *of* $Y$. 
>
>If $X$ and $Y$ are **$F$-related**, then for each $t \in \mathbb{R}$,  
>- $$F(M_t) \subseteq N_t$$ and 
>- $$\eta_t \circ F = F \circ \theta_t$$ on $M_t$. That is, the following diagram commutes
>$$
>\begin{CD}
>     M_t   @>F>>   N_t \\
>     @V \theta_t VV   @VV\eta_t V \\
>     M_{-t}  @>F>>   N_{-t}
>\end{CD}
>$$ 


- [[Smooth Maps on Space of Vector Fields]]
- [[Local Flow on Smooth Manifold]]

>[!important] Corollary
> Let $F: M \rightarrow N$ be a **diffeomorphism**. 
> 
> If $X \in \mathfrak{X}(M)$ and $\theta$ is the **flow** of $X$, then **the flow of pushforward $F_{*}X$** is $$\eta_t =   F \circ \theta_t \circ F^{-1},$$ with domain $$N_t = F(M_t)$$ for each $t \in \mathbb{R}$. 

- [[Pushforward of Vector Fields]]


-----------
##  Recommended Notes and References

- [[Fundamental Theorem on Flows]]

- [[Integral Curve of Vector Field]]
- [[Global Flow on Smooth Manifold]]


- [[Topological Group Action]]
- [[Orbit under Topological Group Actions]]
- [[Group]]