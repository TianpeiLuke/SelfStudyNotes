---
tags:
  - concept
  - math/matrix_analysis
  - statistics/estimation
  - math/linear_algebra
keywords:
  - singular_value_decomposition
  - least_square_estimation
topics:
  - statistics/estimation
  - matrix_analysis
name: Least Square Estimation via Singular Value Decomposition
date of note: 2024-08-21
---

## Concept Definition

>[!important]
>**Name**: Least Square Estimation via Singular Value Decomposition


![[Linear Regression#^24812d]]

![[Least Square Estimation#^9775a7]]

 ![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]
![[Least Square Estimation Solution and Geometric Interpretation#^76f8a3]]

- [[Least Square Estimation Solution and Geometric Interpretation]]

>[!important] Definition
>Consider the **singular value decomposition** of design matrix $X \in \mathbb{R}^{m\times d}$ as
>$$
>  X = U\,\Sigma\,V^{T} = \sum_{i=1}^{d}\sigma_{i}\,u_{i}\,v_{i}^{T}.
>$$
>
>Then 
>$$
>\begin{align*}
> \lVert X\beta - y \rVert_{2}^2 &= \lVert \left( U^{T}\,X\,V \right)(V^{T}\beta) - U^{T}\,y  \rVert_{2}^2  \\[5pt]
> &= \sum_{i=1}^{d}\,\left( \sigma_{i}\,z_{i} - \left( u_{i}^{T}\,y \right) \right)^2 + \sum_{i=d+1}^{m}\,\left( u_{i}^{T}\,y \right)^2
>\end{align*}
>$$
>where $z = V^{T}\beta.$
>
>It follows that the summation is *minimized* when $$z_{i} = \frac{\left\langle u_{i} , y \right\rangle }{\sigma_{i}}, \quad i=1\,{,}\ldots{,}\,d$$ 
>Thus the **least square estimate** $\hat{\beta}$ of $\beta$ can be represented as the *linear combination* of *right-singular vectors*
>$$
>\hat{\beta} = \sum_{i=1}^{d}\,\frac{\left\langle u_{i} , y \right\rangle }{\sigma_{i}}\,v_{i}
>$$
>and the **mean square error**
>$$
>\rho_{LS}^2 := \lVert X\beta - y \rVert_{2}^2 = \sum_{i=d+1}^{m}\left( u_{i}^{T}\,y \right)^2
>$$

^9f2cf8

- [[Singular Value Decomposition of Linear Map]]
- [[Linear Span over a Set of Vectors]]
- [[Linear Combination]]


## Explanation

![[Singular Value Decomposition and Pseudoinverse#^ad36dd]]


- [[Singular Value Decomposition and Pseudoinverse]]


-----------
##  Recommended Notes and References


- [[Singular Value Decomposition of Linear Map]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]


- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation]]
- [[Least Square Estimation with QR Factorization]]
- [[Linear Regression]]



- [[Elements of Statistical Learning by Hastie]]
- [[Numerical Optimization by Nocedal]]
- [[Matrix Computations by Golub]] pp 260 - 288
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 70 - 71
- [[Convex Optimization by Boyd]] pp 4, 131, 153, 177, 293, 304, 458