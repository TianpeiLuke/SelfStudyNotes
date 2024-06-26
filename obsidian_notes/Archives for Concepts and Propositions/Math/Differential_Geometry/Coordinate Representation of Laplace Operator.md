---
tags:
  - concept
  - math/differential_geometry
keywords:
  - coordinate_representation
  - laplace_operator
topics:
  - differential_geometry
name: Coordinate Representation of Laplace Operator
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Laplace Operator

>[!important]
>Let $(M, g)$ be an *oriented Riemannian $n$-manifold* (with or without boundary) and $(x^i)$ be smooth coordinates on an open subset $U \subseteq M$. 
>
>Suppose $f: M \to \mathbb{R}$ is a smooth map. 
>
>- The *gradient* of $f$ can be written in terms of coordinate basis frame:
>$$
>\text{grad }f = g^{i,j}\frac{ \partial f}{ \partial x^{i} }\frac{\partial }{ \partial x^{j} }.  
>$$ 
>where $(g^{i,j})$ is the *matrix of the inverse map* $\hat{g}^{-1}: T^{*}M \to TM$.
>- The *divergence operator* of a vector field $$X = X^i \frac{ \partial  }{ \partial x^i }$$ has representation 
>$$
>\text{div }X =\frac{1}{\sqrt{ \det(g)  } }\frac{ \partial  }{ \partial x^i }\left(X^i\,\sqrt{ \det(g)  }\right)
>$$
>- The **Laplace operator** is defined as $$\Delta f := \text{div}\left(\text{grad }f\right).$$ So it has representation
>$$
>\begin{align*}
>\Delta f &= \frac{1}{\sqrt{ \det(g)  } }\frac{ \partial  }{ \partial x^i }\left(g^{i,j}\;\sqrt{\det(g)}\;\frac{ \partial f}{ \partial x^{j} }\right)
>\end{align*}
>$$

- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Gradient of Smooth Map]]

- [[Coordinate Representation of Gradient]]
- [[Coordinate Representation of Divergence Operator]]

- [[Einstein Summation Convention]]

## Explanation



## Euclidean metric

>[!important]
>Under **Euclidean metric** $\det(g) = 1$, thus
>$$
>\begin{align*}
>\Delta f &= \sum_{i,j=1}^{n}\delta_{i,j}\frac{ \partial  }{ \partial x^i }\left(\frac{ \partial f}{ \partial x^{j} }\right) = \sum_{i=1}^{n}\frac{ \partial^2  }{ (\partial x^i)^2 } f
>\end{align*}
>$$




-----------
##  Recommended Notes and References

- [[Gradient of Smooth Map]]
- [[Riemannian Metric and Riemannian Manifold]]


