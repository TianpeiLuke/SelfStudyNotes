---
tags:
  - concept
  - statistics/estimation
  - optimization/regularization
  - deep_learning/regularization
  - machine_learning/models
  - machine_learning/algorithms
keywords:
  - ridge_regression
  - l2_regularization
topics:
  - statistics/estimation
  - deep_learning/regularization
  - statistics/regularization
name: Ridge Regression and L2 Regularization
date of note: 2024-08-22
---

## Concept Definition

>[!important]
>**Name**: Ridge Regression and L2 Regularization

![[Linear Regression#^06ce34]]

- [[Linear Regression]]

### Ridge Regression as the $\ell_{2}$ Regularized Least Square

>[!important] Definition
>Consider a *linear regression model*
>$$
>Y = \sum_{i=1}^{d}\beta_{i}\,X^{i} + \beta_{0} + \epsilon,
>$$
>where $X := (X^1 \,{,}\ldots{,}\,X^{d})\in \mathbb{R}^{d}$ and $Y\in \mathbb{R}$.
>
>The **ridge regression** are the value $\hat{\beta} := (\hat{\beta}_1 \,{,}\ldots{,}\,\hat{\beta}_d,\,\hat{\beta}_{0})$ that minimize the **$\ell_{2}$-regularized residual sum of squares**
>$$
>\hat{\beta} = \arg\min_{\beta} \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2 + \lambda \sum_{i=1}^{d}\beta_{i}^2
>$$
>where 
>- the first term is the *regression loss* $$\mathbb{E}_{ p }\left[  L_{LS}(Y, f(X)) \right] := \sum_{s=1}^{m}\left[ Y_{s} - \left( \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \beta_{0} \right)\right]^2$$
>- and second term is called the **$\ell_{2}$ regularization term** or the **Tikhonov regularization**
>$$
>  \lambda \lVert \beta \rVert_{2}^2 :=   \lambda \sum_{i=1}^{d}\beta_{i}^2
>$$
>
>
>The **ridge regression** can be formulated in matrix form as the **regularized least square** problem
>$$
>\min_{\beta\in \mathbb{R}^{d+1}}\; \lVert X\beta - y \rVert_{2}^2 + \lambda \lVert \beta \rVert_{2}^2  
>$$
>where 
>- $y := (Y_{1} \,{,}\ldots{,}\,Y_{m})\in \mathbb{R}^{m}$,  
>- $$X = \left[ \begin{array}{ccccc}X_{1}^{1}& X_{1}^{2}& \ldots & X_{1}^{d} & 1\\ X_{2}^{1}& X_{2}^{2}& \ldots & X_{2}^{d}& 1 \\ \ldots & \ldots & \ldots & \ldots & \ldots \\ X_{m}^{1}& X_{m}^{2}& \ldots & X_{m}^{d} & 1  \end{array} \right]\in \mathbb{R}^{m\times (d+1)},$$

- [[Tikhonov Regularization in Optimization and Learning]]
- [[Regularized Loss Minimization]]

### Solution of Ridge Regression as $\ell_2$ shrinkage

>[!info]
>
>We can use *necessary condition* of optimal solution to derive the solution of ridge regression, i.e.
>$$
>\nabla_{\beta} L = 2\left(X\beta - y\right)^{T}\,X+ 2\,\lambda\,\beta^{T} = 0
>$$
>Note that the problem is *convex*, thus this is both *necessary and sufficient* condition for the solution. Thus the solution can be obtained by solving the **normal equation**
>$$
>\left(X^{T}X+ \lambda I\right)\beta = X^{T}y
>$$

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Convex Optimization Problem]]

>[!important] Definition
>The **solution for ridge regression** is of the form
>$$
>\hat{\beta}^{\text{Ridge}} = \left(X^{T}X + \lambda I\right)^{-1}\,X^{T}y
>$$
>- If $X$ has *orthonormal columns*, i.e. $X^{T}X = I$, then $$\hat{\beta}^{\text{Ridge}} = \frac{1}{1 + \lambda} X^{T}y = \frac{1}{1 + \lambda} \hat{\beta}^{\text{LS}}$$
>- This shows that the effect of $\ell_{2}$ regularization is to do **a proportional shrinkage** for *every coordinate*.

^8d2b54


### Solution via SVD

