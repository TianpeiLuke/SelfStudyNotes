---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
  - math/differential_geometry
keywords:
  - sesquilinear_form
topics:
  - linear_algebra
  - functional_analysis
  - tensor_analysis
name: Sesquilinear Form
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Sesquilinear Form


>[!important] Definition
>Let $V$ and $W$ be vector fields over complex field $\mathbb{C}$.
>
>Define $B(\cdot, \cdot)$ as a function from $V \times W$ to $\mathbb{C}$ which satisfies:
> 
> 1. **Linearity** in first argument: for $x,y\in V$ and $z\in W$,  $\alpha, \beta \in \mathbb{C}$, $$B(\alpha x + \beta y, z) = \alpha B(x, z) + \beta B(y, z)$$
> 2. **Conjugate Linearity** in second argument: for $x\in V$. $y, z\in W$, $\alpha, \beta \in \mathbb{C}$, $$B(x, \alpha y + \beta z) = \overline{\alpha} B(x, y) + \overline{\beta} B(x, z)$$
>
>The function $B(\cdot, \cdot)$  is called a **sesquilinear form.**

>[!info]
>We can change the linearity and conjugate linearity position, and it will be another form. 
>
>These two definitions are not the same unless $B$ is *Hermitian*.

## Explanation

>[!important]
>A *sesquilinear form* is a **covariant 2-tensor** on $V \times \overline{W}$, where $\overline{W}$ is the *complex conjugate vector space* to $W$, where the scalar multiplication is with the complex conjugate.
>
>$$
>B \in V^{*} \otimes \overline{W}^{*}
>$$

- [[Covariant Tensor on Vector Space]]
- [[Tensor Product]]

>[!info]
>An *inner product* in complex vector space is a **positive definite sesquilinear form**.

- [[Inner Product Space]]



-----------
##  Recommended Notes and References

- [[Riesz Representation Theorem]]


- [[Covariant Tensor on Vector Space]]
- [[Multilinear Function]]
- [[Inner Product Space]]
- [[Vector Space over a Field]]


- [[Introduction to Smooth Manifolds by Lee]]
- [[Functional Analysis by Reed]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 227, 232


- Wikipedia [Complex_conjugate_of_a_vector_space](https://en.wikipedia.org/wiki/Complex_conjugate_of_a_vector_space)