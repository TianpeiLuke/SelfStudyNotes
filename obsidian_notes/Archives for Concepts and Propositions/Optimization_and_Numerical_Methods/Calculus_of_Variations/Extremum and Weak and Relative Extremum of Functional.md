---
tags:
  - concept
  - math/calculus_of_variations
  - optimization
  - math/functional_analysis
keywords:
  - weak_extremum_functional
  - extremum_functional
  - relative_extremum_functional
topics:
  - functional_analysis
  - variational_calculus
  - optimization
name: 
date of note: 2024-10-29
---

## Concept Definition

>[!important]
>**Name**: Extremum and Weak and Relative Extremum of Functional

![[First Variation of Functional#^d58f5c]]

- [[First Variation of Functional]]

### Strong Extremum

![[Fréchet Derivative and Strong Derivative in Banach Space#^8e4985]]

- [[Fréchet Derivative and Strong Derivative in Banach Space]]

>[!important] Definition
>Let 
>- $\mathcal{C}(\Omega, \mathbb{R}^{m})$ be the space of all *continuous functions* on an open domain $\Omega \subset \mathbb{R}^{n}$
>	- $\mathcal{C}(\Omega, \mathbb{R}^{m})$ is  *Banach space* with uniform norm topology $\lVert \cdot \rVert_{\mathcal{C}(\Omega)}$, i.e. $$\lVert f \rVert_{\mathcal{C}(\Omega)} := \sup_{x\in \Omega}\lVert f(x) \rVert  $$
>
>- Denote $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$ be the *space of continuous differentiable functions*. $$\mathcal{C}^{1}(\Omega) \subset \mathcal{C}(\Omega)$$
>	- $\mathcal{C}^{1}(\Omega)$ is a *Sobolev space* with norm $$\lVert f \rVert_{\mathcal{C}^1(\Omega)} := \sup_{x\in \Omega}\lVert f(x) \rVert + \sup_{x\in \Omega}\lVert Df(x) \rVert$$
>
>- Let $\mathcal{F}$ be a subset of $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$ and $J: \mathcal{F} \to \mathbb{R}$ is a functional on $\mathcal{F}$. 
>
>Then $u \in \mathcal{F}$ is called a **strong extremum** of $J$ if there exists some $\delta_{0} >0$ such that $$J(u) - J(v)$$ have the *same sign* for all $v\in \mathcal{F}$ satisfying $$\lVert u - v \rVert_{\mathcal{C}(\Omega)} < \delta_{0}.$$
>- $u$ is called **strong minimum**  if $$J(u) \le J(v), \quad \forall v\in \mathcal{F},\, \lVert u - v \rVert_{\mathcal{C}(\Omega)} < \delta_{0}$$
>- $u$ is called **strong maximum** if $$J(u) \ge J(v), \quad \forall v\in \mathcal{F},\, \lVert u - v \rVert_{\mathcal{C}(\Omega)} < \delta_{0}$$

- [[Uniform Topology on Metric Spaces]]
- [[Sobolev Space]]


### Weak Extremum

![[Gateaux Derivative and Weak Derivative in Banach Space#^bd289e]]


>[!important] Definition
>Let 
>- $\mathcal{C}(\Omega, \mathbb{R}^{m})$ be the space of all *continuous functions* on an open domain $\Omega \subset \mathbb{R}^{n}$
>	- $\mathcal{C}(\Omega, \mathbb{R}^{m})$ is  *Banach space* with uniform norm topology $\lVert \cdot \rVert_{\mathcal{C}(\Omega)}$, i.e. $$\lVert f \rVert_{\mathcal{C}(\Omega)} := \sup_{x\in \Omega}\lVert f(x) \rVert  $$
>
>- Denote $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$ be the *space of continuous differentiable functions*. $$\mathcal{C}^{1}(\Omega) \subset \mathcal{C}(\Omega)$$
>	- $\mathcal{C}^{1}(\Omega)$ is a *Sobolev space* with norm $$\lVert f \rVert_{\mathcal{C}^1(\Omega)} := \sup_{x\in \Omega}\lVert f(x) \rVert + \sup_{x\in \Omega}\lVert Df(x) \rVert$$
>
>- Let $\mathcal{F}$ be a subset of $\mathcal{C}^{1}(\Omega, \mathbb{R}^{m})$ and $J: \mathcal{F} \to \mathbb{R}$ is a functional on $\mathcal{F}$. 
>
>Then $u \in \mathcal{F}$ is called a **relative extremum** or  **weak extremum** of $J$ if there exists some $\delta_{0} >0$ such that $$J(u) - J(v)$$ have the *same sign* for all $v\in \mathcal{F}$ satisfying $$\lVert u - v \rVert_{\mathcal{C}^{1}(\Omega)} < \delta_{0}.$$
>- $u$ is called **relative minimum** or **weak minimum** if $$J(u) \le J(v), \quad \forall v\in \mathcal{F},\, \lVert u - v \rVert_{\mathcal{C}^{1}(\Omega)} < \delta_{0}$$
>- $u$ is called **relative maximum** or **weak maximum** if $$J(u) \ge J(v), \quad \forall v\in \mathcal{F},\, \lVert u - v \rVert_{\mathcal{C}^{1}(\Omega)} < \delta_{0}$$


^52d40d

- [[Unconstrained Local Minimization]]
- [[Gateaux Derivative and Weak Derivative in Banach Space]]

### Necessary Condition for Weak Extremum

![[Necessary Condition for Relative Extremum of Functional#^813689]]

- [[Necessary Condition for Relative Extremum of Functional]]


## Explanation

>[!info]
>Note that in **weak extremal** definition, we use the norm in *continuous differentiable function space* $$\lVert f \rVert_{\mathcal{C}^{1}(\Omega)} :=  \sup_{x\in \Omega}\lVert f(x) \rVert + \sup_{x\in \Omega}\lVert Df(x) \rVert $$ which is **weaker** than the *norm* in *continuous function space* $$\lVert f \rVert_{\mathcal{C}(\Omega)} := \sup_{x\in \Omega}\lVert f(x) \rVert$$




-----------
##  Recommended Notes and References



- [[Continuous Functions with Compact Support]]
- [[Banach Space]]


- [[Calculus of Variations by Gelfand]] pp 12 -  13
- [[Optimization by Vector Space Methods by Luenberger]] pp 177 - 178
- Giaquinta, M. and Hildebrandt, S. (1996) *Calculus of Variations 1. The Lagrangian Formalism*, Grundlehren der Mathematischen Wissenschaften 310. Springer-Verlag, Berlin. pp 14