---
tags:
  - concept
  - math/linear_algebra
keywords:
  - quotient_map_linear
topics:
  - linear_algebra
name: Quotient Linear Map on Quotient Vector Space
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Quotient Linear Map on Quotient Vector Space

>[!important] Definition
>Let $V$ be a vector space and $S$ be a *subspace* of $A$. Suppose $A$ is a linear transformation on $V$ and $S$ is *invariant* under $A$. 
>
>Let $V/S$ be the *quotient space* of *$V$ modulo $S$*. Define a **quotient transformation** $\tilde{A}$ on $V / S$ by
>$$
>\tilde{A}\,[x]\, = \left[ Ax \right] 
>$$ 
>where $[x] \in V / S$ is a **coset** represented by $x$
>$$
>[x] := x + S = \{ x + v: v\in S \}.
>$$
>
>Denote such $\tilde{A}$ as $A / S$.

- [[Invariance under Linear Transformation]]
- [[Quotient Space of Vector Space]]


## Explanation

>[!important]
>It is important for $S$ to be **invariant under $A$** so that such **quotient map** is *well-defined*.
>
>If $[x] = [y]$,  then due to $S$ being invariant under $A$
>$$
> [x] = [y] \iff  x-y \in S \implies A(x-y) \in S \iff \left[ Ax \right] = \left[ Ay \right]  
>$$


## Isomorphism of Quotient Map and Map restricted on Complement Space

- [[Quotient Space of Vector Space#Isomorphism between Quotient Space and Complement Subspace]]

>[!important] Proposition
>Assume the direct sum decomposition
>$$
>V = S \oplus W,
>$$
>and the pair $(S, W)$ **reduces** $A$. That is, $A$ has *decomposition*
>$$
>A = A_{S} \oplus A_{W}
>$$
>where $A_{S}$ is the restriction of $A$ on subspace $S$, similarly for $A_{W}$.
>
>We know that there exists an isomorphism $T: W \to V/S$ 
>$$
>W \simeq V / S.
>$$
>Then we can show that 
>$$
>\left(A / S\right)\,T = T\,A_{W}
>$$
>In other word, the **quotient linear transformation** $A / S$ is **isomorphic** to $A_{W}$, the *restriction* of $A$ on complement subspace $W$.
>$$
>\begin{CD}
> W @>A_{W}>> W\\
> @V T VV   @V T VV \\
> V / S @> A/S >> V/S
\end{CD}
>$$

- [[Reducibility of Linear Transformation]]


>[!info] Proof
>for any $w \in W$, denote $y  = A_{W}\,w \in W$, then
>$$
>\left(A / S\right)[w] = \left[ A\,w \right] =  \left[ A_{W}\,w \right] =[y] 
>$$
>and 
>$$
>T\, A_{W}\,w = T\,y = [y]
>$$
>so
>$$
>T\, A_{W}\,w = \left(A / S\right)[w] = \left(A / S\right)T\,w
>$$




-----------
##  Recommended Notes and References


- [[Invariance under Linear Transformation]]
- [[Quotient Space of Vector Space]]

- [[Linear Map]]

- [[Quotient Set]]
- [[Equivalence Class]]

- [[Finite Dimensional Vector Spaces by Halmos]]