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
>**Name**: Tensor Product

>[!important] Definition
>Let $V_1,\ldots,V_k$, $W_1,\ldots,W_l$ be real vector spaces, and suppose $F \in L(V_1,\ldots,V_k ; \mathbb{R})$ and $G \in L(W_1,\ldots,W_l; \mathbb{R})$. 
>
>Define a function $F\, \otimes \, G: V_1\times \ldots \times V_k \times W_1\times \ldots \times W_l \rightarrow \mathbb{R}$
> by
>$$
> \begin{align}
> (F\, \otimes \, G)(v_1,\ldots,\,v_k,\,w_1 \ldots, w_l)&= F(v_1,\ldots,\,v_k)\,G(w_1 \ldots, w_l) 
> \end{align}
>$$  
>
>It follows from the *multilinearity* of $F$ and $G$ that $(F\, \otimes \, G)(v_1,\ldots,\,v_k,\,w_1 \ldots, w_l)$ depend *linearly* on *each argument* $v_i$ or $w_j$ *separately*. 
>
>Thus $F\, \otimes \, G$ is an element of $L(V_1,\ldots,V_k, W_1,\ldots,W_l; \mathbb{R})$ called **the tensor product** of $F$ and $G$.

- [[Multilinear Function]]



## Explanation


## Kronecker Product

- [[Kronecker Product of Matrices]]



-----------
##  Recommended Notes and References

- [[Multilinear Function]]
- [[Arbitrary Cartestian Products]]

- [[Kronecker Product of Matrices]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]