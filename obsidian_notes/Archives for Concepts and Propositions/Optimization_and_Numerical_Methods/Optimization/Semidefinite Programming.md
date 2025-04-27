---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - optimization/algorithm
  - optimization/convex_optimization
  - SDP
  - semidefinite_programming
keywords:
  - semidefinite_programming
  - sdp_optimization
topics:
  - optimization/theory
  - optimization/algorithm
name: Semidefinite Programming
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Semidefinite Programming

![[Quadratic Programming#^9ccf19]]

- [[Quadratic Programming]]

>[!important] Definition
>The **semidefinite programming (SDP)** solves the following *convex optimization problem*
>$$
>\begin{align*}
> \min_{x\in \mathbb{R}^{n}}\;&\; \left\langle  c\,,\,x    \right\rangle \\[5pt]
> \text{s.t. }&\; x_{1}F_{1} \,{+}\ldots{+}\,x_{n}F_{n} + G \preceq 0 \\[5pt]
> &\;Ax = b
>\end{align*}
>$$  
>where $x\in \mathbb{R}^{n}$ is the optimization variable and
>- $G, F_{1}\,{,}\ldots{,}\,F_{n} \in \mathcal{S}_{+}^{n}$ are *symmetric positive semidefinite matrix* in $\mathbb{R}^{n\times n}$ and
>- $A\in \mathbb{R}^{p\times n}$, $b\in \mathbb{R}^{p}$
>- $c\in \mathbb{R}^{n}$
>  
>The first constraint $$x_{1}F_{1} \,{+}\ldots{+}\,x_{n}F_{n} + G \preceq 0$$ is called a **linear matrix inequality**.
>- If $G, F_{i}$ are all *diagonal*, then the *linear matrix inequality constraints* becomes *linear inequality constraints*. Then the *SDP* becomes *linear programming*.

- [[Trace of Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Convex Optimization Problem]]
- [[Linear Optimization Problem]]

>[!info]
>The inequality
> $$
> \begin{align*}
 A \succeq B& \;\iff \; (A-B) \in \mathcal{S}_{+}^{n} \text{ is positive semidefinite}& \\[5pt]
 &\; \iff \quad \lambda_{i}(A - B) \ge 0 \quad  \forall i=1\,{,}\ldots{,}\,n
>\end{align*}
>$$ 

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


>[!important] Definition
>The **standard form** of **semidefinite programming (SDP)** solves the following *convex optimization problem*
>$$
>\begin{align*}
> \min_{X\in \mathcal{S}_{+}^{n}}\;&\; \text{tr}(CX) := \left\langle  C\,,\,X    \right\rangle_{tr} \\[5pt]
> \text{s.t. }&\; \text{tr}(A_{i}X) := \left\langle  A_{i}\,,\,X    \right\rangle_{tr} = b_{i}, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\;X \succeq 0
>\end{align*}
>$$  
>where $X \in \mathcal{S}_{+}^{n}$ is the optimization variable that is *symmetric positive semidefinite* and
>- $C, A_{i} \in \mathcal{S}_{+}^{n}$ are *symmetric positive semidefinite matrix* in $\mathbb{R}^{n\times n}$
>  
>Note that besides the **semidefinite constraint** $$X \succeq 0,$$ both the *loss function* and *equality constraints* are **affine**.  

>[!important] Definition
>An **inequality form** of **semidefinite programming (SDP)** solves the following *convex optimization problem*
>$$
>\begin{align*}
> \min_{x\in \mathbb{R}^{n}}\;&\; \left\langle  c\,,\,x    \right\rangle \\[5pt]
> \text{s.t. }&\; x_{1}A_{1} \,{+}\ldots{+}\,x_{n}A_{n} \preceq B\\[5pt]
> &\;X \succeq 0
>\end{align*}
>$$  
>where $x \in \mathbb{R}^{n}$ is the optimization variable and
>- $B, A_{i} \in \mathcal{S}_{+}^{n}$ are *symmetric positive semidefinite matrix* in $\mathbb{R}^{n\times n}$
>- $c\in \mathbb{R}^{n}$

- [[Space of Symmetric Positive Semidefinite Matrices]]

## Explanation





-----------
##  Recommended Notes and References



- [[Second-Order Cone Programming]]

- [[Inverse Covariance Estimation]]

- [[Convex Function]]
- [[Determinant of Linear Transformation]]
- [[Trace of Positive Semi-Definite Operator]]



- [[Primal-Dual Interior Point Method for Convex Optimization]]



- [[Convex Optimization by Boyd]] pp 168, 201, 265, 285, 600 - 608, 618 
- [[Convex Optimization Algorithms by Bertsekas]] pp 22 - 25
- [[Nonlinear Programming by Bertsekas]]