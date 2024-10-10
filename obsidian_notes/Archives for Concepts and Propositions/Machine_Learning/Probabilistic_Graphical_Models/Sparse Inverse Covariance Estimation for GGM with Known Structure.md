---
tags:
  - concept
  - machine_learning/models
  - statistics/estimation
  - statistics/inference
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/inference
  - probabilistic_graphical_models/algorithm
keywords:
  - inverse_covariance_estimation
  - precision_matrix
  - multivariate_gaussian_distribution
  - graph_lasso
  - sparsity
topics:
  - machine_learning_models
  - probabilistic_graphical_model
  - statistics/inference
  - statistics/estimation
name: Sparse Inverse Covariance Estimation with Known Structure
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sparse Inverse Covariance Estimation with Known Structure

![[Gaussian Random Vector#^a97326]]

- [[Gaussian Random Vector]]

![[Inverse Covariance Estimation#^d75d16]]

![[Gaussian Graphical Model#^44a106]]

>[!important] Definition
>Let $X_{i}\sim \mathcal{N}(0, \Theta^{-1})$ where $\Theta \succ 0$ is the *precision matrix*.
>
>The **sparse inverse covariance estimation** with *known dependency graph structure* $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ solves the following *convex optimization problem* 
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(S\,\Theta\right) - \frac{1}{2}\log \det \Theta \\[5pt]
> \text{s.t. }\;&\;\Theta_{i,j} = 0\, \quad (i,j) \not\in \mathcal{E}
>\end{align*}
>$$
>where sample covariance matrix $$S = \frac{1}{n}X^{T}X$$ with $X\in \mathbb{R}^{n\times d}$ and rows $X_{i}$

- [[Inverse Covariance Estimation]]
- [[Gaussian Graphical Model]]


### Optimal Condition for Sparse Inverse Covariance Estimation

>[!important]
>The **Lagranigan** for above problem is defined as
>$$
>L(\Theta, \Gamma) := \text{tr}\left(S\,\Theta\right) - \log \det \Theta + \sum_{(i,j)\not\in \mathcal{E}}\gamma_{i,j}\,\theta_{i,j} 
>$$
>where 
>- $\Theta = [\theta_{i,j}]$ and $S = \frac{1}{n} X^{T}X$ and 
>- $\Gamma = [\gamma_{i,j}]$ with $\gamma_{i,j} \neq 0, \forall (i,j)\not\in \mathcal{E}.$
>  
>  
>Note that   $$\nabla_{\Theta} \log \det(\Theta) = \Theta^{-1}.$$ So one of necessary conditions for the optimal solution is that the **gradient** with respect to $\Theta$ is $$\nabla_{\Theta} L = S -\Theta^{-1} + \Gamma = 0, \quad (1)$$ 

^823ac6

- [[Methods of Lagrangian Multipliers]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

### Algorithm for Sparse Inverse Covariance Estimation

![[Schur Complement and Inversion of Block Matrix#^eb8bd3]]

![[Schur Complement and Inversion of Block Matrix#^0d76ad]]


>[!info]
>Define the *inverse* of $\Theta$ as $W$, i.e. $$W = \Theta^{-1}.$$
>Partitioning $\Theta$ into four *blocks* along the last row and last columns, we have 
>$$
>\Theta := \left[ \begin{array}{cc}
> \Theta_{11} & \theta_{12} \\[5pt] 
>  \theta_{12}^{T} & \theta_{22}
>\end{array} \right] 
>$$
>Similarly, we can partition the inverse of $\Theta$, $W$, as 
>$$
>\begin{align*}
>\Theta^{-1} := \left[ \begin{array}{cc}
> \Theta_{11} & \theta_{12} \\[5pt] 
>  \theta_{12}^{T} & \theta_{22}
>\end{array} \right]^{-1} :=  
>\left[ \begin{array}{cc}
> W_{11} & w_{12} \\[5pt] 
>  w_{12}^{T} & w_{22}
>\end{array} \right] := W
>\end{align*}
>$$

^f40ca8

>[!info]
>According to the **inversion formula** for **block matrix**, we can find the equations for each blocks of $W$ as
>$$
>\begin{align*}
> \Theta_{11} &= (W / w_{22})^{-1} \\[5pt]
> \theta_{12} &= -(W / w_{22})^{-1}w_{12}w_{22}^{-1}\\[5pt]
> \theta_{22} &= w_{22}^{-1} + w_{22}^{-1}w_{12}^{T}(W / w_{22})^{-1} w_{12}w_{22}^{-1}
>\end{align*}
>$$
>where $$(W / w_{22}):= W_{11} - w_{12}w_{22}^{-1}w_{12}^{T}$$ is the **Schur complement** of $w_{22}$ in $W$.

^cf8a74

>[!info]
>Similarly, we have 
>$$
>\begin{align*}
>W_{11} &= (\Theta / \theta_{22})^{-1} \\[5pt]
>w_{12} &= - (\Theta / \theta_{22})^{-1}\theta_{12}\theta_{22}^{-1} = - W_{11}\theta_{12}\theta_{22}^{-1} \\[5pt]
>w_{22}&= \theta_{22}^{-1} + \theta_{22}^{-1}\theta_{12}^{T}(\Theta / \theta_{22})^{-1} \theta_{12}\theta_{22}^{-1} = \theta_{22}^{-1} - w_{12}^{T}\theta_{12}\theta_{22}^{-1} \\[5pt]
> \implies \theta_{22}^{-1}& = w_{22} + w_{12}^{T}\theta_{12}\theta_{22}^{-1} 
>\end{align*}
>$$

^a124e2

- [[Schur Complement and Inversion of Block Matrix]]
- [[Partition of Matrix and Block Matrix]]

>[!info]
>Substitute $W = \Theta^{-1}$ into the equation $(1)$ so that
>$$
> S - W + \Gamma = 0
>$$
>Therefore, considering the top right block of $W$
>$$
>\begin{align*}
>s_{12} - w_{12} + \gamma_{12} &= 0 \\[5pt]
> \implies s_{12} + W_{11}\theta_{12}\theta_{22}^{-1} + \gamma_{12} &=0 \\[5pt]
>  \implies W_{11}\beta &= s_{12} + \gamma_{12}
>\end{align*}
>$$
>where $\beta := -\theta_{12}\theta_{22}^{-1}.$
>Note that
>$$\theta_{22}^{-1} = w_{22} + w_{12}^{T}\theta_{12}\theta_{22}^{-1} = w_{22} -  w_{12}^{T}\beta.$$

>[!quote]
>These can be interpreted as the $p − 1$ *estimating equations* for the **constrained regression** of $X_p$ on the **other predictors**, except that the observed mean cross-products matrix $S_{11}$ is replaced by $W_{11}$, the *current estimated covariance matrix* from the model.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 633

>[!info]
>$$ W_{11}\beta = s_{12} + \gamma_{12}$$ can be considered as a **linear regression problem** on the subset $(i,e)\not\in \mathcal{E}$ where $e$ corresponds to the last column of $\Theta$.
>- Note that $\gamma_{i,2} =0$ for all $i\in N(j)$, thus $$W_{11}^{*}\beta^{*} = s_{12}^{*} \implies \beta^{*} = (W_{11}^{*})^{-1}s_{12}^{*}$$ where $$W_{11}^{*}\in \mathbb{R}^{q\times q}, \; s_{12}^{*} \in \mathbb{R}^{q},\, \beta^{*}\in \mathbb{R}^{q}$$ are reduced matrix, vectors whose *coordinates* corresponding to node $i$ in the *neighborhood* of $e$. Assume that $$q:= |i: (i,e)\in \mathcal{E}|,$$ so there are $q$ zeros in $\gamma_{12}.$
>- The rest $p-q$ entries in $\beta$ is set to be **zero** as $\gamma_{i,2} = -s_{i,2}$.

- [[Linear Regression]]

>[!important] Definition
>Let $X\sim \mathcal{N}(0, \Theta^{-1})$ follow a *Gaussian graphical model* on $\mathcal{G} =(\mathcal{V}, \mathcal{E})$ where $\mathcal{G}$ is known. 
>
>Consider the problem of *parameter estimation* which solves the following problem
>$$
>\begin{align*}
> \min_{\Theta \in \mathbb{R}^{d\times d}} \;&\; \frac{1}{2}\text{tr}\left(S\,\Theta\right) - \frac{1}{2}\log \det \Theta \\[5pt]
> \text{s.t. }\;&\;\Theta_{i,j} = 0\, \quad (i,j) \not\in \mathcal{E}
>\end{align*}
>$$
>where the sample covariance matrix $$S = \frac{1}{n}X^{T}X$$ with $X\in \mathbb{R}^{n\times d}$ and rows $X_{i}$
>
>The **parameter estimation algorithm** for **Gaussian graphical model** that solves above problem is as follow:
>- *Require*: The dependency graph with edge set $\mathcal{E}$
>- *Require*: The *sample covariance matrix* $$S := \frac{1}{n}X^{T}X$$ where rows $X_{i}\sim \mathcal{N}(0, \Theta)$
>- Initialize $$W \leftarrow S$$ where the **diagonal terms** remain unchanged in following steps.
>- Loop until convergence:
>	- For $j=1\,{,}\ldots{,}\,d$: 
>		- **Partition** matrix $W$ along the $j$-th row and $j$-th column: $$\left[ \begin{array}{cc} W_{[-j], [-j]} & W_{[-j],j} \\[5pt] W_{[-j],j}^{T} & W_{j,j}\end{array} \right] := W$$ where 
>			- $W_{jj}\in \mathbb{R}$ and 
>			- $W_{[-j],j}\in \mathbb{R}^{d-1}$ and 
>			- $W_{[-j], [-j]} \in \mathbb{R}^{(d-1) \times (d-1)}$ are the *principal submatrix* excluding $j$-th column and row.
>		- Also **partition** sample covariance matrix $S$ accordingly.
>		- Collect the **adjacency list** of nodes that **connect** to $j$-th node (except for itself). $$N(j) := \left\{ i\in \mathcal{V} \setminus\, \left\{ j \right\}: (i,j)\in \mathcal{E} \right\}$$
>		- Set $s_{12}^{*}$ as a *subset of* $s_{12}$ whose row $i\in N(j).$ $$s_{12}^{*} = [S_{i,j}, \quad i\in N(j)]$$
>		- **Solve the normal equation** $$W_{N(j), N(j)}\;\beta_{N(j)} = S_{N(j), j}$$ where $W_{N(j), N(j)}$ is the principal submatrix whose rows and columns in $N(j)$
>		- Let $\beta_{j} = [\beta_{1}^{(j)}\,{,}\ldots{,}\,\beta_{d-1}^{(j)}] \in \mathbb{R}^{d-1}$ where $$\beta_{i}^{(j)} = \left\{\begin{array}{cl}\beta_{i}^{*} & \text{ if }i\in N(j)\\[5pt] 0 & \text{otherwise}\end{array}\right.$$
>		- **Update** off-diagonal terms in $j$-th column of $W$ via *linear regression* $$W_{[-j],j} \leftarrow W_{[-j], [-j]}\,\beta_{j}$$
>		- If current loop is the *final loop*, compute $\Theta$
>			- Update **diagonal term** in $j$-th column $$\Theta_{j,j} = (S_{j,j} - W_{[-j],j}^{T}\;\beta_{j})^{-1}$$
>			- Update **off-diagonal term** in $j$-th column $$\Theta_{[-j],j} = - \beta_{j}\,\Theta_{j,j} $$

^eead22

- [[Normal Equations and Newton System of Equations]]
- [[Principal Submatrix]]
## Explanation

>[!info]
>In the above process, in each iteration, the algorithm *updates the estimate* of the **parameters** of **GGM**  associated with the **nearest-neighborhood** of each node.
>
>The update is based on **neighborhood regression** model
>$$
>X^{(j)} = \left\langle X^{N(j)} , \beta_{N(j)} \right\rangle + \epsilon_{j}
>$$
>where each node value is *linearly dependent* on its **neighborhood**'s value.

>[!info]
>At each iteration, it solves the **normal equation**
>$$
>W_{N(j), N(j)}\; \beta_{N(j)} = S_{N(j), j}
>$$
>where 
>$$
>W_{N(j), N(j)} \approx (X^{[N(j)]})^{T} X^{[N(j)]}, \quad S_{N(j), j} = (X^{[N(j)]})^{T}X_{j}
>$$

- [[Normal Equations and Newton System of Equations]]


## Gaussian Belief Propagation

>[!info]
 **Gaussian Belief Propagation** can also estimate $\theta_{i,j}$

- [[Gaussian Belief Propagation]]



## Sparse Inverse Covariance Estimation without Known Structure

- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]




-----------
##  Recommended Notes and References


- [[Convex Function]]
- [[Convex Set]]
- [[Convex Optimization Problem]]
- [[Canonical Form of Gaussian Graphical Model]]


- [[Least Square Estimation]]
- [[Algorithms for Least Square Estimation Problem]]
- [[LASSO and Sparsity-Induced Least Square]]

- [[Positive Semidefinite Transformation]]
- [[Trace of Matrix]]
- [[Determinant of Linear Transformation]]


- [[Elements of Statistical Learning by Hastie]] pp 631 - 634
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 25, 38, 
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 265
- [[High Dimensional Probability An Introduction by Vershynin]] pp 100, 130, 237
- [[Convex Optimization by Boyd]] pp 355 - 357


- [[Gaussian Process]]
- [[Gaussian Measure]]
- [[Gaussian Random Function]]


- [[Convex Optimization Problem]]