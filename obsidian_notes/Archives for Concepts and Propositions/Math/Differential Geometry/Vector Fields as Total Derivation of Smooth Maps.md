---
tags:
  - concept
  - math/differential_geometry
keywords:
  - space_vector_field
topics:
  - differential_geometry
name: Vector Fields as Total Derivation of Smooth Maps
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Vector Fields as Derivations of $\mathcal{C}^{\infty}(M)$

>[!important] 
>An *essential property* of vector fields is that they define **operators** *on the space of smooth real-valued functions.*



>[!important] Definition
>If $X \in \mathfrak{X}(M)$ and $f$ is a *smooth real-valued function* defined on an open subset $U \subseteq M$, we obtain *a new function* $Xf:  U \rightarrow \mathbb{R}$, defined by 
>$$
> \begin{align*}
> (X\,f)_{p} &=  X_{p}\,f
> \end{align*}
>$$  
>Note that $v\,f \equiv v(f)$ as we omit the parenthesis.

- [[Smooth Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Vector Space over a Field]]
- [[Derivation of Smooth Map at point and Tangent Vector]]

>[!important] Definition
>Define a map $X: \mathcal{C}^{\infty}(M) \rightarrow \mathcal{C}^{\infty}(M)$ is called a **derivation** (as distinct from a derivation *at* $p$, defined in [[Derivation of Smooth Map at point and Tangent Vector]]) if it is **linear** over $\mathbb{R}$ and satisfies the **Leibnitz rule**
>$$
> \begin{align}
> X(fg) &= f\, X(g) + g\, X(f),  \qquad \forall\,\, f,g \in \mathcal{C}^{\infty}(M)
> \end{align}
>$$ 

>[!info]
>As the *tangent vector* itself is a *linear functional* on $\mathcal{C}^{\infty}(M)$, the **vector field** $X$ is a **linear operator** that maps *a function* to *another function* on $\mathcal{C}^{\infty}(M)$. 
>
>The **value** of function $Xf$ at $p$ is **the directional derivative** of $f$ *along with* $X(p)$ *at point* $p$.


## Explanation

>[!info]
>Be careful not to confuse the notations $fX$ and $Xf$:
> 
>-  the former $fX$ is **the smooth vector field** on $U$ obtained by *multiplying the vector field* $X$ by a smooth function $f$,
>-  while the latter $Xf$ is **the real-valued function** on $U$ obtained by *applying* the vector field $X$ *to* the smooth function $f$.

>[!info]
>Because the action of a tangent vector on a function is determined by the values of the function in an arbitrarily *small neighborhood*, it follows that $Xf$ is **locally determined**. 
>
>In particular,  for any open subset $V \subseteq U$, 
>$$
> \begin{align}
> (X\,f)\bigr|_{V} &= X\left(f \bigr|_{V}\right).
> \end{align}
>$$ 


>[!info]
>The next proposition shows that **derivations** *of* $\mathcal{C}^{\infty}(M)$ can be **identified** with **smooth vector fields**:

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary. 
>
>A map $D: \mathcal{C}^{\infty}(M) \rightarrow \mathcal{C}^{\infty}(M)$ is a **derivation** *if and only* if it is of the form $$Df = Xf$$ for *some smooth vector field* $X \in \mathfrak{X}(M)$.

>[!info]
>Because of this result, we sometimes **identify** **smooth vector fields** on $M$ with **derivations** of $\mathcal{C}^{\infty}(M)$, using the same letter for both
>- the *vector field* (thought of as a **smooth map** from $M$ to $TM$ ) and 
>- the *derivation* (thought of as a **linear map** from $\mathcal{C}^{\infty}(M)$ to itself)


## Lie Bracket of Vector Fields

- [[Lie Bracket of Vector Fields]]



-----------
##  Recommended Notes and References


- [[Derivation of Smooth Map at point and Tangent Vector]]
  
  
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Smooth Vector Field on Manifold]]
- [[Vector Field on Manifold]]


- [[Vector Space over a Field]]

- [[Introduction to Smooth Manifolds by Lee]]