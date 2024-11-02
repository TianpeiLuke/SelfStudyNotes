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
name: Hamiltonian Function in Mechanic
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Hamiltonian Function in Mechanic

### k-Particle System, One-Dimensional, Univariate Case

![[Lagrangian Function in Mechanics and Variational Calculus#^d094aa]]

>[!important] Definition (1-Dimensional Case)
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}$.
>
>Suppose that there are a set of $k$ smooth functions on $\Omega$ $$u_{1}(x) \,{,}\ldots{,}\,u_{k}(x) \in X \subset \mathcal{C}^{1}(\Omega, \mathbb{R})$$
>- It corresponds to a *system of $k$ particles* or *parameterized curves* in $\mathbb{R}$.
>
>Moreover, define the *Lagrangian* function for the **$k$-particle system**  $$L:  \mathcal{U} := \mathbb{R} \times \underbrace{ \mathbb{R} \,{\times}\ldots{\times}\,\mathbb{R} }_{ k }  \times \underbrace{ \mathbb{R} \,{\times}\ldots{\times}\,\mathbb{R} }_{k}  \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathcal{U}$
>- Denote $$L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), u'_{1}(x)\,{,}\ldots{,}\,u'_{k}(x) )$$ 
>- Define the *objective functional* $$J(u_{1}\,{,}\ldots{,}\,u_{k}) := \int_{\Omega} L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), u'_{1}(x)\,{,}\ldots{,}\,u'_{k}(x) ) \,dx$$
>
>Define variable $$p_{i} := \frac{ \partial  }{ \partial u'_{i} }L, \quad i=1\,{,}\ldots{,}\,k $$
>- Suppose that the *Jacobian matrix* $$\frac{ \partial (p_{1}\,{,}\ldots{,}\,p_{k}) }{ \partial (u_{1}' \,{,}\ldots{,}\, u_{k}') } = \left[ \frac{ \partial^2  }{ \partial u'_{i} \partial u'_{j}}L \right] $$ is *non-singular*.
>  
>Define the **Hamiltonian** *function* corresponding to the functional $J$ as
>$$
>\begin{align*}
>&H(x, u_{1}\,{,}\ldots{,}\,u_{k}, \,p_{1}\,{,}\ldots{,}\,p_{k} ) \\[5pt]
>&= \sum_{i=1}^{k}p_{i}\,u_{i}' - L(x, u_{1}, \,{,}\ldots{,}\,u_{k}, u'_{1}\,{,}\ldots{,}\,u'_{k} ) 
>\end{align*}
>$$
>- The set of variables $$(x, u_{1}\,{,}\ldots{,}\,u_{k}, \,p_{1}\,{,}\ldots{,}\,p_{k})$$ is called the **canonical variables** corresponding to $J$.
>- In ODE or physics, the *space of canonical variables* of Hamiltonian is called the **phase space**
>- Substitute the transformation between $p$ and $L$, we have 
>$$
>\begin{align*}
>&H(x, u_{1}\,{,}\ldots{,}\,u_{k}, \,p_{1}\,{,}\ldots{,}\,p_{k} ) \\[5pt]
>&\equiv \sum_{i=1}^{k}u_{i}'\,(\partial_{u_{i}'}L) - L(x, u_{1}, \,{,}\ldots{,}\,u_{k}, u'_{1}\,{,}\ldots{,}\,u'_{k} )\\[5pt]
>&:= E_{L}(x, u_{1}, \,{,}\ldots{,}\,u_{k}, u'_{1}\,{,}\ldots{,}\,u'_{k})
>\end{align*}
>$$

^614926

- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Phase Space of Hamiltonian Systems of Differential Equations]]

