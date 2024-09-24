---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - tensor
  - multilinearity
topics:
  - differential_geometry
  - linear_algebra
name: " Multilinear Function"
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Multilinear Function

>[!important] Definition
>Suppose $V_1,\ldots,V_k$, and $W$ are *vector spaces*. 
>
>A map $F: V_1\times \ldots \times V_k \rightarrow W$ is said to be **multilinear** if it is *linear* as a function of **each variable separately** when the others are held *fixed*: 
>
>That is, for each $i$,
>$$
> \begin{align*}
> F(v_1,\ldots,\,av_i + a'v_i',\, \ldots, v_k) = a\,F(v_1,\ldots,\,v_i,\, \ldots, v_k)  + a'F(v_1,\ldots,\, v_i',\, \ldots, v_k).
> \end{align*} 
>$$ 



>[!important] Definition
>Denote $L(V_1,\ldots,V_k ; W)$ as **the set of all multilinear maps** *from* $V_1\times \ldots \times V_k$ to $W$. 
>
>It is a *vector space* under the usual operations of *pointwise addition* and *scalar multiplication*:
>$$
> \begin{align*}
> (F'+F)(v_1,\ldots,\,v_i,\, \ldots, v_k) &= F(v_1,\ldots,\,v_i,\, \ldots, v_k)  +  F'(v_1,\ldots,\,v_i,\, \ldots, v_k),\\
> (aF)(v_1,\ldots,\,v_i,\, \ldots, v_k)  &= a\,F(v_1,\ldots,\,v_i,\, \ldots, v_k).
> \end{align*}
>$$ 

- [[Linear Map]]
- [[Vector Space over a Field]]


>[!important] Definition
>- A *multilinear function* of **one variable** is just a **linear function**, and 
>- a multilinear function of **two variables** is generally called **bilinear**.

- [[Sesquilinear Form]]
- [[Inner Product Space]]

## Explanation


## Examples





-----------
##  Recommended Notes and References

- [[Arbitrary Cartestian Products]]

- [[Introduction to Smooth Manifolds by Lee]]