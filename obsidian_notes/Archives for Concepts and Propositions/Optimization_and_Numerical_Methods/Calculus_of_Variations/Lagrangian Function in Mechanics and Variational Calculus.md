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
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$, and 
>- $X$ is a subset in the *space of smooth functions* $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$,
>- and $u \in X$ be a vector-valued  *smooth function* in $\Omega$.
>- Note that $u(x)\in \mathbb{R}^{m}$ describes a *parameterize smooth curve* in $\mathbb{R}^{m}$.
>
>Moreover, define the **Lagrangian** function $$L:  \mathbb{R}^{n} \times \mathbb{R}^{m} \times \mathbb{R}^{m \times n}   \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathbb{R}^{n}\times \mathbb{R}^{m}\times \mathbb{R}^{m\times n}$
>- Then there exists some $\delta >0$ such that the **Lagrangian** $$L(x, v(x), Dv(x))$$ is defined in all $x\in \bar{\Omega}$, and for all $v\in \mathcal{C}^{1}(\bar{\Omega}, \mathbb{R}^{m})$ with $\lVert v - u \rVert_{\mathcal{C}^{1}(\Omega)} < \delta$
>- For simplicity, we denote $$L(x, u(x), Du(x) )$$ where $Du(x) = [\partial_{j}u^{i}]_{i,j}$ is the *Jacobian*.

^22c1fa

- [[First Variation of Functional]] 
- [[Euler–Lagrange Equations]]
- [[Necessary Condition for Relative Extremum of Functional]]
- [[Jacobian Matrix and Jacobian Determinant]]

### $k$-particle system

>[!important] Definition
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$.
>
>Suppose that there are a set of $k$ smooth functions on $\Omega$ $$u_{1}(x) \,{,}\ldots{,}\,u_{k}(x) \in X \subset \mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$$
>- It corresponds to a *system of $k$ particles* or *parameterized curves* in $\mathbb{R}^{m}$.
>
>Moreover, define the **Lagrangian** function for the **$k$-particle system**  $$L:  \mathcal{U} := \mathbb{R}^{n} \times \underbrace{ \mathbb{R}^{m} \,{\times}\ldots{\times}\,\mathbb{R}^{m} }_{ k }  \times \underbrace{ \mathbb{R}^{m \times n} \,{\times}\ldots{\times}\,\mathbb{R}^{m \times n} }_{k}  \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathcal{U}$
>
>Denote $$L(x, U(x), DU(x)) := L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), Du_{1}(x)\,{,}\ldots{,}\,Du_{k}(x) )$$ where $Du_{i}(x) = [\partial_{j}u_{i}^{s}(x)]_{s,j}$ is the *Jacobian*.

^d094aa

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

### Classical Mechanics

>[!important]
>In **classical mechanic**, the *Lagrangian* is the **difference** between the **kinetic energy** $T$ and **potential energy** $U$
>$$
>L = T - U
>$$


## Euler-Lagrange Equation

![[Euler–Lagrange Equations#^000423]]

- [[Euler–Lagrange Equations]]

>[!important] 
>Given the **Lagrangian** $$L(x, U(x), DU(x)) := L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), u_{1}'(x)\,{,}\ldots{,}\,u_{k}'(x) ),$$
>the **Euler-Lagrange equation** provides the following equality
>$$
>\begin{align*}
>\frac{d}{dx} L_{u_{i}'}  &= L_{u_{i}}, \quad i=1\,{,}\ldots{,}\,k
>\end{align*}
>$$

![[Euler–Lagrange Equations#^91e132]]




-----------
##  Recommended Notes and References


- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Coordinate Representation of Differential at Point]]


- [[Ordinary Differential Equations by Chicone]] pp 225
- [[Calculus of Variations by Gelfand]]