>[!important] Definition
>$$p_{i} := \frac{ \partial  }{ \partial u'_{i} }L, \quad i=1\,{,}\ldots{,}\,k $$ defines the transformation between **Lagrangian** and **Hamiltonian.**


### k-Particle System, Multi-Dimensional, Multivariate Case

![[Euler–Lagrange Equations#^91e132]]


>[!important] Definition ($m$-Dimensional Case)
>Let $\Omega$ be a *bounded open domain* in $\mathbb{R}^{n}$.
>
>Suppose that there are a set of $k$ smooth functions on $\Omega$ $$u_{1}(x) \,{,}\ldots{,}\,u_{k}(x) \in X \subset \mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$$
>- It corresponds to a *system of $k$ particles* or *parameterized curves* in $\mathbb{R}^{m}$.
>
>Moreover, define the *Lagrangian* functional for the **$k$-particle system**  $$L:  \mathcal{U} := \mathbb{R}^{n} \times \underbrace{ \mathbb{R}^{m} \,{\times}\ldots{\times}\,\mathbb{R}^{m} }_{ k }  \times \underbrace{ \mathbb{R}^{m\times n} \,{\times}\ldots{\times}\,\mathbb{R}^{m\times n}  }_{k}  \to \mathbb{R}$$ as a *real-valued $\mathcal{C}^{1}$-smooth function* on an open set of $\mathcal{U}$
>- Denote $$L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), Du_{1}(x)\,{,}\ldots{,}\,Du_{k}(x) )$$  where $Du_{i}$ is the *Jacobian matrix*.
>- Define the *objective functional* $$J(u_{1}\,{,}\ldots{,}\,u_{k}) := \int_{\Omega} L(x, u_{1}(x), \,{,}\ldots{,}\,u_{k}(x), Du_{1}(x)\,{,}\ldots{,}\,Du_{k}(x) ) \,dx$$
>  
>Define the **Hamiltonian** *functional* corresponding to the functional $J$ as
>$$
>\begin{align*}
>&H(x, u_{1}\,{,}\ldots{,}\,u_{k}, \,p_{1}\,{,}\ldots{,}\,p_{k} ) \\[5pt]
>&= \sum_{i=1}^{k}\left\langle p_{i} , Du_{i} \right\rangle_{F} - L(x, u_{1}, \,{,}\ldots{,}\,u_{k}, Du_{1}\,{,}\ldots{,}\,Du_{k} ) \\[5pt]
>\end{align*}
>$$
>- The set of variables $$(x, u_{1}\,{,}\ldots{,}\,u_{k}, \,p_{1}\,{,}\ldots{,}\,p_{k})$$ is called the **canonical variables** corresponding to $J$.
>- Note that for $A, B\in \mathbb{R}^{m\times n}$, $$\left\langle A , B \right\rangle_{F} = \text{tr}(A^{T}B) = \sum_{i}\sum_{k}A_{k,i}B_{k,i}$$

- [[Euler–Lagrange Equations]]
- [[Jacobian Matrix and Jacobian Determinant]]
- [[Matrix CookBook by Petersen]]

>[!important]
>
> $$p_{i} := \frac{ \partial  }{ \partial Du_{i} }L := [\partial_{j}u_{i}^{s}]_{s,j} \in \mathbb{R}^{m \times n}, \quad i=1\,{,}\ldots{,}\,k $$
> defines the **transformation map** between **Lagrangian** and **Hamiltonian.**


### Energy Functional

>[!important] Definition
>Let $u_{i}\in \mathcal{C}^{2}(\Omega, \mathbb{R}^{m}), i=1\,{,}\ldots{,}\,k$  be $k$ smooth maps where $\Omega \subset \mathbb{R}^{n}.$
>
>The functional 
>$$
>\begin{align*}
>E_{L}(x, U, DU) &:= E_{L}(x, u_{1}, \,{,}\ldots{,}\,u_{k}, Du_{1}\,{,}\ldots{,}\,Du_{k}) \\[5pt]
>&:= \sum_{i=1}^{k}\left\langle \frac{ \partial L}{ \partial Du_{i} }  , Du_{i} \right\rangle_{F} - L(x, u_{1}, \,{,}\ldots{,}\,u_{k}, Du_{1}\,{,}\ldots{,}\,Du_{k} )
>\end{align*}
>$$
>is called the **energy functional.**
>- The above formula can be expanded as $$\begin{align*}E_{L}(x, U, DU)&=\sum_{i=1}^{k}\sum_{j=1}^{n}\sum_{s=1}^{m} (\partial_{j}u_{i}^{s})\frac{ \partial L }{ \partial (\partial_{j}u_{i}^{s}) }  - L(x, \left\{ u_{i} \right\}_{i},\, \left\{  \partial_{j}u_{i}^{s}\right\}_{i,j,s} )\end{align*}$$

^eb8491

- [[Energy Functional for Probabilistic Graphical Model]]

>[!info]
>The Hamiltonian satisfies 
>$$
>\begin{align*}
>&H\left( x, u_{1}\,{,}\ldots{,}\,u_{k}, \,\frac{ \partial L}{ \partial Du_{1} }\,{,}\ldots{,}\, \frac{ \partial L}{ \partial Du_{k} } \right) \\[5pt]
>&:= E_{L}(x, u_{1}, \,{,}\ldots{,}\,u_{k}, Du_{1}\,{,}\ldots{,}\,Du_{k})
>\end{align*}
>$$

>[!important]
>The **energy functional** for $u_{i}\in \mathcal{C}^2(\Omega, \mathbb{R})$, $\Omega \subset \mathbb{R}$ corresponds to the *Lagrangian* is
>$$
>\begin{align*}
>&E_{L}(x, u_{1}, \,{,}\ldots{,}\,u_{k}, u'_{1}\,{,}\ldots{,}\,u'_{k})\\[5pt]
>&\equiv \sum_{i=1}^{k}u_{i}'\,(\partial_{u_{i}'}L) - L(x, u_{1}, \,{,}\ldots{,}\,u_{k}, u'_{1}\,{,}\ldots{,}\,u'_{k} )
>\end{align*}
>$$


## Explanation

![[Legendre Transform#^ee6fff]]

>[!important]
>For fixed $x$ and $u$, define the **Lagrangian** $$\hat{L}(u') := L(x, u, u')$$
>
>The **Legendre transform** of the **Lagrangian** is 
>$$
>\begin{align*}
> H(u, p) := \hat{H}(p) := \sup_{u'}\left\{    \left\langle p ,  u' \right\rangle - \hat{L}(u')\right\}
>\end{align*}
>$$
>which is the **Hamiltonian** with optimal solution $$p = \nabla\hat{L}(u')$$

- [[Legendre Transform]]
- [[Lagrangian Function in Mechanics and Variational Calculus]]


## Hamiltonian System

![[Hamiltonian Systems of Differential Equations#^ad0948]]

- [[Hamiltonian Systems of Differential Equations]]


-----------
##  Recommended Notes and References



- [[First Variation of Functional]]



- [[Ordinary Differential Equations by Chicone]] pp 225
- [[Calculus of Variations by Gelfand]] pp 58
- Wikipedia [Hamiltonian_mechanics](https://en.wikipedia.org/wiki/Hamiltonian_mechanics)