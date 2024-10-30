---
tags:
  - concept
  - math/differential_equation
  - math/real_analysis
keywords:
  - inverse_function_theorem
topics:
  - differential_equation
  - real_analysis
name: Inverse Function Theorem
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Inverse Function Theorem

>[!important] Inverse Function Theorem
>Let $f \in \mathcal{C}^{1}$ be a **continuously differentiable function** on an *open set* $E \subset \mathbb{R}^{n}$ into $\mathbb{R}^{n}$.
>- And the **Jacobian** $D f(a)$ is **invertible** for some $a \in E$, 
>- and $$b = f(a).$$
>  
>Then 
>- there **exists** *open sets* $U, V$ in $\mathbb{R}^{n}$  such that $$a \in U,\; b\in V$$ and $f$ is **one-to-one** on $U$, and $$f(U) = V;$$
>- if $g$ is the **inverse** of $f$ (which by above *exists*), defined in $V$ by $$g(f(x)) = x\quad \forall x\in U$$ then $g\in \mathcal{C}^{1}(V)$ is also **continuously differentiable.**

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Injective Function]]
- [[Bijective Function and Inverse Function]]
- [[Smooth Map between Euclidean Spaces]]
- [[Differential of a Smooth Map at Point]]
- [[Coordinate Representation of Differential at Point]]


## Explanation


Chicone, C. (2006). _Ordinary Differential Equations with Applications_ (2nd edition). Springer. pp 62



-----------
##  Recommended Notes and References

- [[Stable Manifold]]
- [[Smooth Manifold]]

- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Urysohn Lemma]]
- [[Implicit Function Theorem]]

- [[Ordinary Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 240, 266
- [[Principles of Mathematical Analysis by Rudin]] pp 221
