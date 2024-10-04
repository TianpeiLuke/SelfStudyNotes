---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - band_forward_substitution
  - band_back_substitution
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Band Forward Substitution and Band Back Substitution
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Band Forward Substitution and Band Back Substitution

![[Banded System of Equations#^a1a9cb]]


### Band Forward Substitution

![[Forward Substitution of Lower Triangular System#^7ef70f]]


>[!important] Definition
>Consider the problem of solving a **banded triangular system of equations** $$Lx = b$$ where $L$ is a *banded lower triangular matrix* with  *lower bandwidth* $p$.
>
>The **(column-oriented) band forward substitution** algorithm that solves above problem is described as follows
>- *Require*: $L$ with **lower bandwidth** $p$, and $b$.
>- For $j=1\,{,}\ldots{,}\,n$:
>	- $$x_{j} = \frac{b_{j}}{L_{j,j}}$$
>	- For $k=j+1 \,{,}\ldots{,}\, \min\left\{ j+p, n \right\}$:
>		- $$b_{k} \leftarrow b_{k} - L_{k,j}\,x_{j}$$
>	- Finally $$x_{n} = \frac{b_{n}}{L_{n,n}}$$

^c7f30d

- [[Forward Substitution of Lower Triangular System]]

>[!important] 
>If $n \gg p$, then this algorithm requires about $$2np$$ flops.

### Band Back Substitution

![[Back Substitution of Upper Triangular System#^20d9f8]]


>[!important] Definition
>Consider the problem of solving a **banded triangular system of equations** $$Ux = b$$ where $L$ is a *banded upper triangular matrix* with  *upper bandwidth* $q$.
>
>The **(column-oriented) band back substitution** algorithm that solves above problem is described as follows
>- *Require*: $U$ with **upper bandwidth** $q$, and  $b$.
>- For $j=n\,{,}\ldots{,}\,1$:
>	- $$x_{j} = \frac{b_{j}}{L_{j,j}}$$
>	- For $k=\max\left\{ 1, j-q \right\} \,{,}\ldots{,}\, j-1$:
>		- $$b_{k} \leftarrow b_{k} - U_{k,j}\,x_{j}$$
>	- Finally $$x_{1} = \frac{b_{1}}{L_{1,1}}$$

- [[Back Substitution of Upper Triangular System]]

>[!important] 
>If $n \gg q$, then this algorithm requires about $$2nq$$ flops.




## Explanation





-----------
##  Recommended Notes and References


- [[Banded System of Equations]]
- [[Band Triangular System of Equations]]
- [[Band Gaussian Elimination and Band LU Factorization]]



- [[Triangular System of Equations]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Matrix]]
- [[Gaussian Elimination for General Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp
- [[Matrix Computations by Golub]] pp 177 - 179
- [[Matrix Analysis by Horn]]