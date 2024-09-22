---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - least_square_estimation
  - pseudo_inverse_matrix
  - projection_linear_subspace
topics:
  - statistics/estimation
name: Solution of Least Square Estimation and Geometric Interpretation
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Solution of Least Square Estimation and Geometric Interpretation

![[Linear Regression#^b406ef]]

![[Linear Regression#^8d6149]]

![[Least Square Estimation#^9775a7]]

![[Least Square Estimation#^f8f306]]

- [[Least Square Estimation]]
- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]

### Solution of Linear Least Square Estimation

>[!important] Theorem
>Suppose $y\in \mathbb{R}^{m}$, and $X\in \mathbb{R}^{m\times d}$ has **linearly independent columns**.
>
>Then there exists a **unique vector** $\hat{\beta}\in \mathbb{R}^{d}$ that *minimizes the mean squared error* $$\hat{\beta} = \arg\min_{\beta}\;\lVert y - X\beta \rVert_{2}^2$$ over all $\beta$.
>
>Furthermore, the **optimal vector** $\hat{\beta}$ is
>$$
>\hat{\beta} = \left( X^{T}\,X \right)^{-1}\,X^{T}y.
>$$

^17b91f

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 82
- [[Moore–Penrose Pseudo Inverse of Matrix]]

>[!important]
>For **univariate linear regression** $d=1$, the solution is
>$$
>\hat{\beta} = \frac{\left\langle  x\,,\,y    \right\rangle}{\left\langle  x\,,\,x    \right\rangle}, \quad r = y - x\hat{\beta}
>$$
>where $y, x \in \mathbb{R}^{m}$.

^76f8a3


>[!info] Proof
>$$
>\begin{align*}
> RSS(\beta) &= \lVert y - X\beta \rVert_{2}^2\\
> &= \left( y - X\beta \right)^T\,\left( y - X\beta \right) 
>\end{align*}
>$$
>Thus
>$$
>\begin{align*}
> \nabla_{\beta} RSS(\beta) &= \nabla_{\beta}  \left( y - X\beta \right)^T\,\left( y - X\beta \right) \\
> &= -2X^T \left( y - X\beta \right)
>\end{align*}
>$$
>From [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]], the optimal solution $\hat{\beta}$ satisfies the equation
>$$
>X^T \left( y - X\beta \right) = 0
>$$
>Since $\text{Rank}(X) = d$, we see that $X^{T}X$ is *invertible*. Thus
>$$
>\hat{\beta} =  \left( X^{T}\,X \right)^{-1}\,X^{T}y
>$$

- [[Secant Equation and Quasi-Newton Methods]]

>[!important] Definition
>The equation
>$$
>X^{T}X\;\beta = X^{T}y
>$$
>is called the **normal equations** for *linear least square estimation*.

^03c5db

- [[Range and Kernel of Product Map and Normal Map]]
- [[Normal Transformation]]

>[!info]
>Note that 
>$$
>X^{\dagger} := \left( X^T\,X \right)^{-1}\,X^{T}
>$$
>is called the **Moore–Penrose pseudo-inverse** of matrix $X$. Then the least square estimate can be represented as
>$$
>\hat{\beta} = X^{+}y
>$$

- [[Moore–Penrose Pseudo Inverse of Matrix]]

### Algorithm for Solving Least Square Estimation

- [[Algorithms for Least Square Estimation Problem]]

## Explanation

>[!important]
>The **least square estimation** only requires the space $\mathcal{H}$ defines the product $\left\langle  ,  \right\rangle_{\mathcal{H}}$.  Thus, we can generalize the least square problem as the *orthogonal projection* of $y$ to a **Hilbert subspace** $\mathcal{S} \subset \mathcal{H}$
>
>$$
>  \min_{\hat{y} \in \mathcal{S}} \;\lVert y - \hat{y} \rVert_{\mathcal{H}}^2 
>$$

- [[Projection Theorem of Hilbert Spaces]]
- [[Hilbert Space]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[Operations that Preserve Convexity]]

## Geometric Interpretation

>[!important] 
>The **least square estimation problem** can be seen as the **orthogonal projection** of *response* variable $y$ to the *subspace* spanned by *covariates* $X$
>$$
> \hat{y} = \arg\min_{\hat{y} \in \text{span}(X)} \lVert y - \hat{y} \rVert_{2}^2    \implies  \hat{y} = X\hat{\beta} = P_{X}\,(y)
>$$
>where  $\hat{\beta}$ is the *least square estimate* of $\beta$ and $$P_{X}: \mathbb{R}^{m} \to \text{span}\left\{ X \right\}$$ is the **orthogonal projection map**.
>-  $P_{X}$ has the **matrix representation**
>$$
>P_{X} := X\left( X^T\,X \right)^{-1}\,X^{T} \in \mathbb{R}^{m\times m}
>$$
>- To see this, we show that $P_{X}$ is **idempotent**
>$$
> \begin{align*}
> P_{X}^2 &=  X\left( X^T\,X \right)^{-1}\,X^{T}\, X\left( X^T\,X \right)^{-1}\,X^{T} \\
> &=  X\left( X^T\,X \right)^{-1}\,X^{T} \\[5pt]
> &= P_{X}
> \end{align*}
> $$
>
>- The **orthogonal decomposition** of $y$ is
>$$
>\begin{align*}
>y &=  X \hat{\beta} + (y -  X \hat{\beta})\\[5pt]
>&= X\left( X^T\,X \right)^{-1}\,X^{T}y + \left( I -  X\left( X^T\,X \right)^{-1}\,X^{T}\right)y \\[5pt]
>&:= y_{\parallel} + y_{\perp}
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\left\langle y_{\parallel} \,,\,  y_{\perp} \right\rangle &= y^{T}X\left( X^T\,X \right)^{-1}\,X^{T}\,\left[ \left( I -  X\left( X^T\,X \right)^{-1}\,X^{T}\right)y\right] \\[5pt]
>&= 0
>\end{align*}
>$$

^c0f78a

- [[Fundamental Orthogonal Projections]]
- [[Projection Map onto Linear Subspace]]
- [[Projection Theorem of Hilbert Spaces]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[Hilbert Space]]

## General Solution of Linear Least Square Estimation

>[!important] Theorem
>Let $X\in \mathbb{R}^{n\times d}$, and $y\in \mathbb{R}^{n}$.
>
>The **general solution** of **linear least square estimation** $$\hat{\beta} = \arg\min_{\beta} \lVert X\beta - y \rVert_{2}^2$$ is of the form
>$$
>\begin{align*}
>\beta &= X^{+} y + \left(I- X^{+}X\right)z \\[5pt]
>&= P_{\text{Ker}(X)^{\perp}}\left(X^{+}y\right) + P_{\text{Ker}(X)}z
>\end{align*}
>$$
>where $z\in \mathbb{R}^{d}$ is *arbitrary*.
>- The solution is **unique** if $X$ has **full column rank** i.e. $$\text{rank}(X) = d \; \iff \; X^{+}X = I$$

^0bdae8

- [[Fundamental Orthogonal Projections]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 65 - 66

## Solution of Linear System

![[Existence and Uniqueness of Solution of Linear Equations#^1dcd93]]

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]



-----------
##  Recommended Notes and References


- [[Moore–Penrose Pseudo Inverse of Matrix]]

- [[Projection Map onto Linear Subspace]]
- [[Projection Theorem of Hilbert Spaces]]
- [[Orthogonal Complement of Hilbert Spaces]]

- [[Linear Regression]]
- [[Regression Problem]]
- [[Gauss–Markov Theorem]]
- [[Point Estimator]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]] pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245 - 269
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56
- [[Matrix Computations by Golub]] pp 303 - 334
- [[Numerical Linear Algebra by Trefethen]] pp 77 - 87
- [[Deep Learning Foundations and Concepts by Bishop]] pp 117
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 65 - 67