---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - direct_sum
  - orthogonal_complement
topics:
  - functional_analysis
name: Orthogonal Complement of Hilbert Space
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Orthogonal Complement of Hilbert Spaces

>[!important] Proposition
>Let $\mathcal{M} \subseteq \mathcal{H}$ is a **closed linear subspace** of *Hilbert space* $\mathcal{H}$ with *induced inner product* $\left\langle \,,\,\right\rangle$ i.e. 
>$$\left\langle  x\,,\, y   \right\rangle_{\mathcal{M}} = \left\langle x \,,\,y \right\rangle_{\mathcal{H}}$$ 
>for all $x, y \in \mathcal{M}$.  Then $\mathcal{M}$ is also a *Hilbert space*.

>[!important] Definition
> We denote by $\mathcal{M}^{\bot}$ the set of vectors in $\mathcal{H}$ which are *orthogonal to* $\mathcal{M}$;  $\mathcal{M}^{\bot}$ is called **the orthogonal complement** of $\mathcal{M}$. 
> 
>$$
>\mathcal{M}^{\bot} := \{ v\in \mathcal{H}: \left\langle  v\,,\,x    \right\rangle = 0, \forall x \in \mathcal{M} \}
>$$
> 

>[!info]
> It follows from the linearity of the inner product that $\mathcal{M}^{\bot}$ is a *linear subspace* of $\mathcal{H}$ and an elementary argument shows that $\mathcal{M}^{\bot}$ is **closed**. So $\mathcal{M}^{\bot}$ is also a **Hilbert space**.

- [[Orthogonality in Inner Product Space]]
- [[Inner Product Space]]
- [[Hilbert Space]]

## Explanation

>[!info]
>**Orthogonality** is the *central concept* of *Hilbert space*. 
>
>In the presence of **closed subspaces**, the orthogonality allows us to **decompose** the Hilbert space into *the direct sum* of the *subspace* and its *orthogonal complement*.
>
>That is for a closed subspace $\mathcal{M} \subset \mathcal{H}$, 
>$$
>\mathcal{H} = \mathcal{M} \oplus \mathcal{M}^{\bot}.
>$$ 
>or
>$$
>\mathcal{H} = \{ x + y: x\in \mathcal{M}, y \in \mathcal{H} \text{ such that } \left\langle x \,,\,y \right\rangle = 0 \}
>$$

- [[Projection Theorem of Hilbert Spaces]]
- [[Direct Sum of Hilbert Spaces]]



-----------
##  Recommended Notes and References

