---
tags:
  - concept
  - math/differential_geometry
keywords:
  - lower_index_vector_field
  - flat_operator
  - musical_isomorphism
topics:
  - differential_geometry
name: Flat Operator and Lower Index of Vector Field
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Flat Operator and Lower Index of Vector Field

![[Bundle Homomorphism#^d28d96]]

- [[Bundle Homomorphism]]

>[!important] Definition
>Given a *smooth local frame* $(E_i)$ and its **dual coframe** $(\epsilon^i)$, let $$g = g_{i,j}\epsilon^i \epsilon^j$$ be the *local expression* for $g$. 
>
>If $$X= X^i\,E_i$$ is a *smooth vector field*, the **covector field** $\widehat{g}(X)$ has the *coordinate expression*:
>$$
> \begin{align*}
> \widehat{g}(X) = \left(g_{i,j}X^i\right) \epsilon^j := X_j\,\epsilon^j,
> \end{align*}
>$$  
>where the *components* of the covector field $\widehat{g}(X)$ is denoted by 
>$$
> \begin{align}
> X_j &= g_{i,j}X^i. 
> \end{align}
>$$  
>
>We say that *the covector field* $\widehat{g}(X)$ is obtained from *the vector field* $X$ **by lowering an index**. 
>
>And *the covector field* $\widehat{g}(X)$ is denoted by $X^{\flat}$ and called **$X$ flat**.

^a750c7

- [[Riemannian Metric and Riemannian Manifold]]
- [[Vector Field on Manifold]]
- [[Covector Field on Manifold]]
- [[Coordinate Representation of Covector Field on Manifold]]
- [[Coordinate Representation of Vector Field on Manifold]]
- [[Einstein Summation Convention]]



## Explanation

>[!info]
>The **index** of **component function** of vector field before operation is *on the top* i.e.
>$$
>X = X^i \frac{ \partial  }{ \partial x^i } 
>$$
>And after **lowering index**, the result is a covector field whose **component function**'s **index** is **lowered**
>$$
>\omega_{X} = X_{j} dx^{i} := g_{i,j}X^i dx^{j}
>$$
>




-----------
##  Recommended Notes and References

- [[Sharp Operator and Raise Index of Covector Field]]
- [[Tangent-Cotangent Isomorphism in Riemannian Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]

- [[Vector Bundle]]
- [[Homeomorphism]]
- [[Topology of Set]]



- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]