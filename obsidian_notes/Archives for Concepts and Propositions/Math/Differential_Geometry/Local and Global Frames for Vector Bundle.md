---
tags:
  - concept
  - math/differential_geometry
keywords:
  - local_frame
  - global_frame
topics:
  - differential_geometry
name: Local and Global Frames for Vector Bundle
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Local and Global Frames for Vector Bundle

>[!important] Definition
>Let $E \rightarrow M$ be a *vector bundle*. 
>
>If $U \subseteq M$ is an open subset, a *$k$-tuple* of *local sections* $(\sigma_1,\ldots, \sigma_k)$ of $E$ over $U$ is said to be **linearly independent** if their *values* $(\sigma_1(p),\ldots, \sigma_k(p))$ form a *linearly independent $k$-tuple* in $E_p$ for each $p\in U$. 

>[!important] Definition
>Similarly, they are said to **span** $E$ if *their values* span $E_p$ for each $p \in U$.


- [[Linear Independence]]
- [[Linear Span over a Set of Vectors]]
- [[Basis of Vector Space]]
- [[Vector Space over a Field]]

>[!important] Definition
>A **local frame** *for* $E$ *over* $U$ is an *ordered $k$-tuple* $(\sigma_1,\ldots, \sigma_k)$ of *linearly independent local sections* over U that *span* $E$; 
>
>thus $(\sigma_1(p),\ldots, \sigma_k(p))$ is a *basis* for the *fiber* $E_p$ for each $p \in U$. 
>$$
>E_{p} = \text{span}\{ \sigma_1(p),\ldots, \sigma_k(p) \}, \;\; \forall p \in U.
>$$

>[!important] Definition
>It is called a **global frame** if $U = M$. 

>[!important] Definition
>If  $E \rightarrow M$ is a *smooth vector bundle*, a *local or global frame* is a **smooth frame** if each $\sigma_i$ is a *smooth section*. 
>
>We often denote a frame $(\sigma_1,\ldots, \sigma_k)$ by $(\sigma_i)$.

- [[Smooth Section of Vector Bundle]]

## Explanation



## Completion of Local Frame

>[!important] Proposition
>Suppose $\pi: E \rightarrow M$ is a smooth vector bundle of rank $k$.

>[!important] 
> - If $(\sigma_1,\ldots, \sigma_m)$ is a **linearly independent** $m$-tuple of **smooth local sections** of $E$ over an *open subset* $U \subseteq M$, with $1 \le m < k$,  then for each $p \in U$ there *exist* **smooth sections** $\sigma_{m+1},\ldots, \sigma_{k}$ defined on some neighborhood $V$ of $p$ such that $(\sigma_1,\ldots, \sigma_k)$ is a **smooth local frame** for $E$ over $U \cap V$.

>[!important]  
> - If $(v_1,\ldots,v_m)$ is a **linearly independent** $m$-tuple of *elements* of $E_p$ for some $p\in M$, with $1 \le m \le k$, then there *exists* a **smooth local frame** $(\sigma_i)$ for $E$ over some neighborhood of $p$ such that $$\sigma_i(p) = v_i$$ for $i = 1,\ldots,m$.

>[!important]
 >- If $A \subseteq M$ is a **closed subset** and $(\tau_1,\ldots, \tau_k)$ is a **linearly independent** $k$-tuple of **sections** of $E|_{A}$ that are **smooth** in the sense described in [[Vector Bundle]],  then there exists a **smooth local frame** $(\sigma_1,\ldots, \sigma_k)$ for $E$ over *some neighborhood of* $A$ such that $$\sigma_{i}\big|_{A} = \tau_{i}$$ for $i = 1,\ldots,k$.


- [[Linear Independence]]
- [[Basis of Vector Space]]

## Construct Smooth Local Trivialization

>[!info]
>Suppose $E \rightarrow M$  is a smooth vector bundle. 
>
>If $\Phi: \pi^{-1}(U) \rightarrow U \times \mathbb{R}^{k}$ is a **smooth local trivialization** of $E$, we can construct a **local frame** for $E$ over $U$.  

>[!info]
>Define maps $\sigma_1, \ldots, \sigma_k: U \rightarrow E$ by $$\sigma_i(p) = \Phi^{-1}(p, e_i) = \Phi^{-1} \circ \widetilde{e}_i(p)$$ as below:
>
>![[local_frame_local_trivialization.png]]
>
> where $(e_1,\ldots, e_k)$  are **the standard basis** for $\mathbb{R}^k$ so that $\widetilde{e}_i$ is the **frame** such that $$\widetilde{e}_i = (p, e_i).$$ 


>[!info]
> Then $\sigma_i$ is **smooth** because $\Phi$ is a **diffeomorphism**, and the fact that $$\pi_1 \circ \Phi = \pi$$ 
> implies that
> $$
> \begin{align*}
> \pi \circ \sigma_i(p) &=  \pi \circ  \Phi^{-1}(p, e_i) = \pi_1(p, e_i) = p,
> \end{align*}
>$$  
>so $\sigma_i$ is a **section**. 

>[!info]
>To see that $(\sigma_i(p))$ **forms a basis** for $E_p$, just note that $\Phi$ *restricts* to an **isomorphism** *from* $E_p$ *to* $\set{p} \times \mathbb{R}^k$, and $$\Phi(\sigma_i(p)) = (p, e_i),$$ so $\Phi$ takes $\sigma_i(p)$ to the **standard basis** for $\set{p} \times \mathbb{R}^k \simeq \mathbb{R}^{k}$. 


>[!info]
>We say that **this local frame** $(\sigma_i)$ is **associated with** $\Phi$. \qed


>[!important] Proposition
>Every **smooth local frame** for a **smooth vector bundle** is associated with a **smooth local trivialization** constructed as above.

>[!important] Corollary
>A *smooth vector bundle* is **smoothly trivial** *if and only if* it admits a **smooth global frame**.


- [[Coordinate Representation of Element in Vector Bundle]]








-----------
##  Recommended Notes and References

- [[Local and Global Frame for Tangent Bundle]]
- [[Local and Global Coframes for Cotangent Bundle]]

- [[Space of all Smooth Sections of Vector Bundle]]
	- [[Space of all Smooth Vector Fields on a Manifold]]
	- [[Space of all Smooth Covector Fields on a Manifold]]


- [[Smooth Section of Vector Bundle]]
	- [[Smooth Vector Field on Manifold]]

- [[Section of Vector Bundle]]
	- [[Vector Space over a Field]]
	- [[Covector Field on Manifold]]

- [[Vector Bundle]]
	- [[Tangent Bundle]]
	- [[Cotangent Bundle]]


- [[Basis of Vector Space]]


- [[Introduction to Smooth Manifolds by Lee]]