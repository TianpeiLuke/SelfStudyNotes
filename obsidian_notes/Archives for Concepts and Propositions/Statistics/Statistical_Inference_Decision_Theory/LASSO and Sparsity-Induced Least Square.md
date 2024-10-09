---
tags:
  - concept
  - statistics/estimation
  - machine_learning/models
  - machine_learning/theory
  - optimization/regularization
  - optimization/convex_optimization
keywords:
  - lasso
  - sparsity
  - l1_regularization
  - basis_pursuit
topics:
  - statistics/estimation
name: LASSO and Sparsity-Induced Least Square
date of note: 2024-07-24
---

## Concept Definition

>[!important]
>**Name**: LASSO and Sparsity-Induced Least Square

![[Linear Regression#^24812d]]

- [[Linear Regression]]

![[Least Square Estimation#^9775a7]]

>[!important] Definition
>Consider a *linear regression model*
>$$
>Y = \sum_{i=1}^{d}\beta_{i}\,X^{i} + \beta_{0} + \epsilon,
>$$
>where $X := (X^1 \,{,}\ldots{,}\,X^{d})\in \mathbb{R}^{d}$ and $Y\in \mathbb{R}$.
>
>The **least absolute shrinkage and selection operator**, or **LASSO**, or **lasso estimate** are the value $\hat{\beta} := (\hat{\beta}_1 \,{,}\ldots{,}\,\hat{\beta}_d,\,\hat{\beta}_{0})$ that minimize the constrained optimization problem
>$$
>\begin{align*}
>\hat{\beta} = \arg\min_{\beta}& \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2 \\[5pt]
> \text{s.t. }& \sum_{i=1}^{s}\lvert \beta_{i} \rvert \le t 
\end{align*}
>$$
>where 
>- the loss term is the *regression loss* $$\mathbb{E}_{ p }\left[  L_{LS}(Y, f(X)) \right] := \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2$$
>- the constraint set $$\mathcal{S} = \{ \beta\in \mathbb{R}^{d}: \lVert \beta \rVert_{1} \le t  \}$$ is a *polyhedron*.
>
>In matrix form, we can write the LASSO estimation problem as *least square problem* with **$\ell_{1}$ norm constraint** (i.e. *linear constraint*) $$\begin{align*}\min_{\beta}&\; \lVert X\beta - y \rVert_{2}^2  \\[5pt]\text{s.t. }& \lVert \beta \rVert_{1}  \le t \end{align*}$$
>  
>- This is a **quadratic programming** problem.  
>- The corresponding problem is also called the **sparse linear regression.**

^9e20a2

- [[Constrained Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Quadratic Programming]]


>[!important] Definition
>**LASSO** can be written  in the **Lagrangian form**  as the **$\ell_{1}$-regularized residual sum of squares**
>$$
>\hat{\beta} = \arg\min_{\beta} \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2 + \lambda \sum_{i=1}^{d}|\beta_{i}|
>$$ 
>where  
>- the second term is the **$\ell_{1}$ regularization term** or the **sparse-inducing regularization** term
>$$
>  \lambda \lVert \beta \rVert_{1} := \lambda \sum_{i=1}^{d}|\beta_{i}|
>$$
>
>
>The **LASSO** can be formulated in matrix form as the **regularized least square** problem
>$$
>\min_{\beta\in \mathbb{R}^{d+1}}\; \lVert X\beta - y \rVert_{2}^2 + \lambda \lVert \beta \rVert_{1}  
>$$
>where 
>- $y := (Y_{1} \,{,}\ldots{,}\,Y_{m})\in \mathbb{R}^{m}$,  
>- $$X = \left[ \begin{array}{ccccc}X_{1}^{1}& X_{1}^{2}& \ldots & X_{1}^{d} & 1\\ X_{2}^{1}& X_{2}^{2}& \ldots & X_{2}^{d}& 1 \\ \ldots & \ldots & \ldots & \ldots & \ldots \\ X_{m}^{1}& X_{m}^{2}& \ldots & X_{m}^{d} & 1  \end{array} \right]\in \mathbb{R}^{m\times (d+1)},$$

- [[Least Square Estimation]]
- [[Regularized Loss Minimization]]
- [[Methods of Lagrangian Multipliers]]

### Basis Pursuit

>[!important] 
>**LASSO** is also known as **basis pursuit.**
>
>The common formulation of the **basis pursuit** problem or **basis pursuit linear program** is to solve the **$\ell_{1}$ norm minimization problem** with *affine equality constraint*
>$$
>\begin{align}
> \min_{\beta\in \mathbb{R}^{d}} &\; \lVert \beta \rVert_{1}\\[5pt]
>\text{s.t. }& X\beta = y 
>\end{align}
>$$

- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 200

>[!info]
>Same as LASSO, if we could solve this problem, then we would obtain a *solution* to the *linear equations* that has the **fewest number of non-zero entries**.


### LASSO Estimate as Soft-Thresholding of Least Square Estimate

>[!important]
>Let $\hat{\beta}^{LS}$ be the correspond *least square estimate*, i.e. $$\hat{\beta}^{LS} = \arg\min_{\beta} \lVert X\beta - y \rVert_{2}^2$$
>
>Assume that $X$ has **orthonormal columns**, i.e. $X^{T}X = I$.
>
>Then the **LASSO estimate** $\hat{\beta}^{LASSO}$ can be obtained by **soft-thresholding** on least square estimate as
>$$
>\begin{align}
>\hat{\beta}^{LASSO}_{i} &= \text{sgn}(\hat{\beta}^{\text{LS}}_{i})\;\left[ |\hat{\beta}_{i}^{\text{LS}}| - \lambda \right]_{+}, &\quad i=1\,{,}\ldots{,}\,d\\[5pt] 
>&= \left\{\begin{array}{cl} \hat{\beta}_{i}^{\text{LS}} -\lambda &\text{ if }\hat{\beta}_{i}^{\text{LS}} \ge \lambda > 0 \\[5pt] \hat{\beta}_{i}^{\text{LS}} +\lambda &\text{ if }\hat{\beta}_{i}^{\text{LS}} \le -\lambda < 0 \\[5pt] 0 & \text{ otherwise}\end{array}  \right. \\[5pt] 
>&= \text{soft-thresholding}(\,\hat{\beta}^{\text{LS}}_{i}\,,\, \lambda)
>\end{align}
>$$
>where $$[x]_{+} = \max\{ 0, x\}.$$

^4e9f00

- [[Rectified Linear Unit as Activation for Deep Learning]]

>[!important] Definition
>The **soft-thresholding function** or **shrinkage operation** is defined as  
>$$
>\begin{align}
>&\text{soft-thresholding}(x, \lambda)  \\[5pt]
>&:= \text{shrinkage}(x, \lambda) \\[5pt]
>&:= \text{sgn}(x)\;\left[ |x| - \lambda \right]_{+} \\[10pt] 
>&= \left\{\begin{array}{cl} x-\lambda &\text{ if }x \ge \lambda > 0 \\[5pt] x +\lambda &\text{ if }x \le -\lambda < 0 \\[5pt] 0 & \text{ otherwise}\end{array}  \right. \\
>\end{align}$$
>
>- This function *remove all* $x$ whose *absolute value* is *less than* $\lambda$.
>- For $|x| \ge \lambda$, the *absolute value* is *reduced* by $\lambda$.
>- The **shrinkage operation** can be defined using the *proximal operation* $$\text{shrinkage}(x, \lambda) = \arg\min_{z} \left\{  \lVert x \rVert_{1} + \frac{1}{2\lambda}\lVert x - z \rVert_{2}^2   \right\} $$

- [[Proximal Algorithm]]
- [[Augmented Lagrangian Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]


>[!info]
>Soft-thresholding function is commonly used in **wavelet-based smoothing.**

- [[Wavelet]]


## Explanation

>[!quote]
>Because of the nature of the constraint, making t sufficiently small will cause some of the coefficients to be exactly zero. Thus the lasso does a kind  of **continuous subset selection**. 
>
>If $t$ is chosen larger than $$t_{0} = \sum_{j=1}^{p}\lvert \hat{\beta}_{j} \rvert $$ (where $\hat{\beta}_{j} = \hat{\beta}_{j}^{LS}$, the *least squares estimates*), then the **lasso estimates** are the $\hat{\beta}_{j}$’s. 
>
>On the other hand, for $t = t_{0}/2$ say, then the *least squares coefficients* are **shrunk** by about 50% on average. However, *the nature of the shrinkage is not obvious*, and we investigate it further in Section 3.4.4 below. Like the subset size in variable subset selection, or the penalty parameter in ridge regression, $t$ should be *adaptively chosen* to minimize an estimate of expected prediction error.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 69

>[!important] 
>The **LASSO** estimate is the **convex relaxation** of the general **sparse linear regression problem** which originally modeled using $\ell_{0}$ norm:
>$$
>\begin{align}
> \min_{\beta\in \mathbb{R}^{d}} &\; \lVert \beta \rVert_{0}\\[5pt]
>\text{s.t. }& X\beta = y 
>\end{align}
>$$
>or
>$$
>\begin{align*}
>\min_{\beta}&\; \lVert X\beta - y \rVert_{2}^2  \\[5pt]
> \text{s.t. }& \lVert \beta \rVert_{0}  \le t 
\end{align*}
>$$
>
>Here **$\ell_{0}$ norm** is defined as the **support** of vector $x$, i.e. the *count* of *nonzero entries in a vector* $$\lVert x \rVert_{0} = \text{supp}(x) := \lvert \{ i: x_{i} \neq 0 \} \rvert  $$

- [[Support of Measure]]

## $\ell_{1}$ vs $\ell_{2}$ Regularization

![[Ridge Regression and L2 Regularization#^8d2b54]]

![[LASSO and Sparsity-Induced Least Square#^4e9f00]]

- [[Ridge Regression and L2 Regularization]]

![[ridge_regression_lasso.png]]





-----------
##  Recommended Notes and References


- [[Laplace Distribution]]
- [[Partial Least Square]]





- [[Gaussian Graphical Model]]
- [[Conditional Independence]]

- [[Schur Complement and Inversion of Block Matrix]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]

- [[Convex Optimization Problem]]


- [[Elements of Statistical Learning by Hastie]] pp 68 - 79
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 198, 200, 262 - 265
- [[High Dimensional Probability An Introduction by Vershynin]] pp 263 - 267
- [[Convex Optimization by Boyd]] pp 184, 205
- [[Convex Optimization Algorithms by Bertsekas]] pp 27 - 29, 286 - 288
- Wikipedia [Partial_correlation](https://en.wikipedia.org/wiki/Partial_correlation)