![[Least Square Estimation via Singular Value Decomposition#^9f2cf8]]

![[Sherman–Morrison–Woodbury Matrix Inversion Formula#^57a83b]]

>[!important] Definition
>Consider the **singular value decomposition** of design matrix $X \in \mathbb{R}^{m\times d}$ as
>$$
>  X = U\,\Sigma\,V^{T} = \sum_{i=1}^{d}\sigma_{i}\,u_{i}\,v_{i}^{T}.
>$$
>
>Then 
>$$
>\begin{align*}
> X\hat{\beta}^{\text{Ridge}} &= X\left(X^{T}X + \lambda I\right)^{-1}\,X^{T}y \\[5pt]
> &= U\,\Sigma\,V^{T}\left(V\Sigma^{T}\Sigma V^{T} + \lambda I\right)^{-1}V\,\Sigma^{T}\,U^{T}y\\[5pt]
> &=  U\,\Sigma\,V^{T}\left[\lambda^{-1} I - \lambda^{-2}V\left((\Sigma^{T}\Sigma)^{-1}  + \lambda^{-1}I\right)^{-1}V^{T}   \right] V\,\Sigma^{T}\,U^{T}y\\[5pt]
> &= U\,\Sigma\,\left[\lambda^{-1} I - \lambda^{-2}\left((\Sigma^{T}\Sigma)^{-1}  + I\right)^{-1}   \right] \,\Sigma^{T}\,U^{T}y\\[5pt]
> &= \sum_{i=1}^{d}u_{i} \left(\frac{\sigma_{i}^2}{\sigma_{i}^2 + \lambda}\right)u_{i}^{T}y
>\end{align*}
>$$
>- Like *linear regression*, **ridge regression** computes the coordinates of $y$ with respect to the *orthonormal basis* $U$. 
>- It then **shrinks these coordinates** by the factors $$ \left(\frac{\sigma_{i}^2}{\sigma_{i}^2 + \lambda}\right).$$
>
>The solution of *ridge regression* can be represented as
>$$
>\begin{align*}
>\hat{\beta}^{\text{Ridge}} = \sum_{i=1}^{d} \left(\frac{\sigma_{i}}{\sigma_{i}^2 + \lambda}\right) \left\langle  u_{i}\,,\,y    \right\rangle\,v_{i}
>\end{align*}
>$$
>- Compare to least square solution $$\hat{\beta} = \sum_{i=1}^{d}\,\frac{1}{\sigma_{i}}\,\left\langle u_{i} , y \right\rangle v_{i}$$
>- We see that the **effect of $\ell_{2}$ regularization** is that when $\sigma_{i} \to 0$, the solution of ridge regression still **numerically stable** as $$\sigma_{i} \to 0 \implies \left(\frac{\sigma_{i}}{\sigma_{i}^2 + \lambda}\right) \to 0$$ while the least square solution is *not stable*.

- [[Least Square Estimation via Singular Value Decomposition]]
- [[Singular Value Decomposition of Linear Map]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]



## Explanation



## Solution via Least Square Estimation

>[!info]
>The **ridge regression** problem solves
>$$
>\min_{x} \; \lVert Ax - b \rVert_{2}^2 + \lambda\,\lVert x \rVert_{2}^2  
>$$
>This is equivalent to solve a **least square** problem with **augmented design matrix**
>$$
>\min_{x}\; \lVert \widetilde{A}\,x -   \widetilde{b}\rVert^2 
>$$
>where $$\widetilde{A}:= \left[ \begin{array}{c}A\\[5pt] \sqrt{ \lambda}I \end{array} \right]$$ and $$\widetilde{b}:= \left[ \begin{array}{c}b\\[5pt] 0 \end{array} \right]$$
>- Check [[Algorithms for Least Square Estimation Problem]] for algorithms to solve least square problem.
>- Check [[Quadratic Programming]] for QP solvers

- [[Algorithms for Least Square Estimation Problem]]
- [[Least Square Estimation]]



## SVD of Ridge Regression





## $\ell_{1}$ Regularized Regression

- [[LASSO and Sparsity-Induced Least Square]]


-----------
##  Recommended Notes and References



- [[Regression Problem]]
- [[Minimum Mean Square Estimation]]
- [[Quadratic Programming]]

- [[Elements of Statistical Learning by Hastie]] pp 61 - 68, 650, 659
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 613 - 617
- [[Deep Learning Foundations and Concepts by Bishop]] pp 163
- [[Matrix Computations by Golub]] pp 307
- [[Convex Optimization by Boyd]] pp 184, 205
- [[Convex Optimization Algorithms by Bertsekas]] pp 26 - 27