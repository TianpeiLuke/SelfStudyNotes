---
tags:
  - concept
  - optimization/algorithm
  - statistics/estimation
  - machine_learning/models
  - machine_learning/algorithms
keywords:
  - least_square_estimation
  - linear_regression
  - qr_factorization
  - successive_orthogonalization
topics:
  - optimization/algorithm
  - statistics/estimation
  - machine_learning_algorithm
name: Least Square Estimation with QR Factorization
date of note: 2024-08-20
---

## Concept Definition

>[!important]
>**Name**: Least Square Estimation with QR Factorization

![[Linear Regression#^24812d]]

![[Least Square Estimation#^9775a7]]

 ![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]
![[Least Square Estimation Solution and Geometric Interpretation#^76f8a3]]

- [[Least Square Estimation Solution and Geometric Interpretation]]

>[!important] Definition
>Consider the *linear least square estimation problem* 
>$$
>Y_{s} = \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} + \epsilon_{s},\; \quad s=1 \,{,}\ldots{,}\,m.
>$$
>where $\epsilon_{s}|X_{s} \sim \mathcal{N}(0, \sigma^2)$.
>
>The least square coefficient $\hat{\beta}_{d}$ can be solved via a **successive orthogonalization algorithm** as follow
>- *Require* $(Y, X)$ where
>	- the *response* $Y = (Y_{1} \,{,}\ldots{,}\,Y_{m})$
>	- the *design matrix* $X = (1, X^1 \,{,}\ldots{,}\,X^{d})^{T}\in \mathbb{R}^{m\times (d+1)}$
>		- each row $X^{i} = (X_{1}^{i} \,{,}\ldots{,}\,X_{m}^{i})$ for $i=1\,{,}\ldots{,}\,d$
>- *Initialize* $r_{0} = X^{0} = 1$
>- For $i=1\,{,}\ldots{,}\,d$:
>	- **Regress** $X^{i}$ on $\left(r_{0} \,{,}\ldots{,}\,r_{i-1}\right)$ to produce 
>		- the **coefficients** $$\hat{\gamma}_{j,i} = \frac{\left\langle  r_{j}\,,\,X^{i} \right\rangle}{\left\langle  r_{j}\,,\,r_{j}    \right\rangle},\quad j=1 \,{,}\ldots{,}\,i-1$$
>		- and the **residual vector** $$r_{i} = X^{i} - \sum_{j=1}^{i-1}\hat{\gamma}_{j,i}\;r_{j}$$
>- **Regress** $Y$ on the **residual vector** $r_{d}$ to give the estimate $\hat{\beta}_{d}$ $$\hat{\beta}_{d} = \frac{\left\langle  r_{d}\,,\,Y \right\rangle}{\left\langle  r_{d}\,,\,r_{d}    \right\rangle}$$
>
>Note that by rearranging $(X^1 \,{,}\ldots{,}\,X^{d})$, any one of them could be in the last position, hence the above algorithm solves any least square coefficient $\hat{\beta}_{i}$ for $i=1\,{,}\ldots{,}\,d$ .


>[!info]
>The residual vectors are **orthogonal** to each other.
>$$\left\langle  r_{i}\,,\,r_{j}    \right\rangle = \lVert r_{i} \rVert  \delta_{i,j}$$

### QR Factorization

>[!important]
>The **successive orthogonalization algorithm** can be represented in matrix form as
>$$
>X = Z\,\Gamma
>$$
>where 
>- $Z = [r_{0} \,{,}\ldots{,}\,r_{d}]\in \mathbb{R}^{m\times (d+1)}$ whose *columns* are *residual vectors* and are *orthogonal* to each other.
>- $\Gamma$ is an *upper triangular matrix* with entries as $\hat{\gamma}_{j,i}$.
>  
>Define $D = \text{diag}\{\lVert r_{1} \rVert \,{,}\ldots{,}\, \lVert r_{d} \rVert \}$ is a *diagonal matrix.* We can represent the above matrix factorization as
>$$
>\begin{align*}
>X &= Z\,D^{-1}\,D\,\Gamma \\[5pt]
>&= Q\, R
>\end{align*}
>$$
>where $$Q = \left[\lVert r_{0} \rVert^{-1} \,r_{0} \,{,}\ldots{,}\,\lVert r_{d} \rVert^{-1} \,r_{d}\right] \in \mathbb{R}^{m\times (d+1)} \text{ is orthogonal matrix}$$ so that $$Q^{T}Q = I_{d+1}$$ and $$R = D\,\Gamma \in \mathbb{R}^{(d+1) \times (d+1)} \text{ is upper triangular matrix}.$$
>
>This is the **QR factorization** of data $X$.
>

- [[QR Factorization of Matrix]]

### Least Square via QR Factorization

>[!important] Definition
>Given the **QR factorization** of design matrix $X\in \mathbb{R}^{m\times (d+1)}$, the *least square estimate* $\hat{\beta}$ of $\beta$ is given by 
>$$
>\begin{align*}
> \hat{\beta} &= R^{-1}\,Q^{T}\,y\\
> \hat{y} &= Q\,Q^{T}\,y.
>\end{align*}
>$$
>Note that since $R$ is an *upper triangle matrix*, it is easy to solve the system of equations
>$$
>R\,\hat{\beta} = Q^{T}\,y
>$$





## Explanation

>[!important]
>The algorithm above is the **Gram-Schmidt procedure** for multiple regression.

- [[Gram-Schmidt Orthogonalization]]




-----------
##  Recommended Notes and References

- [[Linear Regression]]
- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 182
- [[Optimization by Vector Space Methods by Luenberger]] pp 78 - 102
- [[Numerical Optimization by Nocedal]] pp 245 - 269
- [[Elements of Statistical Learning by Hastie]] pp 43 - 56