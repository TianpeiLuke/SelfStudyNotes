---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - projection_theorem
topics:
  - functional_analysis
name: The Projection Theorem of Hilbert Space
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**: The Projection Theorem of Hilbert Spaces

>[!important] The Hilbert Projection Theorem
>Let $\mathcal{H}$ be a *Hilbert space*, $\mathcal{M}$ a **closed subspace** of $\mathcal{H}$, and suppose $x \in \mathcal{H}$. Then there exists in $\mathcal{M}$ a **unique** element $z$ **closest** to $x$.
>
>That is, there exists some element $z^{*} \in \mathcal{M}$ such that
>$$
>d(z^{*}, x) = \inf_{z \in \mathcal{M}}d(z, x)
>$$
>where $d(z, x) = \sqrt{ \left\langle  x-z\,,\, x-z   \right\rangle }.$ 
>
>Denote such optimal solution $z^{*} := \text{Proj}_{\mathcal{M}}(x).$


>[!important] The Hilbert Projection Theorem (Geometric version)
>Let $\mathcal{H}$ be a *Hilbert space*, $\mathcal{M}$ a **closed subspace**. 
>
>Then every $x \in \mathcal{H}$ can be **uniquely** written $$x = z + w$$ where $z \in \mathcal{M}$ and $w \in \mathcal{M}^{\bot}$.

- [[Orthogonal Complement of Hilbert Spaces]]
- [[Direct Sum of Hilbert Spaces]]

## Explanation


>[!important]
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
>\mathcal{H} = \{ x + y: x\in \mathcal{M}, y \in \mathcal{H}, \left\langle x \,,\,y \right\rangle = 0 \}
>$$

- [[Orthogonal Complement of Hilbert Spaces]]
- [[Direct Sum of Hilbert Spaces]]





-----------
##  Recommended Notes and References

- [[Inner Product Space]]
- [[Hilbert Space]]

- [[Projection Map onto Linear Subspace]]