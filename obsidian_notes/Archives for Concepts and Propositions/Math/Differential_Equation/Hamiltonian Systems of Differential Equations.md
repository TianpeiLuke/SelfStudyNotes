---
tags:
  - concept
  - math/differential_equation
keywords:
  - hamiltonian_system_ode
topics:
  - differential_equation
name: Hamiltonian Systems of Differential Equations
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Hamiltonian Systems of Differential Equations

![[Hamiltonian Function in Mechanic and Variational Calculus#^614926]]

- [[Hamiltonian Function in Mechanic and Variational Calculus]]

>[!important] Definition
>Let  $H: \mathbb{R}^{n} \times \mathbb{R}^{n} \to \mathbb{R}$ be a *smooth function*, called **Hamiltonian**, given by
>$$
>(q_{1} \,{,}\ldots{,}\,q_{n}, p_{1} \,{,}\ldots{,}\,p_{n}) \mapsto H(q_{1} \,{,}\ldots{,}\,q_{n}, p_{1} \,{,}\ldots{,}\,p_{n})
>$$
>and define the associated **Hamiltonian system** on $\mathbb{R}^{2n}$ with *Hamiltonian* $H$
>$$
>\left\{\begin{align*}
> \frac{d}{dt} q_{i} &= \dfrac{ \partial H }{ \partial p_{i} }, \quad i=1 \,{,}\ldots{,}\, n \\[5pt]
> \frac{d}{dt} p_{i} &= - \dfrac{ \partial H }{ \partial q_{i} }, \quad i=1 \,{,}\ldots{,}\, n
>\end{align*}
>\right.
>$$
>Note that the **dimension** of the *phase space* of a **Hamiltonian system** is required to be **even**. 
>
>We can represent it in compact form
>$$
>\frac{d}{dt} z = J\,\nabla_{z} H 
>$$
>where $z = (q, p)$, and 
>$$
>J = \left[\begin{array}{cc}
> 0 & I\\ 
> - I & 0
>\end{array}\right] \in \mathbb{R}^{2n \times 2n}
>$$
>is a *skew-symmetric permutation matrix*.

^ad0948

- [[Symplectic Matrix]]
- [[Homogeneous Linear Differential Equations]]
- [[Gradient Flow in Euclidean Space]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Skew-Hermitian and Skew-Symmetric Matrix]]
- [[Ordinary Differential Equations by Chicone]] pp 38


## Explanation

>[!example]
>A typical example of Hamiltonian system consists of the **potential** and **kinetic energy**
>$$
>H(q, p) = U(q) + K(p)
>$$
>where $U(q)$ is the **potential energy** and $K(p)$ is the **kinetic energy**.
>
>For instance 
>$$
>K(p) = \frac{1}{2}\left\langle M^{-1}p , p \right\rangle
>$$
>where $M \succ 0$ is a **symmetric positive definite matrix**.

- [[Positive Semidefinite Transformation]]


## Configuration Space

>[!important] Definition
>- The **configuration space** for a classical mechanical system is the space consisting of all possible *positions* of the system.
>
>
 >- The corresponding *Hamiltonian system* is said to have **$n$ degrees of freedom** if the configuration space is *locally specified* by $n$ coordinates $(q_{1} \,{,}\ldots{,}\,q_{n})$. 

## Phase Space

>[!important] Definition
>- The **phase space** of a *Hamiltonian system* is the subset of $\mathbb{R}^{n} \times \mathbb{R}^{n}$ of all *positions* and *momenta* specified by the coordinates $(q_{1} \,{,}\ldots{,}\,q_{n}, p_{1} \,{,}\ldots{,}\,p_{n})$.  The **dimension** of the *phase space* is therefore *even*; it is the space in which the Hamiltonian system evolves. 
>
>- The **state space** is also a subset of $\mathbb{R}^{n} \times \mathbb{R}^{n}$, but it is the space of *positions and velocities* with the coordinates $(q_{1} \,{,}\ldots{,}\,q_{n}, \dot{q}_{1} \,{,}\ldots{,}\,\dot{q}_{n}).$

^5f6725

- [[Tangent Bundle]]
- [[Phase Space of Hamiltonian Systems of Differential Equations]]

>[!important] 
>The three most important properties of the Hamiltonian dynamic are
>- *Hamiltonian dynamics* **conserves the Hamiltonian**
>- *Hamiltonian dynamics* **conserves the volume** in the **phase space**.
>- *Hamiltonian dynamics* is **time-reversible**.

^46b385


## Lagrangian Mechanics

- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Legendre Transform]]

## Energy Surface

>[!important] Definition
>For $c \in \mathbb{R}$ and the *Hamiltonian*  $H: \mathbb{R}^{n} \times \mathbb{R}^{n} \to \mathbb{R}$, the corresponding **energy surface** *with energy* $c$ is defined to be the set $$\mathcal{S}_{c} = \{(q, p) \in \mathbb{R}^{n} \times \mathbb{R}^{n}  : H(q, p) = c \}.$$
>
>If
>$$\text{grad }H(q, p) = 0, \quad  \forall (q, p) \in  \mathcal{S}_{c},$$ 
>then the set $\mathcal{S}_{c}$ is called a **regular energy surface.**

- [[Regular Space]]
- [[Gradient of Smooth Map]]







-----------
##  Recommended Notes and References

- [[Hamilton-Jacobi Equation]]
- [[Hamiltonian Function in Mechanic and Variational Calculus]]

- [[Stable Manifold]]
- [[Smooth Manifold]]

- [[Vector Field as Infinitesimal Generator of Local Flow]]

- [[Ordinary Differential Equations]]


- [[Ordinary Differential Equations by Chicone]] pp 38
- [[Introduction to Smooth Manifolds by Lee]]