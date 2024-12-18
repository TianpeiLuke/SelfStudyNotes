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
name: Variational Derivative of Functional
date of note: 2024-10-29
---

## Concept Definition

>[!important]
>**Name**: Variational Derivative of Functional

>[!important] Definition
>Let $y\in \mathcal{C}^{1}(\mathbb{R}^{d})$ be a *continuous differentiable function*. Denote $y := y(x)$ for some $x\in \mathbb{R}^{d}$.  
>
>Consider $$J: \mathcal{C}^{1}(\mathbb{R}^{d}) \to \mathbb{R}$$ as a *functional* on the space of differentiable functions.
>
>The **variational derivative** or **functional derivative** of *functional* $J[y]$ at $x=x_{0}$ is defined as 
>$$
>\frac{\delta J}{\delta y} \Big|_{x = x_{0}} = \lim_{ \Delta \sigma \to 0 } \frac{J[y+h] - J[y] }{\Delta \sigma}
>$$
>where 
>- $h := h(x)$ is an *increment* or *delta function* so that there exists some small $\epsilon >0$ such that  $$h(x) = 0, \; \forall x\not\in B(x_{0}, \epsilon)\, $$
>- $\Delta\sigma$ is the *area* between $y = h(x)$ and x-axis $y=0$, i.e. $$\Delta \sigma := \int_{\mathbb{R}^d} |h(x)| dx = \int_{B(x_{0}, \epsilon)} |h(x)| dx$$
>  
>As a result $$\Delta J := J[y + h] - J[y] = \left(\frac{\delta J}{\delta y} \Big|_{x = x_{0}} + \epsilon \right)\,\Delta\,\sigma $$ Thus as $\epsilon \to 0$, we have the **variation or differential of functional** at a point $x_{0}$ as $$\delta J = \frac{\delta J}{\delta y} \Big|_{x = x_{0}}\,\Delta\,\sigma$$

- [[First Variation of Functional]]
- [[Characteristic Function of Set]]
- [[Metric Topology and epsilon-ball]]
- [[Space of all Continuous Functions]]
- [[Hypograph or Subgraph of Function]]

### Variational Derivative via First Variation and Gateaux Differential

>[!important] Definition
>Let $X \subset \mathcal{C}^{1}(\Omega)$ be the space of *smooth functions* on $\Omega$. A *functional* $$J: X \to \mathbb{R}$$ is given by the *Lagrangian formalism* $$J[y] = \int_{\Omega}\,F(x, y, y')\,dx$$ where  $y := y(x) \in X$ and $y' = dy / dx.$
>  
>The **variational derivative** of $J$ at $y_{0}\in X$ is defined as a smooth function $$\frac{\delta J}{\delta y}\Big|_{y_{0}} \in X$$ that satisfies 
>$$
>\delta J(y_{0}, h) := \int_{\Omega}\,\frac{\delta J}{\delta y}\Big|_{y_{0}}\,h\,dx
>$$
>where 
>- $h\in \mathcal{C}_{c}^{\infty}(\Omega)$ is an arbitrary *smooth test function* with *compact support*.
>- and $\delta J(y_{0}, h)$ is the **first variation** of $J$ at $y_{0}$ i.e. the **Cateaux derivative** of $J$ $$\delta J(y_{0}, h) := \lim_{ t \to 0 } \frac{|J[y_{0} + t\,h] - J[y_{0}]|}{t}  $$

^82443b

- [[Gateaux Derivative and Weak Derivative in Banach Space]]
- [[First Variation of Functional]]
- [[Continuous Functions with Compact Support]]
- [[Lagrangian Function in Mechanics and Variational Calculus]]


### Variational Derivative via Euler-Lagrange Equation

![[Euler–Lagrange Equations#^f331ce]]

![[Euler–Lagrange Equations#^7c3405]]

![[Euler–Lagrange Equations#^76fc96]]

- [[Euler–Lagrange Equations]]

>[!important]
>For functional defined as $$J[y] = \int_{a}^{b}F(x, y, y')dx,$$ the corresponding **variation** of $J$ at $x_{0}$ is given by 
>$$
>\begin{align*}
>\delta J(y, h) = J[y+ h] - J[y] = \int_{a}^{b} \frac{\delta J}{\delta y} h\,dx, \quad \delta y := h \in \mathcal{C}_{c}^{\infty}(\mathbb{R}^{d}, \mathbb{R})
>\end{align*}
>$$
>
>We can show that the **variational derivative** of $J$ is given by the LHS of **Euler-Lagrange equation**.
>$$
>\frac{\delta J}{\delta y} = \frac{ \partial F}{ \partial y} -\frac{d}{dx}  \frac{ \partial F }{ \partial y' } 
>$$

### Variational Derivative for Multivariate Function Input

![[Euler–Lagrange Equations#^fbb619]]

>[!important]
>Let $x := (x^1\,{,}\ldots{,}\,x^{n})$, and $y: \mathbb{R}^{n} \to \mathbb{R}$.
>
>For functional defined as $$J[y] = \int_{a}^{b}F(x, y, \nabla y)dx,$$ the corresponding **variation** of $J$ at $x_{0}$ is given by 
>$$
>\begin{align*}
>\delta J(y, h) = J[y+ h] - J[y] = \int_{a}^{b} \frac{\delta J}{\delta y} h\,dx, \quad \delta y := h \in \mathcal{C}_{c}^{\infty}(\mathbb{R}^{d}, \mathbb{R})
>\end{align*}
>$$
>
>We can show that the **variational derivative** of $J$ is given by the LHS of **Euler-Lagrange equation**.
>$$
>\frac{\delta J}{\delta y} = \frac{\partial  F}{ \partial y}- \sum_{i=1}^{n}\left(\frac{\partial }{ \partial x^{i}}\frac{\partial  F}{ \partial (\partial_{i} y) }\,\right)
>$$
>or
>$$
>\frac{\delta J}{\delta y} = \frac{ \partial F}{ \partial y} - \text{div}\left( \frac{ \partial F }{ \partial  \nabla y }  \right)
>$$

^60b0b8

- [[Jacobian Matrix and Jacobian Determinant]]
- [[Euler–Lagrange Equations]]


## Explanation

>[!info]
>The following notations of *functional derivative* are the same
>$$
>\frac{\delta J}{\delta y} \Big|_{x = x_{0}} \equiv \frac{\delta J}{\delta y(x_{0})} 
>$$

>[!info]
>If the **Fréchet derivative** of $J$ at $y$ exists, i.e. $DJ(y)$, then $$DJ(y)(h) = \int_{\Omega}\;\frac{\delta J}{\delta y} h\,dx$$ or $$DJ(y) = \int_{\Omega}\;\frac{\delta J}{\delta y} \cdot\,dx$$

- [[Fréchet Derivative and Strong Derivative in Banach Space]]





-----------
##  Recommended Notes and References


- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Entropy Functional]]

- [[Bounded Linear Functional]]

- [[Optimization by Vector Space Methods by Luenberger]]
- [[Calculus of Variations by Gelfand]] pp 27 - 29, 
- Giaquinta, M., & Hildebrandt, S. (1995). _Calculus of Variations I_ (Corrected edition). Springer.
- Wikipedia [Functional_derivative](https://en.wikipedia.org/wiki/Functional_derivative#Definition)