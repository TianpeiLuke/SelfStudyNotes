---
tags:
  - concept
  - math/linear_algebra
keywords:
  - quotient_vector_space
topics:
  - linear_algebra
name: Quotient Space of Vector Space
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Quotient Space of Vector Space

>[!important] Definition
>Let $V$ be a *vector space* and $S \subset V$ be the *subspace* of $V$. 
>
>For any $x\in V$,  define $x+ S$ as the set of all vectors $x+v$ where $v\in S$, i.e.
>$$
>x + S := \left\{ x+v: v\in S\right\}. 
>$$
>
>Note that it is possible for $x \neq y$, but $x + M = y + M.$ 

- [[Linear Subspace]]
- [[Vector Space over a Field]]

>[!important] Proposition
>We define a relation $R \subset V \times V$ as
>$$
>x R y \iff  x - y \in S.
>$$
>
>Then $R$ satisfies the *Reflexivity*, *Symmetry*, *Transitivity* properties. Thus $R$ is an **equivalence relation**, called **congruent relation**,
>
>We define the **coset** (*equivalence class*) of $x$ as 
>$$
>[x] := x + S
>$$

- [[Equivalence Relation]]
- [[Equivalence Class]]

>[!important] Definition 
>Note that 
>- for $x\in V$ and $y\in V$, the **coset addition** is
>$$
>\begin{align*}
>(x + S) + (y + S) &= \{ x + v: v\in S \} + \{ y + w: w\in S \} \\
>&= \{x+y + u: u \in S  \}\\
>&= x+y + S
\end{align*}
>$$
>- also for any $\lambda \in F$, the **scalar product of coset** is
>$$
>\begin{align*}
> \lambda (x + S) &= \lambda \{ x + v: v\in S \} \\
>&= \{ \lambda x  +  \lambda v: v \in S  \}\\
>&=  \{ \lambda x  +  u: u \in S  \}\\
>&= \lambda x + S
\end{align*}
>$$
>since $S$ is a linear subspace, that is closed under vector addition and scalar product.
>- Similarly, we define the **identity** $0 + S = S$ where $0 \in V$ is the zero vector in $V$. Note that $0 \in S$ as well.


>[!important] Proposition
>Let $V$ be a *vector space* and $S \subset V$ be the *subspace* of $V$. 
>
>The set of all cosets $x+ S$ for arbitrary $x\in V$ forms a *vector space* under the coset addition, scalar product.
>
>It is called the **quotient space** of *$V$ modulo $S$*, denoted as $V / S$.

- [[Vector Space over a Field]]
- [[Quotient Set]]

## Explanation

>[!info]
>Quotient space $V / S$ **identifies** all linear transformation under $S$ as **equivalent**. 
>
>It is equivalent geometrically *compress* the entire *subspace* into a *point*, since the relative *coordinate within* $S$ does not matter at all.

## Isomorphism between Quotient Space and Complement Subspace

>[!important] Proposition
>If $S$ and $W$ are **complementary subspaces** of a vector space $V$, i.e.
>$$
>V = S \oplus W,
>$$
>then the correspondence $W \to V/S$ defined by
>$$
>w \mapsto w + S, \quad \forall w\in W
>$$
>is an **isomorphism** between $W$ and $V/S$. That is,
>$$
>W \simeq V / S.
>$$

- [[Direct Sum of Subspaces]]
- [[Linear Isomorphism]]

## Dimension

>[!important] Proposition (Dimension of Quotient Space)
>If $S$ is an $m$-dimensional *subspace* of an $n$-dimensional vector space $V$, then the quotient space $V / S$ has dimension $(n- m)$.



-----------
##  Recommended Notes and References

- [[Quotient Set]]
	- [[Quotient Group]]

- [[Quotient Map]]

- [[Linear Subspace]]
- [[Vector Space over a Field]]

- [[Finite Dimensional Vector Spaces by Halmos]]