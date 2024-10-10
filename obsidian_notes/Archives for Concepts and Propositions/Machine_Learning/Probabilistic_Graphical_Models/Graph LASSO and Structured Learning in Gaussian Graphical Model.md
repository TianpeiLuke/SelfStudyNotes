---
tags:
  - concept
  - statistics/estimation
  - probabilistic_graphical_models/inference
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/models
  - statistics/concentration_inequality
keywords:
  - graph_lasso
  - inverse_convariance_estimation
  - gaussian_graphical_model
topics:
  - statistics/estimation
  - probabilistic_graphical_model
  - concentration_inequality
name: Graph LASSO and Structured Learning in Gaussian Graphical Model
date of note: 2024-07-24
---

## Concept Definition

>[!important]
>**Name**: Graph LASSO and Structured Learning in Gaussian Graphical Model

### $\ell_{1}$ Regularized Estimation for High Dimensional Problem

>[!quote]
>Whenever $n < d$, the sample covariance matrix is always **rank-deficient**, so that the **maximum likelihood estimate does not exist**. In this setting, some form of regularization is essential. When the graph $G$ is expected to have relatively *few edges*, a natural form of regularization is to impose an **$\ell_1$-constraint** on the entries of $\Theta$. (If computational considerations were not a concern, it would be natural to impose $\ell_0$-constraint, but as in Chapter 7, we use the **$\ell_1$-norm as a convex surrogate**.)
>
>-- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 354


>[!important] Definition
>Let $X_{i}\sim \mathcal{N}(0, \Theta^{-1})$ follow a *Gaussian graphical model* on $\mathcal{G} =(\mathcal{V}, \mathcal{E})$ where $\mathcal{G}$ is known. 
>
>The **Graph LASSO** estimation solves the following *$\ell_{1}$-regularized inverse covariance estimation*  problem
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(S\,\Theta\right) - \frac{1}{2}\log \det \Theta + \lambda \lVert \Theta \rVert_{1, \text{ off}} 
>\end{align*}
>$$
>where
>-  $S$ is the *sample covariance matrix* $$S = \frac{1}{n}X^{T}X$$ 
>-  the design matrix $X = [X_{1}\,{,}\ldots{,}\,X_{n}]^{T} \in \mathbb{R}^{n\times d}$ and $X_{i}\in \mathbb{R}^{d}$
>- and $$\lVert \Theta \rVert_{1, \text{ off}} = \sum_{i\neq j}|\theta_{i,j}|$$
>

- [[Gaussian Graphical Model]]
- [[Inverse Covariance Estimation]]
- [[Lp Space]]
- [[Operator p-Norm of Matrix]]
- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]


### Graph LASSO algorithm

