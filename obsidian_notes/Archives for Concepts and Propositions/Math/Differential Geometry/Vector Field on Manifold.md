---
tags:
  - concept
  - math/differential_geometry
keywords:
  - vector_field
topics:
  - differential_geometry
name: Vector Field
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Vector Field on Manifold

>[!important] Definition
>If $M$ is a *smooth manifold* with or without boundary, a **vector field** on $M$ is a **section (right inverse)** *of the map* $$\pi: TM \rightarrow M.$$ 
>
>More concretely, a **vector field** is a *continuous map* $X: M \rightarrow TM$, usually written $p \mapsto X_p$, with the property that
>$$
> \begin{align}
> \pi \circ X = \text{Id}_{M},
> \end{align}
>$$  
>or **equivalently**, $X_p \in T_{p}M$ for each $p \in M$.

- [[Section of Continuous Function]]
- [[Tangent Bundle]]


>[!info]
>We write the **value** of $X$ **at** $p$ as $X_p$ instead of $X(p)$ to be *consistent with our notation* for elements of the tangent bundle, as well as to *avoid conflict with the notation* $v(f)$ for the *action of a vector* *on a function*.

## Explanation

>[!info]
>A **vector field** is seen as a **global generalization** of a *tangent vector*. 
>
>In differential geometry, it is the *vector field* that *of major concern* not tangent vector *at specific point*.



>[!info]
>Vector field can be visualized as *a collection of* **arrows** *on the surface of manifold*, and each arrow has its **origin** *attached* to a point in the manifold. The **direction** of arrows corresponds to the **tangent directions** at that point.


## Compare Vector Field with Tangent Vectors and Diferentials

>[!important]
>We can compare several related concepts:
>>[!info]
>>**Tangent vector** $v \in T_{p}M$ is both a **geometric tangent vector**, i.e. the tangent direction for some curve on $M$ passing $p$, and a **derivation** at $p$ defined on $\mathcal{C}^{\infty}(M)$ that satisfies the product rule. For the latter case, $v$ is a *linear functional* that act on functions $f \in \mathcal{C}^{\infty}(M)$.  $v(f)$ induces the *directional derivatives* of $f$ along $v$ and **derivation** at $p$.
> 
>>[!info]
>>The **differential** of $F: M\rightarrow N$ at $p$, $dF_{p}$, is a *linear operator* from $T_{p}M$ to $T_{p}N$. $dF_{p}$ maps a *tangent vector* at $p$ *in* $M$ to a *tangent vector* at $F(p)$ *in* $N$. Since tangent vectors are functions, $dF_{p}$ is also a *linear functional* if $F: M\rightarrow \mathbb{R}$. $dF_{p}(v) \in T_{F(p)}N$ can act on a function on $N$ to have $dF_{p}(v)(f)$.
> 
>>[!info]
>>The **vector field** $X$ is a *continuous* map from a *point* $p \in M$ to a *tangent vector* $X_p = v \in T_{p}M$. Thus for smooth function $f$ on $M$, $X_{p}f$ is a *real-value*, i.e. the *directional derivative* of $f$ along $v=X_{p}.$  A vector field $X$ is also a **derivation operator** on $\mathcal{C}^{\infty}(M)$. It maps a *smooth function* $f$ to a *new smooth function* $Xf$ which at each point is $X_{p}f$. A vector field is a **global generalization** of a tangent vector. 
> 

## Smooth Vector Field and Rough Vector Field

- [[Smooth Vector Field on Manifold]]

## Vector Field as Derivation Operator on Smooth Function Space

- [[Vector Fields as Total Derivation of Smooth Maps]]
- [[Derivation of Smooth Map at point and Tangent Vector]]

## Compare with Affine Space

>[!info]
>A vector field can be defined on *the vector space* of **free vectors** that is associated with the **affine space**.
>
>$TM$ serve as the role of such free vector space for general smooth manifolds.

- [[Affine Space]]



-----------
##  Recommended Notes and References

- [[Tangent Bundle]]
- [[Derivation of Smooth Map at point and Tangent Vector]]

- [[Section of Continuous Function]]

- [[Introduction to Smooth Manifolds by Lee]]