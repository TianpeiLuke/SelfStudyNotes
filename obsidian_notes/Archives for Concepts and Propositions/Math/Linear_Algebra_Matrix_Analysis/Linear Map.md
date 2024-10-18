---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - linear_map
topics:
  - linear_algebra
  - functional_analysis
name: Linear Map
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Linear Map

>[!important] Definition
>Let $V$ and $W$ be vector spaces over the same field $F$,  $\varphi: V \to W$ is a **linear map** if it preserve *the linear operations*, i.e.
> 
> - **Additivity**: preservation of *vector addition operation*
>$$
>\begin{align*}
>\varphi(x + y) &= \varphi(x) + \varphi(y), \quad \forall x, y \in V\\
> \end{align*}
>$$
> 
> - **Homogeneity**: preservation of *scalar product operation*
>$$
>\begin{align*}
>\varphi(\lambda x) &= \lambda \varphi(x), \quad \forall \lambda \in F, x\in V 
> \end{align*}
>$$

^ece3c6

- [[Vector Space over a Field]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Bounded Linear Functional]]

>[!info]
>Sometimes a linear map $\varphi$ is called a **linear operator.**

## Explanation

>[!info]
>- The vector addition **within** $\varphi$ is with respect to the definition in domain vector space $V$; 
>- The vector addition **outside** $\varphi$ is with respect to the definition in co-domain vector space $W$;  
>$$
>\varphi(x +_{V} y) = \varphi(x) +_{W} \varphi(y)
>$$  




-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]