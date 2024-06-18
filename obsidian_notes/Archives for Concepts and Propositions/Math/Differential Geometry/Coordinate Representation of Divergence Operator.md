---
tags:
  - concept
  - math/differential_geometry
keywords:
  - coordinate_representation
  - divergence_operator
topics:
  - differential_geometry
name: Coordinate Representation of Gradient
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Divergence Operator

>[!important]
>Let $(M, g)$ be an *oriented Riemannian $n$-manifold* (with or without boundary) and $(x^i)$ be smooth coordinates on an open subset $U \subseteq M$. 
>
>Suppose $X: M \rightarrow TM$ is a *smooth vector field*. The **divergence** of $X$ is defined as
>$$
>d\left(X \mathbin{\lrcorner } dV_{g}\right) := (\text{div }X)\,dV_{g} 
>$$ 
>where $dV_{g}$ is the *Riemannian volume form*
>$$
>dV_{g} := \sqrt{ \det(g) }\; dx^1 \,{\wedge}\ldots{\wedge}\, dx^{n}
>$$
>
>The **divergence** of $$X := X^i \frac{ \partial  }{ \partial x^i } $$ has coordinate representation
>$$
>\text{div }X =\frac{1}{\sqrt{ \det(g)  } }\frac{ \partial  }{ \partial x^i }\left( X^i\,\sqrt{ \det(g)  }\right)
>$$

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Exterior Derivatives of Differential Form]]
- [[Interior Multiplication]]
- [[Riemannian Volume Form]]
- [[Einstein Summation Convention]]


## Explanation

>[!info]
>$$
>\begin{align*}
> X &= X^i  \frac{ \partial  }{ \partial x^i } \\
> dV &= \rho\, dx^1 \,{\wedge}\ldots{\wedge}\, dx^n, \qquad \text{where } \rho = \sqrt{ \det(g_{i,j}) }\\
> \Rightarrow X  \mathbin{\lrcorner } dV &= X  \mathbin{\lrcorner }\left(\rho\, dx^1 \,{\wedge}\ldots{\wedge}\, dx^n\right) \\
> &= \sum_{i=1}^{n}(-1)^{i-1}\rho X^i dx^1 \,{\wedge}\ldots{\wedge}\, \widehat{dx^i} \,{\wedge}\ldots{\wedge}\,dx^n\\
> \Rightarrow d\left(X  \mathbin{\lrcorner } dV\right)&=  \sum_{i=1}^{n}(-1)^{i-1}d\left(\rho X^i\right) \,\wedge dx^1\,{\wedge}\ldots{\wedge}\, \widehat{dx^i} \,{\wedge}\ldots{\wedge}\, dx^n\\
> &= \sum_{i=1}^{n}(-1)^{i-1}\left(\sum_{s=1}^{n}\frac{\partial (\rho X^i) }{ \partial x^s }\,dx^s\right) \wedge dx^1\,{\wedge}\ldots{\wedge}\, \widehat{dx^i} \,{\wedge}\ldots{\wedge}\, dx^n\\
> &= \sum_{i=1}^{n}(-1)^{i-1}\left(\frac{ \partial (\rho X^i) }{ \partial x^i } dx^i\right) \wedge dx^1 \,{\wedge}\ldots{\wedge}\, \widehat{dx^i} \,{\wedge}\ldots{\wedge}\,dx^n\\
> &=  \frac{1}{\rho}\sum_{i=1}^{n}\left(\frac{ \partial (\rho X^i) }{ \partial x^i }\, \rho\,dx^1\,{\wedge}\ldots{\wedge}\, dx^i  \,{\wedge}\ldots{\wedge}\, dx^n\right)\\
> &=  \frac{1}{\rho}\sum_{i=1}^{n}\frac{ \partial (\rho X^i) }{ \partial x^i } dV \\
> &= \left(\frac{1}{\rho}\sum_{i=1}^{n} \frac{ \partial (\rho X^i) }{ \partial x^i } \right)dV\\
> \Rightarrow  \text{div}(X)&=\frac{1}{\rho}\sum_{i=1}^{n} \frac{ \partial (\rho X^i) }{ \partial x^i }
> \end{align*}
>$$ 

## Euclidean metric

>[!important]
>Under **Euclidean metric** $\det(g) = 1$, thus
>$$
>\text{div }X = \sum_{i=1}^{n}\frac{ \partial  }{ \partial x^i }X^i
>$$






-----------
##  Recommended Notes and References

- [[Gradient of Smooth Map]]
- [[Riemannian Metric and Riemannian Manifold]]


