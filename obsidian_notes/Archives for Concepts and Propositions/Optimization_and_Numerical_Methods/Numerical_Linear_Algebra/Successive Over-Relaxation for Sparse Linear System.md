---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - successive_over_relaxation
  - symmetric_successive_over_relaxation
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Successive Over-Relaxation for Sparse Linear System
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Successive Over-Relaxation for Sparse Linear System

![[Gauss-Seidel Iteration for Sparse Linear System#^084714]]

![[Gauss-Seidel Iteration for Sparse Linear System#^86aad2]]

>[!important] Definition
>Consider the *linear system* $Ax = b$ where $A = [a_{i,j}] \in M_{m,n}(\mathbb{C})$,  $b = [b_{i}]\in \mathbb{C}^{m}$. That is,
>$$
>\begin{align*}
> a_{1,1}x_{1} \,{+}\ldots{+}\,a_{1,n}x_{n} &= b_{1}\\[5pt]
> a_{2,1}x_{1} \,{+}\ldots{+}\,a_{2,n}x_{n} &= b_{2}\\[5pt]
> \ldots& \\[5pt]
> a_{m,1}x_{1} \,{+}\ldots{+}\,a_{m,n}x_{n} &= b_{m}
>\end{align*}
>$$
>Suppose $x^{(k-1)}$ is an *approximation* to $x = A^{-1}b$. 
>
>The **successive over-relaxation (SOR)** generates a *new approximation* $x^{(k)}$ by computing a **forward pass**
>- For $i=1\,{,}\ldots{,}\,n$:
>$$
>\begin{align*}
> x_{i}^{(k)}  &= w \left(\dfrac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,x_{j}^{(k)} -  \sum_{j=i+1}^{n}a_{i,j}\,x_{j}^{(k-1)}}{a_{i,i}}\right) + (1- w)\,x_{i}^{(k-1)}
>\end{align*}
>$$
>- If $w=1$, then this is just the **Gauss-Seidel** method.

- [[Gauss-Seidel Iteration for Sparse Linear System]]

>[!important] Definition
>The **backward successive over-relaxation (SOR)** iteration generates a *new approximation* $$x^{(k)} \to A^{-1}b$$ by computing a **forward pass**
>- For $i=n\,{,}\ldots{,}\,1$:
>$$
>\begin{align*}
> x_{i}^{(k)}  &= w \left(\dfrac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,x_{j}^{(k-1)} -  \sum_{j=i+1}^{n}a_{i,j}\,x_{j}^{(k)}}{a_{i,i}}\right) + (1- w)\,x_{i}^{(k-1)}
>\end{align*}
>$$


>[!important] Definition
>Consider the task of solving a *linear system* $$Ax = b.$$ 
>
>The **(forward) successive over-relaxation (SOR)** iteration can be formulated in compact form: $$\left(\frac{1}{w}D_{A} + L_{A}\right)x^{(k)} = \left(\left(\frac{1}{w} - 1\right)D_{A} + U_{A}\right)x^{(k-1)} + b$$
>And the **backward successive over-relaxation (SOR)** iteration is formulated as $$\left(\frac{1}{w}D_{A} + U_{A}\right)x^{(k)} = \left(\left(\frac{1}{w} - 1\right)D_{A} + L_{A}\right)x^{(k-1)} + b$$
>where 
>-  $D_{A}$, $L_{A}$ and $U_{A}$ are *diagonal entries*, *lower triangular entries*, and *upper triangular entries* of $A$, respectively
>$$
>\begin{align*}
> D_{A} &= \text{diag}(A) = \text{diag}(a_{1,1} \,{,}\ldots{,}\,a_{n,n})\\[5pt] 
> L_{A} &= \left[ \begin{array}{cccc}0&  &  & 0 \\ a_{2,1}& 0 &  & \vdots\\ \vdots & \ddots & \ddots & \vdots\\ a_{n,1}& \cdots & a_{n,n-1} & 0\end{array} \right]\\[5pt]  
> U_{A} &= \left[ \begin{array}{cccc}0& a_{1,2}  & \cdots  & a_{1,n} \\\vdots & 0 & \ddots & \vdots\\ \vdots &  & \ddots & a_{n-1,n}\\ 0 &  &  & 0\end{array} \right]
\end{align*}
>$$

### Symmetric SOR

>[!important] Definition
>Consider the task of solving a *linear system* $$Ax = b$$ where $A$ is **Hermitian**. 
>
>The **symmetric forward successive over-relaxation (SSOR)** iteration can be formulated in compact form: $$\left(\frac{1}{w}D_{A} + L_{A}\right)x^{(k)} = \left(\left(\frac{1}{w} - 1\right)D_{A} - L_{A}^{T}\right)x^{(k-1)} + b$$
>And the **symmetric backward successive over-relaxation (SSOR)** iteration is formulated as $$\left(\frac{1}{w}D_{A} + L_{A}^{T}\right)x^{(k)} = \left(\left(\frac{1}{w} - 1\right)D_{A} - L_{A}\right)x^{(k-1)} + b$$
>where 
>-  $D_{A}$, $L_{A}$ and $U_{A}$ are *diagonal entries*, *lower triangular entries*, and *upper triangular entries* of $A$, respectively
>$$
>\begin{align*}
> D_{A} &= \text{diag}(A) = \text{diag}(a_{1,1} \,{,}\ldots{,}\,a_{n,n})\\[5pt] 
> L_{A} &= \left[ \begin{array}{cccc}0&  &  & 0 \\ a_{2,1}& 0 &  & \vdots\\ \vdots & \ddots & \ddots & \vdots\\ a_{n,1}& \cdots & a_{n,n-1} & 0\end{array} \right]\\[5pt]  
> U_{A} &= \left[ \begin{array}{cccc}0& a_{1,2}  & \cdots  & a_{1,n} \\\vdots & 0 & \ddots & \vdots\\ \vdots &  & \ddots & a_{n-1,n}\\ 0 &  &  & 0\end{array} \right]
\end{align*}
>$$


## Explanation

>[!quote]
>The **Gauss-Seidel iteration** is very attractive because of its simplicity. Unfortunately, if the spectral radius of $M_{GS}^{-1} N_{GS}$ is close to unity, then it may be **prohibitively slow**.






-----------
##  Recommended Notes and References


- [[Gauss-Seidel Iteration for Sparse Linear System]]

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]



- [[Matrix Computations by Golub]] pp 619 - 620
- [[Numerical Linear Algebra by Trefethen]] pp 318, 339