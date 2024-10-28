---
tags:
  - concept
  - math/differential_geometry
keywords:
  - differential_map
topics:
  - differential_geometry
name: Differential of a Smooth Map
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Differential of a Smooth Map

>[!important] Definition
>If $M$ and $N$ are *smooth manifolds* with or without boundary and $F: M \rightarrow N$ is a *smooth map*, for each $p \in M$ we define a map
>$$
> \begin{align*}
> dF_{p}: T_{p}M \rightarrow T_{F(p)}N ,
> \end{align*} 
>$$ 
> called the **differential** of $F$ at $p$, as follows. 
> 
> Given $v \in T_{p}M$, we let $dF_{p}(v)$ be the **derivation** at $F(p)$ that **acts** on $f \in \mathcal{C}^{\infty}(N)$ by the rule 
>$$ 
> \begin{align*}
> dF_{p}(v)(f) &= v(f \circ F).
> \end{align*} 
>$$
>

- [[Tangent Space Definition and Development]]
- [[Smooth Map between Euclidean Spaces]]

 >[!info]
> Note that if $f \in \mathcal{C}^{\infty}(N)$, then $f \circ F \in \mathcal{C}^{\infty}(M)$, so $v(f \circ F)$ makes sense. 
>
>$$
>v(f) := \frac{d}{dt}f(p + t\,v)
>$$
>$$
>\begin{align*}
>dF_{p}(v)(g) & =\frac{d}{dt}g(F(p + t\,v)) 
\end{align*}, \quad p\in M, v \in T_{p}M
>$$


>[!info] Other Names
>In the differential geometry literature, the **differential** is sometimes called 
>- the **tangent map**, 
>- the **total derivative**, or 
>- simply **the derivative of $F$.** 
>-  **the (pointwise) pushforward**. 
>	- Because it "**pushes**" *tangent vectors* **forward** *from the domain manifold* to the *codomain*

>[!info]
>Different authors denote it by symbols such as
>$$
> \begin{align*}
> F'(p), \quad D\,F(p), \quad D\,F, \quad F^{*},\quad T\,F, \quad T_{p}F.
> \end{align*}
>$$ 



## Explanation

>[!info]
>The **differential** $dF_{p}$ is a **linear operator** that maps a *linear functional* on $\mathcal{C}^{\infty}(M)$ to another *linear functional* $\mathcal{C}^{\infty}(N)$. This reflects the **impact of smooth map** $F: M \rightarrow N$.
>
>
>Note that *the tangent vector* itself is a *linear functional* on the smooth functions $f$

- [[Bounded Linear Operator and Norm of Operator]]

![[differentials.png]]

## Properties

>[!important] Proposition
>Let $M, N$, and $P$ be smooth manifolds with or without boundary, let $F: M \rightarrow N$ and $G: N \rightarrow P$ be smooth maps, and let $p \in M$.
> 
>- $dF_{p}: T_{p}M \rightarrow T_{F(p)}N$ is **linear.**
>- $d(G \circ F)_{p} = dG_{F(p)} \circ dF_{p}: T_{p}M \rightarrow T_{(G \circ F)(p)}P$.
>- $d(\text{Id}_{M})_{p} = \text{Id}_{T_{p}M}: T_{p}M \rightarrow T_{p}M$.
>- If $F$ is a **diffeomorphism**, then $dF_{p}: T_{p}M \rightarrow T_{F(p)}N$ is an **isomorphism**, and
> $(dF_{p})^{-1} = d(F^{-1})_{F(p)}$

## Coordinate Representation

- [[Coordinate Representation of Differential at Point]]


-----------
##  Recommended Notes and References

- [[Tangent Space Definition and Development]]
- [[Smooth Map between Euclidean Spaces]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Principles of Mathematical Analysis by Rudin]] pp 260 - 261