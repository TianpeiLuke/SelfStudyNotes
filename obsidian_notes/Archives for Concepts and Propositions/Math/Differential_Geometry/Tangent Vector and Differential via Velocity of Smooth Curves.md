---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tangent_vector
  - curve_on_manifold
  - velocity_curve
topics:
  - differential_geometry
name: Tangent Vector as Velocity of Smooth Curves
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Tangent Vector as Velocity of Smooth Curves

![[Parameterized Curve on Manifold#^fa255d]]

![[Velocity of Smooth Curves#^da57a9]]



>[!important] Proposition
>Suppose $\mathcal{M}$ is a **smooth manifold** with or without boundary and $p \in \mathcal{M}$.
>
>Every $v\in T_{p}\mathcal{M}$ is the **velocity of some smooth curve** in $\mathcal{M}$.

- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Velocity of Smooth Curves]]
- [[Tangent Space as Finite Dimensional Vector Space]]
- [[Introduction to Smooth Manifolds by Lee]] pp 70

## Explanation

## Composition

>[!important] Proposition (The Velocity of a Composite Curve)
>Let $F: \mathcal{M} \to \mathcal{N}$ be a *smooth map*, and let $\gamma: J \to \mathcal{M}$ be a *smooth curve*.
>
>For any $t_{0} \in J$, the **velocity** at $t=t_{0}$ of the **composite curve** $F \circ \gamma: J\to \mathcal{N}$ is given by
>$$
>\left(F \circ \gamma \right)'(t_{0}) = dF\left(\gamma'(t_{0})\right).
>$$

- [[Differential of a Smooth Map at Point]]

>[!important] Corollary (Computing the Differential Using a Velocity Vector)
>Suppose $F: \mathcal{M} \to \mathcal{N}$ is a *smooth map*, $p \in \mathcal{M}$, and $v\in T_{p}\mathcal{M}$. 
>
>Then 
>$$
>dF_{p}(v) = \left(F \circ \gamma\right)'(0)
>$$
>for any *smooth curve* $\gamma: J \to \mathcal{M}$ such that $0 \ni J$, $\gamma(0)=p$ and $\gamma'(0) = v.$

## Tangent Vectors as Equivalence Classes of Curves

- [[Introduction to Smooth Manifolds by Lee]] pp 72

### Equivalence Relation on Set of all Smooth Curves

>[!important] Definition
>Suppose $p \in \mathcal{M}$. Let $$G_{p, \mathcal{M}} = \left\{ \gamma: J \to \mathcal{M}:\;\; 0\ni J \subset \mathbb{R}, \;  \gamma(0) = p \right\} $$ be the set of all smooth curves in $\mathcal{M}$ that contains $p$.
>
>For two curves $\gamma_{1}, \gamma_{2} \in G_{p, \mathcal{M}}$, define a **relation** $$\gamma_{1} \sim \gamma_{2} \iff (f \circ \gamma_{1})'(0) = (f \circ \gamma_{2})'(0)$$  for all smooth function $f \in \mathcal{C}^{\infty}(\mathcal{M})$ defined on small neighborhood of $p$. 
>- We can show that the relation above is an **equivalence relation.**
>
>Denote the set of *equivalence classes* (i.e. the **quotient set**) as $\mathcal{V}_{p}\mathcal{M}$, i.e.
>$$
>\mathcal{V}_{p}\mathcal{M} := G_{p, \mathcal{M}}  \;/ \sim.
>$$
>The **tangent space** to $\mathcal{M}$ at $p$ is defined as $\mathcal{V}_{p}\mathcal{M}.$ 
>- A **tangent vector** is the equivalence class
>$$
> [\gamma] \in \mathcal{V}_{p}\mathcal{M}
>$$

^673c21

- [[Equivalence Relation]]
- [[Equivalence Class]]
- [[Quotient Set]]

>[!important] Definition
>Suppose $F: \mathcal{M} \to \mathcal{N}$ is a *smooth map*, $p \in \mathcal{M}$, and $[\gamma]\in \mathcal{V}_{p}\mathcal{M}$. 
>
>The **differential** of $F$ **at** $p$, $dF_{p}: \mathcal{V}_{p}\mathcal{M} \to \mathcal{V}_{F(p)}\mathcal{M}$, is defined by  
>$$
>[\gamma] \mapsto [F \circ \gamma]
>$$

^de2033

- [[Differential of a Smooth Map at Point]]

>[!important] Definition
>For any smooth curve $\gamma: J \to \mathcal{M}$ where $0 \ni J$ and $\gamma(0)= p$, the **velocity** of $\gamma$ **at** $0$ is just the *equivalence class* $[\gamma] \in \mathcal{V}_{p}\mathcal{M}.$
>$$
>\gamma'(0) = [\gamma] \in \mathcal{V}_{\gamma(0)}\mathcal{M}. 
>$$
>
>The **velocity** of $\gamma$ **at** $t_{0} \ni J$ can be defined as 
>$$
>\gamma'(t_{0}) = [\gamma] \in \mathcal{V}_{\gamma(t_{0})}\mathcal{M}. 
>$$ 
>where $$\gamma_{t_{0}}(t) = \gamma(t_{0} + t).$$

>[!important] Proposition
>Suppose $\mathcal{M}$ is a *smooth manifold* with or without boundary and $p \in \mathcal{M}$. 
>
>Let $\mathcal{V}_{p}\mathcal{M}$ be the set of **equivalence classes** of *smooth curves* starting at $p$ under the relation $$\gamma_{1} \sim \gamma_{2} \iff (f \circ \gamma_{1})'(0) = (f \circ \gamma_{2})'(0)$$  for all smooth function $f \in \mathcal{C}^{\infty}(\mathcal{M})$ defined on small neighborhood of $p$. 
>
>The map 
>$$
>\Psi: \mathcal{V}_{p}\mathcal{M} \to T_{p}\mathcal{M} 
>$$
>defined by
>$$
>\Psi[\gamma] = \gamma'(0)
>$$
>is *well-defined* and **bijective**.

- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Velocity of Smooth Curves]]
- [[Bijective Function and Inverse Function]]
- [[Introduction to Smooth Manifolds by Lee]] pp 76


-----------
##  Recommended Notes and References

- [[Parameterized Curve on Manifold]]
- [[Smooth Manifold]]
- [[Tangent Space Definition and Development]]


- [[Introduction to Smooth Manifolds by Lee]]