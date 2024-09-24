---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - matrix_partition
  - conformal_matrix_partition
topics:
  - matrix_analysis
  - linear_algebra
name: Conformal Matrix Partitions
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Conformal Matrix Partitions

![[Partition of Matrix and Block Matrix#^91291d]]

>[!important] Definition
>Let $A\in M_{m,n}(F)$, $B\in M_{n,p}(F)$, and  
>- let $\alpha_{1}\,{,}\ldots{,}\,\alpha_{t}$ be a *partition* of row index $\{ 1\,{,}\ldots{,}\, m\}$,  and $\beta_{1} \,{,}\ldots{,}\,\beta_{s}$ be a *partition* of column index $\{ 1\,{,}\ldots{,}\, n\}$ of matrix $A$
>- and let $\delta_{1} \,{,}\ldots{,}\,\delta_{d}$ be a *partition* of row index $\{ 1\,{,}\ldots{,}\, n\}$, and $\gamma_{1} \,{,}\ldots{,}\,\gamma_{r}$ be a *partition* of column $\{ 1\,{,}\ldots{,}\, p\}$ of matrix $B$.
>  
>Then the two *partitions* of $A$ and $B$ are said to be **conformal partition** if they agree on the set $\{ 1\,{,}\ldots{,}\,n \}$, i.e. $$\{ \beta_{1} \,{,}\ldots{,}\,\beta_{s} \} = \{ \delta_{1} \,{,}\ldots{,}\,\delta_{d} \}$$

## Explanation

>[!important]
>Let $A\in M_{m,n}(F)$, $B\in M_{n,p}(F)$, with **conformal partitions**, then the **product** can be decomposed as the sum of partitioned products $$(AB)[\alpha_{i}, \gamma_{j}] = \sum_{k=1}^{s}A[\alpha_{i}, \beta_{k}]\;B[\beta_{k}, \gamma_{j}]$$ 
>
>Thus, multiplication of **conformally partitioned matrices** mimics usual *matrix multiplication*.





-----------
##  Recommended Notes and References


- [[Partition of Matrix and Block Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Laplace Expansion Theorem]]


- [[Positive Semidefinite Transformation]]
- [[Determinant of Linear Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 17
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 
- [[Matrix Computations by Golub]] pp 
- [[Finite Dimensional Vector Spaces by Halmos]] pp 