![[Sparse Inverse Covariance Estimation for GGM with Known Structure#^eead22]]

>[!important] Definition
>Let $X\sim \mathcal{N}(0, \Theta^{-1})$ follow a *Gaussian graphical model* on $\mathcal{G} =(\mathcal{V}, \mathcal{E})$ where $\mathcal{G}$ is *unknown*. 
>
>Consider the problem of *Graph LASSO* which solves the following problem
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(S\,\Theta\right) - \frac{1}{2}\log \det \Theta + \lambda \lVert \Theta \rVert_{1, \text{ off}} 
>\end{align*}
>$$
>where $$\lVert \Theta \rVert_{1, \text{ off}} = \sum_{i\neq j}|\theta_{i,j}|$$
>
>The **Graph LASSO algorithm** for **Gaussian graphical model** is described as follow:
>- *Require*: regularization parameter $\lambda >0$
>- *Require*: The *sample covariance matrix* $$S := \frac{1}{n}X^{T}X$$ where $X_{i}\sim \mathcal{N}(0, \Theta)$
>- Initialize $$W \leftarrow S + \lambda I.$$ The **diagonal terms** remain unchanged.
>- Loop until convergence:
>	- For $j=1\,{,}\ldots{,}\,d$: 
>		- **Partition** matrix $W$ along the $j$-th row and $j$-th column: $$\left[ \begin{array}{cc} W_{[-j], [-j]} & W_{[-j],j} \\[5pt] W_{[-j],j}^{T} & W_{j,j}\end{array} \right] := W$$ where 
>			- $W_{jj}\in \mathbb{R}$ and 
>			- $W_{[-j],j}\in \mathbb{R}^{d-1}$ and 
>			- $W_{[-j], [-j]} \in \mathbb{R}^{(d-1) \times (d-1)}$ are the *principal submatrix* excluding $j$-th column and row.
>		- **Partition** sample covariance matrix $S$ accordingly.
>		- **Solve the LASSO problem** $$\beta_{j} = \arg\min_{\beta}\,\frac{1}{2n}\lVert\, Z\beta - y\,\rVert_{2}^2 + \lambda \lVert \beta \rVert_{1}$$ where
>			- $$\frac{1}{n} Z^{T}Z = W_{[-j], [-j]},\;\; \frac{1}{n}Z^{T}y = S_{[-j],j}$$
>			- The solution satisfies the equation $$W_{[-j], [-j]}\,\beta_{j} - S_{[-j],j} + \lambda\,\text{sgn}(\beta_{j}) = 0$$ 
>			- Solve LASSO using **coordinate descent algorithm**.
>			- For $i\in [-j]$
>				- $$\beta_{i}^{(j)} \leftarrow \frac{1}{W_{i,i}}\text{Shrinkage}\left(  \left( S_{i,j} - \sum_{k  \neq i \in [-j]}W_{k,i}\beta_{k}^{(j)} \right) \;,\; \lambda \right)$$
>		- **Update** $j$-th column of $W$ except for the diagonal term $$W_{[-j],j} \leftarrow W_{[-j], [-j]}\,\beta_{j}$$
>		- If *final loop*, compute $\Theta$
>			- Update **diagonal term** in $j$-th column $$\Theta_{j,j} = (W_{j,j} - W_{[-j],j}^{T}\;\beta_{j})^{-1}$$
>			- Update **off-diagonal term** in $j$-th column $$\Theta_{[-j],j} = - \beta_{j}\,\Theta_{j,j} $$

![[LASSO and Sparsity-Induced Least Square#^5d43ca]]

- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]
- [[LASSO and Sparsity-Induced Least Square]]
- [[Block Coordinate Descent Algorithm]]



## Explanation

### Neighborhood Regression

>[!info]
>In the above process, in each iteration, the algorithm *updates the estimate* of the **parameters** of **GGM**  associated with the **nearest-neighborhood** of each node.
>
>The update is based on **neighborhood regression** model
>$$
>X^{(j)} = \left\langle X^{N(j)} , \beta_{N(j)} \right\rangle + \epsilon_{j}
>$$
>where each node value is *linearly dependent* on its **neighborhood**'s value.

>[!info]
>For **Graph LASSO**, the **support set** of $\beta_{j} := (\beta_{1}^{(j)}\,{,}\ldots{,}\,\beta_{d-1}^{(j)})$ determines the neighorhood
>$$
>N(j) := \left\{ i\in \mathcal{V} \setminus\,\left\{ j \right\}:\; |\beta_{i}^{(j)}| > 0 \right\}
>$$

>[!info]
>In **Graph LASSO**, it solves a **LASSO problem** for each node based on the **neighborhood regression** model
>$$
>X^{(j)} = \left\langle X^{[-j]} , \beta \right\rangle + \epsilon_{j}\; \quad |\text{supp}(\beta)| \le t
>$$
>


### Development of Algorithm

![[Sparse Inverse Covariance Estimation for GGM with Known Structure#^f40ca8]]

![[Sparse Inverse Covariance Estimation for GGM with Known Structure#^cf8a74]]

![[Sparse Inverse Covariance Estimation for GGM with Known Structure#^a124e2]]

>[!info]
>The **sub-gradient optimality condition** gives us
>$$
> S - \Theta^{-1} + \lambda\, \text{sgn}(\Theta)  = S - W + \lambda\, \text{sgn}(\Theta) = 0
>$$
>Therefore, considering the top right block of $W$
>$$
>\begin{align*}
>s_{12} - [\Theta^{-1}]_{12} + \lambda\, \text{sgn}(\theta_{12}) &= 0 \\[5pt]
> \implies s_{12} - w_{12} - \lambda\, \text{sgn}(\beta) &= 0
>\end{align*}
>$$
>Here $$\beta := -\theta_{12}\theta_{22}^{-1} \implies \text{sgn}(\beta) = - \text{sgn}(\theta_{12}).$$
>
>Thus we have the **equation** corresponding to the **subgradient optimality condition** 
>$$
> W_{11}\beta = s_{12}  - \lambda\, \text{sgn}(\beta) \quad (*)
>$$
>where  $$w_{12} = W_{11}\beta, \quad \beta := -\theta_{12}\theta_{22}^{-1}.$$ 

- [[Subgradient Methods]]
- [[Subdifferential of Convex Function]]

>[!info]
>For general LASSO problem
>$$
> \min_{\beta} \frac{1}{2} \lVert Z\beta - y \rVert_{2}^2   + \lambda \lVert \beta \rVert_{1} 
>$$
>the *sub-gradient optimality condition* is
>$$
>Z^{T}Z\beta - Z^{T}y + \lambda\, \text{sgn}(\beta) = 0
>$$
>Compare with above condition, we have
>- $$W_{11} = Z^{T}Z, \quad Z^{T}y = s_{12}$$
>- Then $\beta$ in $(*)$  solves the LASSO problem above.

>[!important]
>We can choose $$Z = [X_{1}\,{,}\ldots{,}\,X_{j-1}, X_{j+1}\,{,}\ldots{,}\,X_{d}]^{T} := X_{[-j]}\in \mathbb{R}^{n\times (d-1)}$$ and $$y = X_{j}$$
>Thus 
>$$
>Z^{T}Z \approx W_{[-j], [-j]}, \quad Z^{T}y = S_{[-j],j}
>$$
>So the **LASSO** problem becomes a regression
>$$
>\beta_{j} = \arg\min_{\beta} \frac{1}{2n} \lVert X_{[-j]}\beta - X_{j} \rVert_{2}^2   + \lambda \lVert \beta \rVert_{1} 
>$$
>which corresponds to the **neighborhood regression** $$X^{(j)} = \left\langle  X^{[-j]}\,,\, \beta_{j}  \right\rangle + \epsilon_{j} \equiv \left\langle  X^{N(j)}\,,\, \beta_{N(j)}  \right\rangle + \epsilon_{j}$$

- [[Linear Regression]]

>[!info]
>Note that
>$$\theta_{22}^{-1} = w_{22} + w_{12}^{T}\theta_{12}\theta_{22}^{-1} = w_{22} -  w_{12}^{T}\beta.$$


>[!important]
>Note that the **diagonal term** of $W$ is *fixed* $$W_{j,j} = S_{j,j} + \lambda.$$

## Other Algorithms that Solve Graph LASSO

- [[Augmented Lagrangian Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]
- Oztoprak, F., Nocedal, J., Rennie, S., & Olsen, P. A. (2012). Newton-like methods for sparse inverse covariance estimation. _Advances in neural information processing systems_, _25_.


## Statistical Analysis for Graph Lasso










-----------
##  Recommended Notes and References




- [[Linear Regression]]
- [[Regularized Loss Minimization]]
- [[LASSO and Sparsity-Induced Least Square]]
- [[Conditional Independence]]


- [[Schatten Norm and Nuclear Norm of Matrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

- [[Regularized Loss Minimization]]
- [[Convex Optimization Problem]]

- [[Probabilistic Graphical Models by Koller]] pp 987 - 992
- [[Elements of Statistical Learning by Hastie]] pp 635 - 638
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 265, 253, 353 - 369
- [[High Dimensional Probability An Introduction by Vershynin]]
- Friedman, J., Hastie, T., & Tibshirani, R. (2008). Sparse inverse covariance estimation with the graphical lasso. _Biostatistics_, _9_(3), 432-441.
- Mazumder, R., & Hastie, T. (2012). The graphical lasso: New insights and alternatives. _Electronic journal of statistics_, _6_, 2125.
