---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/stochastic_process
keywords:
  - stochastic_matrix
  - doubly_stochastic_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - stochastic_process
name: Stochastic Matrix and Doubly Stochastic Matrix
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Stochastic Matrix and Doubly Stochastic Matrix

>[!important] Definition
>A **(row) stochastic matrix** is a nonnegative matrix $A\in M_{n}$ with property that $$Ae = e,$$ where $e:=1 = [1\,{,}\ldots{,}\,1]\in F^{n}$.
>
>That is, all of its *row sums are $1$* $$\sum_{j=1}^{n}a_{i,j} = 1,\quad i=1\,{,}\ldots{,}\,n,$$ is said to be 

^a60df1

- [[Nonnegative and Positive Matrix]]

>[!important] Definition
>A **column stochastic matrix** is a nonnegative matrix $A\in M_{n}$ with property that $$e^{T}A = e^{T},$$ where $e:=1 = [1\,{,}\ldots{,}\,1]\in F^{n}$. That is, all of its *column sums* are $1$.

>[!important] Definition
>A nonnegative matrix $A\in M_{n}$ is **doubly stochastic** if $A$ and $A^{T}$ are both *stochastic.*

^e60317

>[!important] Definition
>A nonnegative matrix $A\in M_{n}$ is **doubly substochastic** if 
>- $$Ae \preceq e$$
>- $$e^{T}A \preceq e^{T}$$
>
>that is, all *row and column sums* are *at most one*. 


## Explanation

>[!important]
>By definition, all stochastic matrix has an **eigenvalue** $1$, and the corresponding **eigenvector** is all 1 vector $e$.
>
>Moreover, it can be shown that the **spectral radius** $$\rho(A) := \left\{ |\lambda|: \lambda\in \sigma(A) \right\}  = 1.$$

- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Radius of Linear Operator]]
- [[Spectrum of Adjoint of Linear Operator]]


>[!info]
>**Stochastic matrices** arise in the study of **Markov chains** and in a variety of modeling problems in economics and operations research.

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]

### Eigenvector and Invariant Measures of Markov Chain

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Invariant Measure and Stationary Distribution]]

## Space of Stochastic Matrices

![[Space of Stochastic Matrices#^824e76]]

- [[Space of Stochastic Matrices]]


-----------
##  Recommended Notes and References


- [[Invariant Measure and Stationary Distribution]]
- [[Hidden Markov Model]]
- [[Markov Chain and Markov Process]]
- [[Nonnegative Matrix Factorization or NMF]]
- [[Markov Transition Kernel and Transition Function]]
- [[Matrix]]
- [[Positive Linear Functional]]


- [[Matrix Analysis by Horn]] pp 547 - 552
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]]