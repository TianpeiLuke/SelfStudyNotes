---
tags:
  - concept
  - math/differential_equation
keywords: 
topics:
  - differential_equation
name: 
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: 

![[Hamiltonian Systems of Differential Equations#^ad0948]]

- [[Hamiltonian Systems of Differential Equations]]

![[Hamiltonian Systems of Differential Equations#^5f6725]]

### Manifold Intepretation




## Explanation


Chicone, C. (2006). _Ordinary Differential Equations with Applications_ (2nd edition). Springer. pp 39

## Reversibility of Hamiltonian Dynamic

>[!important] Proposition
>The Hamiltonian dynamic $(q(t), p(t))$ is **time-reversible** for $t \ge 0$:
>$$
>\theta_{t}(q_{t}(q, p), - p_{t}(q, p)) = (q, -p)
>$$
>where $$\theta_{t}: (q, p) \mapsto (\,q_{t}(q, p)\,,\, p_{t}(q, p)\,)$$ is the *flow* of Hamiltonian dynamic. 
>
>This is equivalent to say that $\theta_{t}$ is **one-to-one mapping.**

- [[Local Flow on Smooth Manifold]]
- [[Bijective Function and Inverse Function]]

## Hamiltonian Vector Field

>[!important] Definition
>The Hamiltonian system of equations defines a **Hamiltonian vector field** 
>$$
> V := \sum_{i=1}^{n}\frac{ \partial H }{ \partial p_{i} }\,\frac{ \partial  }{ \partial q_{i} }  - \sum_{i=1}^{n}\frac{ \partial H }{ \partial q_{i} }\,\frac{ \partial  }{ \partial p_{i} }.
>$$

>[!important] Defintion
>The **gradient field of Hamiltonian** $\text{grad }H$ has the following coordinate representation
>$$
> \text{grad }H := \sum_{i=1}^{n}\frac{ \partial H }{ \partial q_{i} }\,\frac{ \partial  }{ \partial q_{i} }  + \sum_{i=1}^{n}\frac{ \partial H }{ \partial p_{i} }\,\frac{ \partial  }{ \partial p_{i} }.
>$$

- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Coordinate Representation of Gradient]]
- [[Orthogonality in Inner Product Space]]

## Conservation of Hamiltonian 

>[!important] Proposition
>The **Hamiltonian vector field** defined by the Hamiltonian system of equations 
>$$
> V := \sum_{i=1}^{n}\frac{ \partial H }{ \partial p_{i} }\,\frac{ \partial  }{ \partial q_{i} }  - \sum_{i=1}^{n}\frac{ \partial H }{ \partial q_{i} }\,\frac{ \partial  }{ \partial p_{i} }
>$$
>is *orthogonal* to the **gradient field of Hamiltonian** $\text{grad }H$  at each point $(q, p)$ in *phase space*.
>
>This can be interpreted as the **Hamiltonian** $H$ is **invariant** along the flow of Hamiltonian dynamic $(q(t), p(t))$. That is, 
>$$
>\begin{align*}
> \frac{d}{dt} H(q(t), p(t)) &= \left\langle V , \text{grad }H \right\rangle \\
> &=\sum_{i=1}^{n}\left[ \frac{ \partial H }{ \partial q_{i} }\frac{d}{dt} q_{i} + \frac{ \partial H }{ \partial p_{i}}\frac{d}{dt} p_{i}   \right] \\
> &= \sum_{i=1}^{n}\left[ \frac{ \partial H }{ \partial q_{i} }\frac{ \partial H }{ \partial p_{i} } - \frac{ \partial H }{ \partial p_{i}} \dfrac{ \partial H }{ \partial q_{i} }   \right]\\
> &=0
>\end{align*}
>$$


## Volume Preserving

>[!important] Proposition
>The **divergence** of *Hamiltonian vector field* is **zero**. 
>
>That is, 
>$$
>\begin{align*}
> \text{div }V &:= \text{div }\left(\sum_{i=1}^{n}\frac{ \partial H }{ \partial p_{i} }\,\frac{ \partial  }{ \partial q_{i} }  - \sum_{i=1}^{n}\frac{ \partial H }{ \partial q_{i} }\,\frac{ \partial  }{ \partial p_{i} } \right)\\
> &= \sum_{i=1}^{n}\frac{ \partial  }{ \partial p_{i} }\left( - \frac{ \partial H }{ \partial q_{i} }\, \right) + \sum_{i=1}^{n}\frac{ \partial  }{ \partial q_{i} }\left( \frac{ \partial H }{ \partial p_{i} } \right)\\
> &= \sum_{i=1}^{n}\left[\frac{ \partial^2  H}{ \partial p_{i}\partial q_{i} }  - \frac{ \partial^2  H}{ \partial q_{i}\partial p_{i} }  \right] \\
> & = 0
>\end{align*}
>$$
>
>By [[Divergence Theorem on Riemannian Manifold]], this indicates that the Hamiltonian dynamic $(q(t), p(t))$ **preserves volume** in phase space $(q,p)$.
>$$
>\text{Vol}\left( \theta_{s}\left( D \right) \right) = \text{Vol}(D)
>$$
> for every *compact regular domain* $D$, where $\theta_{t}: (q, p) \mapsto (q_{t}(q,p), p_{t}(q, p)).$

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Coordinate Representation of Divergence Operator]]
- [[Divergence Theorem on Riemannian Manifold]]
- [[Measure Preserving Transformation]]

## Symplecticness

- [[Introduction to Smooth Manifolds by Lee]]




-----------
##  Recommended Notes and References

- [[Stable Manifold]]
- [[Smooth Manifold]]

- [[Tangent Bundle]]


- [[Hamiltonian Systems of Differential Equations]]
- [[Ordinary Differential Equations]]


- [[Introduction to Smooth Manifolds by Lee]]
- [[Ordinary Differential Equations by Chicone]]
- Chicone, C. (2006). _Ordinary Differential Equations with Applications_ (2nd edition). Springer.