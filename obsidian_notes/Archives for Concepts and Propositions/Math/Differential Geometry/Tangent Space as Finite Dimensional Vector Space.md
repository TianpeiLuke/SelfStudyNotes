---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_space
topics:
  - differential_geometry
name: Tangent Space as Vector Space
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Tangent Space $T_{p}M$ as vector space

>[!important] Proposition
>If $M$ is an *$n$-dimensional smooth manifold*, then for each $p \in \mathcal{M}$ the tangent space $T_{p}\mathcal{M}$ is an **$n$-dimensional vector space.**


>[!important] Proposition
>Suppose $\mathcal{M}$ is an $n$-dimensional smooth manifold *with boundary*. 
>
>For each $p \in \mathcal{M}$, $T_{p}\mathcal{M}$ is an **$n$-dimensional vector space.**

- [[Coordinate Representation of Tangent Vector]]
- [[Vector Space over a Field]]

>[!important] Proposition
>Suppose $V$ is a finite-dimensional vector space with its standard smooth manifold structure. 
>
>For each point $a \in V$, the map $v \rightarrow D_v\big|_a$ defined by 
> $$
> \begin{align}
> D_v|_a(f) &= D_{v}(f(a)) = \frac{d}{dt}\Big|_{t=0}f(a + t\,v).
> \end{align}
> $$
> is a **canonical isomorphism** from $V$ to $T_{a}V$, such that for *any linear map* $L: V \rightarrow W$, the following diagram **commutes**:
>$$
>\begin{CD}
>
\end{CD}
>$$
> 
>![[tangent_space_to_vector_space_diagram.png]]
>

 <img src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09V%20%26%26%20%7BT_%7Ba%7DV%7D%20%5C%5C%0A%09%5C%5C%0A%09W%20%26%26%20%7BT_%7BL(a)%7DW%7D%0A%09%5Carrow%5B%22%5Csimeq%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22L%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7BdL_a%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Csimeq%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	V &amp;&amp; {T_{a}V} \\
	\\
	W &amp;&amp; {T_{L(a)}W}
	\arrow[&quot;\simeq&quot;, from=1-1, to=1-3]
	\arrow[&quot;L&quot;', from=1-1, to=3-1]
	\arrow[&quot;{dL_a}&quot;, from=1-3, to=3-3]
	\arrow[&quot;\simeq&quot;', from=3-1, to=3-3]
\end{tikzcd}
" />


- [[Introduction to Smooth Manifolds by Lee]]


## Tangent Space as Space of Free Vectors


>[!info]
>Consider an **affine space** $M$, then $T_{p}M$ at every $p\in M$ are all *parallel* to each other. This vector space $T_{p}M$ is **the vector space of free vectors** that is associated with **affine space** $M$.
>
>This means that for general smooth manifold, the tangent bundle $TM$ serve the role of **the vector space of free vectors**.

- [[Affine Space]]
- [[Parallel Subspaces]]



-----------
##  Recommended Notes and References

- [[Tangent Space Definition and Development]]
- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Vector Space over a Field]]
