---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - jordan_decomposition
  - jordan_canonical_form
topics:
  - matrix_analysis
  - linear_algebra
name: Jordan Canonical Form
date of note: 2024-09-15
---

## Concept Definition

>[!important]
>**Name**: Jordan Canonical Form

>[!important] Definition
>The **Jordan block matrix** is of the form
>$$J_{i} = \left[
>\begin{array}{cccccc}
> \lambda_{i} & 1 & 0 & \cdots & \cdots & 0 \\
> 0 & \lambda_{i}  & 1 & 0 &  & \vdots \\
> \vdots & \ddots & \lambda_{i} & \ddots & \ddots & \vdots \\
> \vdots &  & \ddots & \ddots & 1 & 0 \\
> \vdots &  & & \ddots & \lambda_{i}  & 1 \\
> \vdots & \cdots &   \cdots  &  \cdots  & 0 & \lambda_{i}
>\end{array}
>\right] \in \mathbb{C}^{k_{i}\times k_{i}}
>$$

>[!important] Theorem (Jordan Canonical Form)
>For all $A\in \mathbb{C}^{n\times n}$ with *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\in \mathbb{C}$ (*not necessarily distinct*), there exists $X\in \mathbb{C}^{n\times n}$ such that 
>$$
>X^{-1}\,A\,X = J = \text{diag}\left(J_{1} \,{,}\ldots{,}\,J_{q}\right),
>$$
>where each of the **Jordan block matrices** $J_{1} \,{,}\ldots{,}\,J_{q}$ is of the form
>$$J_{i} = \left[
>\begin{array}{cccccc}
> \lambda_{i} & 1 & 0 & \cdots & \cdots & 0 \\
> 0 & \lambda_{i}  & 1 & 0 &  & \vdots \\
> \vdots & \ddots & \lambda_{i} & \ddots & \ddots & \vdots \\
> \vdots &  & \ddots & \ddots & 1 & 0 \\
> \vdots &  & & \ddots & \lambda_{i}  & 1 \\
> \vdots & \cdots &   \cdots  &  \cdots  & 0 & \lambda_{i}
>\end{array}
>\right] \in \mathbb{C}^{k_{i}\times k_{i}},
>$$
>and $$\sum_{i=1}^{q}k_{i} = n.$$

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Multiplicity of Linear Map]]

>[!important] Definition
>For $A\in \mathbb{C}^{n\times n}$, the **Jordan canonical form (JCF)** is of the form
>$$
> A = X\,\text{diag}\left(J_{1} \,{,}\ldots{,}\,J_{q}\right)\,X^{-1}
>$$
>where $X$ is **invertible** and $J_{i}$ is the **Jordan block matrix** associated with eigenvalue $\lambda_{i}$.


## Explanation


## Characteristic Polynomial and Multiplicity 

- [[Multiplicity of Linear Map]]
- [[Characteristic Polynomial for Linear Map]]



-----------
##  Recommended Notes and References


- [[Nilpotent Linear Transformation and Matrix]]
- [[Krylov Subspace]]
- [[Characteristic Polynomial for Linear Map]]


- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 82 - 85
- [[Matrix Computations by Golub]]