---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_map_on_vector_fields
topics:
  - differential_geometry
name: Smooth Maps on Space of Vector Fields
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Smooth Maps on Space of Vector Fields

>[!info] 
>If $F: M \rightarrow N$ is a **smooth map** and $X$ is a **vector field** on $M$, then for each point $p \in M$, we obtain a **vector** $$dF_{p}(X_p) \in T_{F(p)}N$$ by applying the **differential** of $F$ to $X_p$. 
>
>Can we map a vector field to a vector field via differential $dF_{p}$ ? Unfortunately, **this does not in general true.** 


>[!important] Definition
>Suppose $F: M \rightarrow N$ is **smooth** and $X$ is a **vector field** on $M$,  and suppose there happens to be a  **vector field** $Y$ on $N$ with the property that for each $p \in M$,
>$$
> \begin{align*}
> dF_{p}(X_p) &= Y_{F(p)}.
> \end{align*}
>$$ 
> In this case, we say *the vector fields* $X$ *and* $Y$ are **$F$-related.**

- [[Differential of a Smooth Map at Point]]
- [[Smooth Map between Euclidean Spaces]]
- [[Smooth Vector Field on Manifold]]




## Explanation

>[!important] Proposition
>Suppose $F: M \rightarrow N$ is a *smooth map* between manifolds with or without boundary, $X \in \mathfrak{X}(M)$, and $Y \in \mathfrak{X}(N)$. 
>
>Then $X$ and $Y$ are **$F$-related** *if and only if* for *every smooth* real-valued *function* $f$ defined on an open subset of $N$,
>$$
> \begin{align}
> X(f \circ F) &= (Yf) \circ F 
> \end{align}
>$$ 

- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Space of all Smooth Vector Fields on a Manifold]]


>[!important] Proposition
>Suppose $M$ and $N$ are smooth manifolds with or without boundary, and $F: M \rightarrow N$ is a **diffeomorphism**. 
>
>For every $X \in \mathfrak{X}(M)$, there is a **unique** *smooth vector field* on $N$ that is **$F$-related** to $X$.

- [[Diffeomorphism]]

## Pushforward of Smooth Vector Fields

- [[Pushforward of Vector Fields]]

## Lie Bracket of Smooth Vector Fields

- [[Lie Bracket of Vector Fields]]




-----------
##  Recommended Notes and References


- [[Differential of a Smooth Map at Point]]
- [[Smooth Map between Euclidean Spaces]]
  
  
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field on Manifold]]


- [[Vector Space over a Field]]

- [[Introduction to Smooth Manifolds by Lee]]