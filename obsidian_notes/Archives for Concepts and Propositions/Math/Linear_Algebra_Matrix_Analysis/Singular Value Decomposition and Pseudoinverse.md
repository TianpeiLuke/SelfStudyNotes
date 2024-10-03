---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - singular_value_decomposition
  - moore_penrose_inverse
topics:
  - matrix_analysis
name: Singular Vector Decomposition and Pseudoinverse
date of note: 2024-09-20
---

## Concept Definition

>[!important]
>**Name**: Singular Vector Decomposition and Pseudoinverse

![[Moore–Penrose Pseudo Inverse of Matrix#^56d67e]]


>[!important] Proposition
>Let $A \in M_{m,n}$, and $q= \min\left\{ m, n \right\}$, and suppose that $\text{rank}(A) = r.$ The **singular value decomposition** of $A$ is given by $$A = U \,\Sigma\,V^{*},$$ where  $U \in U(m)$ and $V\in U(n)$ are **unitary matrices**, and a **square diagonal matrix** $$\Sigma_{q} = \text{diag}(\sigma_{1} \,{,}\ldots{,}\,\sigma_{q})$$ such that $\sigma_{1} \ge \sigma_{2} \ge \ldots \sigma_{r} >0 = \sigma_{r+1} =  \ldots = \sigma_{q}$ and  in which 
>  $$
>  \begin{align*}
>  \Sigma = \left\{ \begin{array}{cc} \Sigma_{q} & m = n\\[5pt] \left[ \Sigma_{q}, \; 0 \right] \in M_{m,n} & n > m \\[5pt] \left[ \begin{array}{c}\Sigma_{q} \\ 0\end{array} \right] \in M_{m,n} & m > n\end{array}\right.
>  \end{align*}
> $$
> 
>Then the **Moore-Penrose Pseudoinvse** $A^{+}$ has the **singular value decomposition** 
>$$
>A^{+} = V\,\Sigma^{+}\,U^{*} \in M_{n,m}
>$$ 
>where
>$$
>  \begin{align*}
>  \Sigma^{+} = \left\{ \begin{array}{cc} \Sigma_{q}^{-1} & m = n\\[5pt] \left[ \Sigma_{q}^{-1}, \; 0 \right] \in M_{m,n} & n > m \\[5pt] \left[ \begin{array}{c}\Sigma_{q}^{-1} \\ 0\end{array} \right] \in M_{m,n} & m > n\end{array}\right.
>  \end{align*}
>$$

^652a04

- [[Singular Value Decomposition of Linear Map]]

## Explanation

>[!important] 
>The matrix $A\in M_{m,n}$ has the following **singular value decomposition (SVD)**
>$$
>A = \sum_{i=1}^{r}\sigma_{i}\,u_{i}\,v_{i}^{*}
>$$ 
>Then the **pseudo-inverse** of $A$, $A^{+}$ has  the following **singular value decomposition (SVD)** $$
>A^{+} =  \sum_{i=1}^{r} \frac{1}{\sigma_{i}}\,v_{i}\,u_{i}^{*}
>$$

^ad36dd

- [[Ridge Regression and L2 Regularization]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Least Square Estimation via Singular Value Decomposition]]




-----------
##  Recommended Notes and References


- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Singular Value Decomposition of Linear Map]]




- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] 
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 38
- [[Matrix CookBook by Petersen]] pp 31