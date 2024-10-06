---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - optimization/algorithm
  - optimization/convex_optimization
  - math/matrix_analysis
keywords:
  - least_square_estimation
  - pseudo_inverse_matrix
  - projection_linear_subspace
topics:
  - statistics/estimation
name: Algorithm for Least Square Estimation
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Algorithm for Least Square Estimation

![[Least Square Estimation#^9775a7]]

![[Least Square Estimation#^f8f306]]

- [[Least Square Estimation]]
- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]

![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]

^17b91f

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Non-Parametric Least Square Estimation]]
- [[Forward Stagewise Additive Modeling]]

###  Least Square Estimation via Linear System of Equations

![[Least Square Estimation Solution and Geometric Interpretation#^03c5db]]

>[!info]
>The key for solving the LSE is to solve the **normal equations**. 
>
>We can apply *algorithms* from *numerical linear algebra*

- [[Normal Equations and Newton System of Equations]]

>[!info]
>Solving $x$ is equivalent to finding the solution of **normal equation**
>$$
>X^{T}\,X\,\beta = X^{T}b \iff S\,\beta = w
>$$ 
>where $$S := X^{T}\,X \succ 0$$ is a **symmetric positive definite transformation** (since $A$ has full column rank) and $w := X^{T}b$
>- This is a **symmetric positive definite system**
>- We can use **$LDL^{T}$ factorization** $$S = L\,D\,L^{T},$$ which requires $n^3 / 3$ flops. Here $L$ is *unit lower triangular matrix* and $D$ is the *diagonal matrix*.
>	- The solution can be obtained by solving three triangular systems $$L\,z = w, \quad D\,y = z, \quad L^{T}\beta = y$$
>- Or we can use **Cholesky factorization**  $$S = G\,G^{T},$$ which requires $n^3 / 3$ flops. Here $G$ is a *lower triangular matrix*. 
>	- The solution can be obtained by solving two triangular systems $$G\,y = w, \quad G^{T}\,\beta = y$$
>	- The total computation requires about $(m + n / 3)n^2$ flops

- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[LDU Factorization of Symmetric Matrix]]
- [[LU Factorization of Matrix]]
- [[Gaussian Elimination with Partial Pivoting]]
- [[Gaussian Elimination for General Linear System]]

### QR Factorization

![[Least Square Estimation with QR Factorization#^b530a4]]

![[Least Square Estimation with QR Factorization#^7f67c6]]


>[!info]
>In case for **undercomplete system** $n < m$
>
>An alternative way is to find the **QR factorization** of $X$ $$X = Q\,R$$ where $Q$ is orthogonal matrix, and $R$ is *upper triangular*.
>
 >Then the solution can be found via solving $$R\,\beta = Q^{T}b:= y$$
>- This is a *triangular system*
>- *QR factorization with MGS* requires about $2mn^2$ flops.
>- Apply the MGS to augmented matrix $$\left[ A, b \right] $$ would reduce the *dependency on the instability* of $Q$
>- The total computation requires about $2(m - n / 3)n^2$ flops. 
>	- This is **twice as much operations as needed** compared to *Choloksy factorization*.

- [[QR Factorization of Matrix]]
- [[Householder QR Factorization]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[Gram-Schmidt Orthogonalization]]


- [[Least Square Estimation with QR Factorization]]
- [[QR Factorization of Matrix]]

### Singular Value Decomposition

![[Least Square Estimation via Singular Value Decomposition#^9f2cf8]]

- [[Singular Value Decomposition of Linear Map]]
- [[Least Square Estimation via Singular Value Decomposition]]

### Iterative Methods 

- [[Classical Iterations to approximate Solution of Sparse Linear System]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Normal Equation Residual and CGNER]]




## Explanation

### Comparison of Numerical Methods to Solve Least Square Problem

>[!quote]
>It is instructive to compare the normal equation and QR approaches to the full-rank  LS problem in light of Theorem 5.3.1.  
>- The method of normal equations (e.g. **Cholosky factorization**) produces an $x_{LS}$ whose **relative error** depends on $\kappa_{2}(A)^2$, a factor that can be considerably larger than the **condition number** associated with a **"small residual" LS problem**.  
>- The **QR approach** (**Householder**, **Givens**, **careful MGS**) solves a **nearby LS problem**. Therefore, these methods produce a computed solution with **relative error** that is "predicted" by the **condition** *of the underlying LS problem*.  
>
>Thus, the **QR approach is more appealing** in situations where $b$ is *close to the span of $A$'s columns*. 
>
>Finally, we mention **two other factors** that figure in the debate about *QR versus normal equations*. **First**, the **normal equations approach** involves about **half of the  arithmetic** when $m \gg n$ and does **not require as much storage**, assuming that $Q(:, 1:n)$ is required. **Second**, **QR approaches** are applicable to a **wider class of LS problems**. This is because the Cholesky solve in the method of normal equations is "*in trouble*" if $\kappa_{2}(A) \approx 1 / \sqrt{ u }$ while the *R-solve step* in a QR approach is in trouble only if $\kappa_{2}(A) \approx 1 / u$. Choosing the "right" algorithm requires having an appreciation for these **tradeoffs**.
>
>-- [[Matrix Computations by Golub]] pp 268


## Comparison of Time Complexity

| Method                                                  | Flops             |
| ------------------------------------------------------- | ----------------- |
| **Cholesky Factorization** and **Gaussian Elimination** | $\dfrac{2n^3}{3}$ |
| **Householder QR**                                      | $\dfrac{4n^3}{3}$ |
| **Modified Gram-Schmidt**                               | $2n^3$            |
| **Singular Value Decomposition**                        | $12n^3$           |



>[!quote]
>Although **Gaussian elimination** involves the least amount of arithmetic, there are three reasons why an orthogonalization method might be considered:
>- The flop counts tend to exaggerate the **Gaussian elimination** advantage. When *memory traffic* and *vectorization overheads* are considered, the **QR approach** is comparable in efficiency. 
>- The **orthogonalization methods** have **guaranteed stability**; there is no "*growth factor*" to worry about as in Gaussian elimination. 
>- In cases of **ill-conditioning**, the *orthogonal methods* give an added measure of reliability. QR with condition estimation is very dependable and, of course, SVD is *unsurpassed* when it comes to producing a meaningful solution to a nearly singular system.
>  
>We are not expressing a strong preference for orthogonalization methods but merely suggesting viable alternatives to Gaussian elimination.  
>  
>-- [[Matrix Computations by Golub]] pp 298 - 299  



-----------
##  Recommended Notes and References

- [[Forward Stagewise Additive Modeling]]


- [[Fundamental Subspaces from Linear Map]]
- [[Fundamental Orthogonal Projections]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Projection Map onto Linear Subspace]]

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Matrix]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]] pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245 - 269
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56
- [[Matrix Computations by Golub]] pp 303 - 334