---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_space
topics:
  - differential_geometry
name: Development of Tangent Space
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Tangent Space $T_{p}M$

>[!important] Definition 
>The set of *all derivations* of $\mathcal{C}^{\infty}(M)$ at $p$, denoted by $T_{p}M$, is a *vector space* called the **tangent space** to $M$ at $p$. 
>
>An element of $T_{p}M$ is called a **tangent vector** at $p$.


>[!info]
>The central idea of calculus is **linear approximation**. In order to make sense of **calculus on manifolds**, we need to introduce the **tangent space** to a manifold at a point, which we can think of as a sort of *"linear model"* for the manifold near the point. 

## Tangent Space in Euclidean Space

### Geometric Tangent Space in Euclidean Space

>[!info]
>Define the **geometric tangent space** to $\mathbb{R}^n$ at $a$, denoted by $\mathbb{R}_{a}^n$, to be the set $$\{a\} \times \mathbb{R}^n = \{(a, v):  v \in \mathbb{R}^n\}.$$ 
>
>A **geometric tangent vector** in $\mathbb{R}^n$ is an element of $\mathbb{R}_{a}^n$ for some $a \in \mathbb{R}^n$. 



>[!info]
>As a matter of notation, we *abbreviate* $(a, v)$ as $v_a$ (or sometimes $v|_a$ if it is clearer, for example if $v$ itself has a subscript).


>[!info]
 >We think of $v_a$ as the vector $v$ with its initial point at $a$.The set $\mathbb{R}_{a}^n$ is a real *vector space* under the natural operations
>   $$
> \begin{align*}
> v_a + w_a = (v + w)_a, \quad c\,v_a = (c\,v)_a.
> \end{align*}
> $$ 

>[!info]
>The vectors $e_i|_a$, $i = 1,\ldots,n$, are a basis for $\mathbb{R}_{a}^n$. In fact, as a *vector space*, $\mathbb{R}_{a}^n$ is essentially the same as $\mathbb{R}^n$ itself.


### Space of Derivations as a Finite-Dimensional Functional Space

>[!info]
> Let $T_{a}\mathbb{R}^n$ denote the *set of all derivations* of $\mathcal{C}^{\infty}(\mathbb{R}^n)$ at $a$. 
> 
> Clearly, $T_{a}\mathbb{R}^n$  is a **vector space** under the operations
> $$
> \begin{align*}
> (w_1 + w_2)(f)  = w_1(f) + w_2(f), \quad (c\,w)(f) = c\,w(f).
> \end{align*}
> $$

>[!info]
>Note that by definition, a **derivation** $w \in T_{a}\mathbb{R}^n$ is a **linear functional** on $\mathcal{C}^{\infty}(\mathbb{R}^n)$. Thus $T_{p}\mathbb{R}^{n}$ is a *functional space*.


- [[Derivation of Smooth Map at point and Tangent Vector]]


### Equivalence between Geometric Tangent Space and Space of Derivation Operations in $\mathbb{R}^n$

>[!info]
>The most important (and perhaps somewhat surprising) fact about $T_{a}\mathbb{R}^n$ is that it is **finite-dimensional**, and in fact is naturally **isomorphic** to the *geometric tangent space* $\mathbb{R}_{a}^n$ that we defined above.
> $$
> T_{a}\mathbb{R}^{n} \simeq \mathbb{R}^{n}
> $$

>[!important] Proposition
>
> Let $a \in \mathbb{R}^n$.
> 1. For each geometric tangent vector $v_a \in \mathbb{R}_{a}^n$, the map $D_v|_a: \mathcal{C}^{\infty}(\mathbb{R}^n) \rightarrow \mathbb{R}$ defined by following 
> $$
> \begin{align}
> D_v|_a(f) &= D_{v}(f(a)) = \frac{d}{dt}\Big|_{t=0}f(a + t\,v).
> \end{align}
> $$
> is a *derivation* at a. $D_v|_a(f)$ is called the **directional derivative** of $f$ *along vector* $v$ at point $a$. 
> 
> 2. The map $v_a \rightarrow D_v|_a$ is an **isomorphism** from $\mathbb{R}_{a}^n$ onto $T_{a}\mathbb{R}^n$.


>[!info]
>The above proposition connects *two distinct concepts* together via **isomorphism**:
>1. A **vector space** $\mathbb{R}_{a}^n$ at point $a$, which consists of all **geometric tangent vectors** $v_a$. 
>   
>   Each $v_a$ points to the **direction of tangent line** *at point* $a$
>   
>2. A **functional space** $T_{a}\mathbb{R}^{n}$ associated with point $a$, which consists of all **derivations** $w$. 
>   
>   Each derivation $w = D_v\big|_{a}$ is a **linear functional** that maps a *smooth function* on $\mathbb{R}^{n}$ to its **directional derivatives** *along vector* $v$.

- [[Bounded Linear Functional]]
- [[Bounded Linear Operator and Norm of Operator]]

## Extension to Smooth Manifold

- We can also reach to the isomorphism between a geometric tangent vector at $p$ on smooth manifold and a directional derivative along such geometric tangent vector at $p$

>[!info]
>$v\in T_p(M)$, then 
>- $v$ is a *tangent vector* of manifold $M$ at point $p \in M$
>- $v$ is a *linear functional* on any smooth maps on $M$, which take the *directional derivatives* of such smooth map at $p \in M$ along the tangent vector $v$
>  $$v(f) := \frac{d}{dt}\Big|_{t=0} f(p+ t\,v)$$

- [[Smooth Function on Smooth Manifold]]
- [[Vector Space over a Field]]
- [[Introduction to Smooth Manifolds by Lee]]

## Alternative Definition

- [[Tangent Vector as Velocity of Smooth Curves]]



-----------
##  Recommended Notes and References

- [[Tangent Space as Finite Dimensional Vector Space]]

- [[Introduction to Smooth Manifolds by Lee]]