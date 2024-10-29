---
tags:
  - concept
  - math/differential_geometry
keywords:
  - parallel_transport
  - covariant_derivative_along_curve
topics:
  - differential_geometry
name: Parallel Transport Algebraic Definitions
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Parallel Transport Algebraic Definitions

![[Covariant Derivative Along a Curve#^3107a5]]

>[!important] Definition
>Let $\mathcal{M}$ be a smooth manifold and $\gamma: I \to \mathcal{M}$ is a parameterized curve on $\mathcal{M}$.
>
>For each $t_0, t_1 \in I$, we define a map 
>$$
> \begin{align}
> P^{\gamma}_{t_0, t_1}: T_{\gamma(t_0)}\mathcal{M} \rightarrow T_{\gamma(t_1)}\mathcal{M},  
> \end{align}
>$$
>called the **parallel transport map**, by setting 
>$$
> \begin{align*}
> P^{\gamma}_{t_0, t_1}(v) &= V(t_1), \quad \forall v \in T_{\gamma(t_0)}\mathcal{M}
> \end{align*}
>$$  
>where $V$ is the **parallel transport** *of* $v$ *along* $\gamma$. 
> 
>
>- This map is **linear**, because the *equation of parallelism* is *linear*. 
>- It is in fact an **isomorphism**, because $$P^{\gamma}_{t_1, t_0}$$ is an **inverse** for it.
> 

^6db768

- [[Linear Map]]
- [[Linear Isomorphism]]
- [[Parameterized Curve on Manifold]]
- [[Smooth Manifold]]

![[parallel_transport_along_curve.png]]

### Parallel Transport along Piecewise-Smooth Curve

>[!important] Definition
>Given an *admissible curve* $\gamma: [a, b] \rightarrow \mathcal{M}$, a map $$V: [a, b] \rightarrow T\mathcal{M}$$ such that $$V(t) \in T_{\gamma(t)}\mathcal{M}$$ for each $t$ is called  a **piecewise smooth vector field** *along* $\gamma$ if 
>- $V$ is *continuous* 
>- and there is an *admissible partition* $(a_0 \,{,}\ldots{,}\, a_k)$ for $\gamma$ such that $V$ is *smooth* on each subinterval $[a_{i-1}, a_i]$. 
>	- We will call any such partition an **admissible partition** for $V$. 
>
>A *piecewise smooth vector field* $V$ *along* $\gamma$ is said to be **parallel along** $\gamma$ if $$D_t(V) = 0$$ wherever $V$ is smooth.

- [[Covariant Derivative from Parallel Transport]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field Along a Curve]]


>[!info]
>Given the **parallel transport map** $P^{\gamma}_{t_{0}, t}$, the map $V$ can be defined as 
>$$
>V(t) = P^{\gamma}_{t_{0}, t}(V(t_{0}))
>$$


### Parallel Frame along the Curve

>[!important] Definition
>Given any *basis* $$\{b_1 \,{,}\ldots{,}\,b_n\} \subset T_{\gamma(t_0)}\mathcal{M},$$ we can *parallel transport* the vectors $b_i$ *along* $\gamma$, thus obtaining an **$n$-tuple** of **parallel vector fields** $$(E_1 \,{,}\ldots{,}\, E_n)$$  **along** $\gamma$. i.e. $$(E_{i})_{\gamma(t)} = P_{t_{0}, t}^{\gamma}(b_{i}), \quad t\in I, \; i=1\,{,}\ldots{,}\,n$$
>- Because each parallel transport map is an *isomorphism*,  the vectors $(E_i(t))$ *form a basis* for $T_{\gamma(t)}\mathcal{M}$ at each point $\gamma(t)$.
>
>Such an *$n$-tuple* of vector fields along $\gamma$ is called a **parallel frame** *along* $\gamma$.

^1c955c

- [[Local and Global Frame for Tangent Bundle]]
- [[Basis of Vector Space]]

![[parallel_orthonormal_frame.png]]


### Parallel Transport Determines the Covariant Derivative

![[Covariant Derivative from Parallel Transport#^76a0d0]]

- [[Covariant Derivative from Parallel Transport]]

### Parallel Transport Determines the Connection

![[Covariant Derivative from Parallel Transport#^51023f]]




## Explanation





![[para_transp3.png]]





## Covariant Derivative from Parallel Transport

- [[Covariant Derivative from Parallel Transport]]





-----------
##  Recommended Notes and References


- [[Parallel Transport of Tensor Field along Curve]]
- [[Covariant Derivative from Parallel Transport]]

- [[Tensor Field on Manifold]]
- [[Section of Vector Bundle]]
- [[Integral Curve of Vector Field]]

- [[Velocity of Smooth Curves]]

- [[Smooth Map between Euclidean Spaces]]
- [[Smooth Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Space of all Smooth Tensor Fields on a Manifold]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Tangent Bundle]]
- [[Vector Bundle]]



- [[Introduction to Riemannian Manifolds by Lee]]