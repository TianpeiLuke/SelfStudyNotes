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
>**Name**: 



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


- [[Linear Regression]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Regularized Loss Minimization]]



- [[Regression Problem]]
- [[Minimum Mean Square Estimation]]
- [[Quadratic Programming]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 613 - 617
- [[Deep Learning Foundations and Concepts by Bishop]] pp 163
- [[Matrix Computations by Golub]] pp 307
- [[Convex Optimization by Boyd]] pp 184, 205
- [[Convex Optimization Algorithms by Bertsekas]] pp 26 - 27