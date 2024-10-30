---
tags:
  - concept
  - math/calculus_of_variations
  - math/functional_analysis
keywords:
  - first_variation_functional
  - variational_derivative_functional
topics:
  - variational_calculus
  - functional_analysis
name: First Variation and Variational Derivative of Functional
date of note: 2024-10-29
---

## Concept Definition

>[!important]
>**Name**: First Variation and Variational Derivative of Functional

>[!important] Definition
>Let $y\in \mathcal{C}^{1}(\mathbb{R}^{d})$ be a *continuous differentiable function*. Denote $y := y(x)$ for some $x\in \mathbb{R}^{d}$.  
>
>Consider $$J: \mathcal{C}^{1}(\mathbb{R}^{d}) \to \mathbb{R}$$ as a *functional* on the space of differentiable functions.
>
>The **variational derivative** or **functional derivative**, or **first variation** of *functional* $J[y]$ at $x=x_{0}$ is defined as 
>$$
>\frac{\delta J}{\delta y} \Big|_{x = x_{0}} = \lim_{ \Delta \sigma \to 0 } \frac{J[y+h] - J[y] }{\Delta \sigma}
>$$
>where 
>- $h := h(x)$ is an *increment* or *delta function* so that there exists some small $\epsilon >0$ such that  $$h(x) = 0, \; \forall x\not\in B(x_{0}, \epsilon)\, $$
>- $\Delta\sigma$ is the *area* between $y = h(x)$ and x-axis $y=0$, i.e. $$\Delta \sigma := \int_{\mathbb{R}^d} |h(x)| dx = \int_{B(x_{0}, \epsilon)} |h(x)| dx$$
>  
>As a result $$\Delta J := J[y + h] - J[y] = \left(\frac{\delta J}{\delta y} \Big|_{x = x_{0}} + \epsilon \right)\,\Delta\,\sigma $$ Thus as $\epsilon \to 0$, we have the **variation or differential of functional** at a point $x_{0}$ as $$\delta J = \frac{\delta J}{\delta y} \Big|_{x = x_{0}}\,\Delta\,\sigma$$

- [[Variation of Functional]]
- [[Characteristic Function of Set]]
- [[Metric Topology and epsilon-ball]]
- [[Space of all Continuous Functions]]
- [[Hypograph or Subgraph of Function]]

### Variational Derivative via Euler-Lagrange Equation

![[Euler–Lagrange Equations#^f331ce]]

![[Euler–Lagrange Equations#^7c3405]]

![[Euler–Lagrange Equations#^76fc96]]

- [[Euler–Lagrange Equations]]

>[!important]
>For functional defined as $$J[y] = \int_{a}^{b}F(x, y, y')dx,$$ the corresponding **variation** of $J$ at $x_{0}$ is given by 
>$$
>\begin{align*}
>\delta J(y, \varphi) = J[y+ h] - J[y] = \int_{a}^{b} \frac{\delta J}{\delta y} \delta y\,dx, \quad \delta y := \varphi \in \mathcal{C}_{c}^{\infty}(\mathbb{R}^{d}, \mathbb{R})
>\end{align*}
>$$
>
>We can show that the **variational derivative** of $J$ is given by the LHS of **Euler-Lagrange equation**.
>$$
>\frac{\delta J}{\delta y} = \frac{ \partial F}{ \partial y} -\frac{d}{dx}  \frac{ \partial F }{ \partial y' } 
>$$



## Explanation

>[!info]
>The following notations of *functional derivative* are the same
>$$
>\frac{\delta J}{\delta y} \Big|_{x = x_{0}} \equiv \frac{\delta J}{\delta y(x_{0})} 
>$$




-----------
##  Recommended Notes and References


- [[Lagrangian Function in Mechanics]]
- [[Entropy Functional]]

- [[Bounded Linear Functional]]


- [[Calculus of Variations by Gelfand]] pp 27 - 29, 