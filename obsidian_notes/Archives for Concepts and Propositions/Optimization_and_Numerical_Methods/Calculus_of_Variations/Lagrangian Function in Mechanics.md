---
tags:
  - concept
  - math/differential_equation
  - math/calculus_of_variations
keywords:
  - euler_lagrange_equation
  - calculus_variation
topics:
  - differential_equation
  - variational_calculus
name: Lagrangian Function in Mechanics
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Lagrangian Function in Mechanics

### $1$-particle system

>[!important] Definition
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$, and $u(x) \in X$ be a vector-valued  *smooth function* in $\Omega$, where $X$ is a subset in the *space of smooth functions* $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$. 
>- $u$ describes the position of a *particle* or *parameterize curve*.
>
>Moreover, define the **Lagrangian** functional $$L:  \mathbb{R}^{n} \times \mathbb{R}^{m} \times \mathbb{R}^{m \times n}   \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathbb{R}^{n}\times \mathbb{R}^{m}\times \mathbb{R}^{m\times n}$
>- Then there exists some $\delta >0$ such that the **Lagrangian** $$L(x, v(x), Dv(x))$$ is defined in all $x\in \bar{\Omega}$, and for all $v\in \mathcal{C}^{1}(\bar{\Omega}, \mathbb{R}^{m})$ with $\lVert v - u \rVert_{\mathcal{C}^{1}(\Omega)} < \delta$
>- For simplicity, we denote $$L(x, u(x), Du(x) )$$ where $Du(x) = [\partial_{j}u^{i}]_{i,j}$ is the *Jacobian*.

- [[First Variation of Functional]] 
- [[Euler–Lagrange Equations]]
- [[Necessary Condition for Relative Extremum of Functional]]
- [[Coordinate Representation of Differential at Point]]

### $k$-particle system

>[!important] Definition
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$.
>
>Suppose that there are a set of $k$ smooth functions (*parameterized curve*)  $$u_{1}(x) \,{,}\ldots{,}\,u_{k}(x) \in X \subset \mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$$ in $\Omega$ 
>
>Moreover, define the **Lagrangian** functional for the **$k$-particle system**  $$L:  \mathcal{U} := \mathbb{R}^{n} \times \underbrace{ \mathbb{R}^{m} \,{\times}\ldots{\times}\,\mathbb{R}^{m} }_{ k }  \times \underbrace{ \mathbb{R}^{m \times n} \,{\times}\ldots{\times}\,\mathbb{R}^{m \times n} }_{k}  \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathcal{U}$
>- For simplicity, we denote $$L(x, U(x), DU(x)) := L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), Du_{1}(x)\,{,}\ldots{,}\,Du_{k}(x) )$$ where $Du_{k}(x) = [\partial_{j}u_{k}^{i}]_{i,j}$ is the *Jacobian*.

- [[Parameterized Curve on Manifold]]


## Explanation


>[!important]
>The above **Lagrangian formalism** describe a **1-particle system** as a **parameterized curve** $u$ and its **phase-space representation** $$(x, u, Du)$$ on surface $\mathcal{S}$.
>
>In physics, 
>- $x = t\in \mathbb{R}$ represent **time**.  
>- $u(t)\in \mathbb{R}^{m}$ is the **position** of particle in $\mathcal{S} \subset\mathbb{R}^{m}$
>- $Du \in \mathbb{R}^{m\times 1}$ is the **momentum** or **velocity** of particle in $T_{u}\mathcal{S}$
>  
>




-----------
##  Recommended Notes and References


- [[Hamiltonian Function in Mechanic]]

- [[Ordinary Differential Equations by Chicone]] pp 225
- [[Calculus of Variations by Gelfand]]

