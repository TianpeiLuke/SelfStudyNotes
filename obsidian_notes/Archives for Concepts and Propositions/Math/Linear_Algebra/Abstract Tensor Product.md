---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - exterior_form
topics:
  - differential_geometry
  - linear_algebra
name: Exterior Forms
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Abstract Tensor Product

- [[Introduction to Smooth Manifolds by Lee]]

>[!info] Definition (via Construction)
>Now let $V_1,\ldots,V_k$ be real vector spaces. 
>
>- We begin by forming **the free vector space** $\mathcal{F}(V_1\times \ldots \times V_k)$, which is the set of *all finite* formal linear combinations of $k$-tuples $(v_1,\ldots,\,v_k)$ with $v_i \in V_i$ for $i = 1,\ldots,k$. 


>[!info]
>
>- Let $\mathcal{R}$ be the *subspace* of $\mathcal{F}(V_1\times \ldots \times V_k)$   *spanned* by all elements of the following forms:
>$$
> \begin{align}
> &(v_1,\ldots,\,a\,v_i, \ldots, v_k) - a\,(v_1,\ldots,\,v_i, \ldots, v_k) \nonumber\\
> &(v_1,\ldots,\,v_i + v_i', \ldots, v_k) - (v_1,\ldots,\,v_i, \ldots, v_k) -  (v_1,\ldots,\ v_i', \ldots, v_k) 
> \end{align}
>$$  
>with $v_j, v_j' \in V_j$, $i \in \set{1,\ldots,k}$, and $a \in \mathbb{R}$.


>[!important] Definition
>- Define **the tensor product** of **the spaces** $V_1,\ldots,V_k$, denoted by $V_1 \otimes \ldots \otimes V_k$, to be the following  *quotient vector space*:
>$$
> \begin{align*}
> V_1 \otimes \ldots \otimes V_k &= \mathcal{F}(V_1\times \ldots \times V_k) / \mathcal{R}
> \end{align*}
>$$ 
>  and let $\Pi:  \mathcal{F}(V_1\times \ldots \times V_k)  \rightarrow V_1 \otimes \ldots \otimes V_k$ be *the natural projection*. 
>- The *equivalence class* of an element $(v_1, \ldots, v_k)$ in $V_1 \otimes \ldots \otimes V_k$ is denoted by
>$$
> \begin{align}
> v_1 \otimes \ldots \otimes v_k &= \Pi(v_1, \ldots, v_k)\qquad (1)
> \end{align}
>$$ 
> and is called **the (abstract) tensor product** of $(v_1, \ldots, v_k)$. 

- [[Multilinear Function]]
- [[Tensor Product]]
- [[Quotient Space of Vector Space]]

>[!info]
> It follows from the definition that abstract tensor products satisfy
>$$ 
> \begin{align*}
> v_1 \otimes \ldots \otimes (a\,v_i)  \otimes \ldots \otimes v_k  &= a (v_1  \otimes \ldots  \otimes v_i \otimes \ldots \otimes v_k),\\
> v_1 \otimes \ldots \otimes (v_i + v_i') \otimes \ldots \otimes v_k &= (v_1 \otimes \ldots \otimes v_i \otimes \ldots \otimes v_k) +  (v_1 \otimes \ldots \otimes v_i' \otimes \ldots \otimes v_k) 
> \end{align*}
>$$ 


## Explanation

>[!info]
>This abstract construction definition of tensor product is equivalent to [[Tensor Product]]

>[!important] Proposition
>If $V_1,\ldots,V_k$  are finite-dimensional vector spaces, there is a **canonical isomorphism**
>$$
> \begin{align}
> V_1^{*}\otimes \ldots \otimes V_k^{*} &\simeq L(V_1,\ldots,V_k ; \mathbb{R}) 
> \end{align} 
>$$ 
>under which the **abstract tensor product** defined by (1) corresponds to the **tensor product of covectors** defined by 
>$$
>\begin{align}
(\omega^1\otimes \ldots \otimes \omega^k)(v_1, \ldots, v_k)&= \omega^1(v_1)\,\ldots \omega^{k}(v_k).  
\end{align}
>$$
>where  $\omega^j \in V_{j}^{*}$ for $j = 1,\ldots,k$,.

- [[Linear Isomorphism]]
- [[Multilinear Function]]
- [[Covector on Vector Space]]





-----------
##  Recommended Notes and References

- [[Multilinear Function]]
- [[Tensor Product]]

- [[Quotient Space of Vector Space]]
- [[Vector Space over a Field]]

- [[Introduction to Smooth Manifolds by Lee]]