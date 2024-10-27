---
tags:
  - concept
  - math/lie_group_algebra
  - math/linear_algebra
  - math/matrix_analysis
  - math/ordinary_differential_equation
keywords:
  - local_flow_general_linear_group
  - matrix_exponential
topics:
  - lie_group_lie_algebra
  - differential_geometry
  - differential_equation
  - matrix_analysis
  - linear_algebra
name: Matrix Exponential and Flow in General Linear Group
date of note: 2024-10-27
---

## Concept Definition

>[!important]
>**Name**: Matrix Exponential and Flow in General Linear Group

![[Global Flow on Smooth Manifold#^532ef7]]

>[!important] Definition
>A function $$A: \mathbb{R} \to \text{GL}(n; \mathbb{C})$$ is called a **one-parameter subgroup** of $\text{GL}(n; \mathbb{C})$ or a **global flow** on $\text{GL}(n; \mathbb{C})$ if
>- $A$ is *continuous*
>- $$A(0) = I$$
>- for all $s,t\in \mathbb{R}$, $$A(t+s) = A(t)A(s)$$

^926b51

- [[General Linear Group]]
- [[Subgroup]]

>[!important] Theorem (Representation of One-Parameter Subgroup)
>Let $A: \mathbb{R} \to \text{GL}(n; \mathbb{C})$ be a **one-parameter subgroup** of $\text{GL}(n; \mathbb{C})$, 
>
>Then there **exists** a **unique** matrix $X \in M_{n}(\mathbb{C})$ such that $$A(t) = e^{tX}.$$

^b0ad7e

- [[Matrix Exponential]]


## Explanation

>[!important]
>We can define  a map $$\theta: \mathbb{R} \times \text{GL}(n;\mathbb{C}) \to \text{GL}(n;\mathbb{C})$$ from  **one-parameter subgroup** $A$ by $$\theta(t, X)= A(t)\,X$$
>
>We show that $\theta$ is a **global flow** in $\text{GL}(n; \mathbb{C})$ since the following conditions are satisfied:
>- $\theta$ is a *continuous map*
>- $$\theta(0, X) = A(0)X = X$$
>- for any $X\in \text{GL}(n; \mathbb{C})$, any $s,t\in \mathbb{R}$ $$\begin{align*} \theta(t, \theta(s, X)) & = A(t)\theta(s, X) \\[5pt] &= A(t)A(s)X \\[5pt] &= A(t+s)X \\[5pt] &= \theta(t+s, X)\end{align*}$$

- [[Topological Group Action]]
- [[Local Flow on Smooth Manifold]]
- [[Global Flow on Smooth Manifold]]




-----------
##  Recommended Notes and References



- [[Matrix Lie Group]]
- [[Lie Group]]
- [[Group]]
- [[Matrix]]

- [[Topological Group]]
- [[Topology of Set]]

- [[Lie Groups Lie Algebra and Representations by Hall]] pp 41