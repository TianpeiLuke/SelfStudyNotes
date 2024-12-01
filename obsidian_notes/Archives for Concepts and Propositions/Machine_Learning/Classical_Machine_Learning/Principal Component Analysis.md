---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/latent_variable_model
  - machine_learning/dimensionality_reduction
keywords:
  - principal_component_analysis
  - dimensionality_reduction
topics:
  - probabilistic_graphical_model
  - machine_learning_models
  - dimensionality_reduction
name: Principal Component Analysis
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Principal Component Analysis

### PCA as Linear Auto-Encoder

>[!important] Definition
>Let $X_{i} \in \mathbb{R}^{d},\, i=1\,{,}\ldots{,}\,n$ be i.i.d. samples from distribution $\mathcal{P}$ with *zero mean* $$ \mathbb{E}_{  }\left[ X_{i} \right] = 0.$$
>
>We would like to *reduce the dimensionality* of these vectors using *linear transformation*. 
>- In particular, let $W\in \mathbb{R}^{s \times d}$ be a matrix with $s < d$. The linear map $$x \mapsto Wx$$ defined a **linear encoder** where $W$ is called a **compression / encoding matrix**.
>- We also define a linear map $$z \mapsto Uz$$ as the corresponding **linear decoder** where $U \in \mathbb{R}^{d \times s}$ is called a **recovering / decoding matrix.**
>  
>The goal of **principle component analysis (PCA)** is to find $W\in \mathbb{R}^{s \times d}$  and $U \in \mathbb{R}^{d \times s}$ so that the *reconstruction error* (i.e. *mean squared error*) between original and recovered vectors is minimal:
>$$
>\min_{W\in \mathbb{R}^{s \times d}, U \in \mathbb{R}^{d \times s}}\sum_{i=1}^{n}\lVert X_{i} - U\,W\,X_{i} \rVert_{2}^2 
>$$

^4f6696

- [[Auto-Encoder and Stochastic Auto-Encoder]]

>[!important] Proposition
>Let $(U,W)$ be the **optimal solution** for 
>$$
>\min_{W\in \mathbb{R}^{s \times d}, U \in \mathbb{R}^{d \times s}}\sum_{i=1}^{n}\lVert X_{i} - U\,W\,X_{i} \rVert_{2}^2 
>$$
>
>Then the columns $u_{i}$ of  $U = [u_{i}]$ are **orthonormal** i.e. $$U^{T}U = I_{s}$$ and $$W = U^{T}.$$

^b1e550

- [[Understanding Machine Learning by Shalev-Shwartz]] pp 279

### PCA as Optimization on Manifold

>[!important] Definition
>We can reformulate the **principle component analysis (PCA)** as the following *subspace optimization problem*
>$$
>\begin{align}
>\min_{U \in \mathbb{R}^{d \times s}}& \sum_{i=1}^{n}\lVert X_{i} - U\,U^{T}\,X_{i} \rVert_{2}^2 \\
>\text{s.t. }& U^{T}\,U = I
>\end{align}
>$$
>or equivalently
>$$
>\min_{U \in \text{St}(d, s) }\sum_{i=1}^{n}\lVert X_{i} - P_{\mathcal{R}(U)}\,X_{i} \rVert_{2}^2 
>$$
>where $$\text{St}(d, s)  := \left\{U \in \mathbb{R}^{d \times s}: U^{T}\,U = I  \right\}$$ is called the **Stiefel manifold**  and $P_{\mathcal{R}(U)} = U\,U^{T}$ is the *orthogonal projection* on *range (column space)* of $U$, $\mathcal{R}(U)$.

^028c45

- [[Stiefel Manifold]]
- [[Linear Subspace]]
- [[Projection Map onto Linear Subspace]]
- [[Fundamental Subspaces from Linear Map]]
- [[Orthogonal Group]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 9 - 10

### PCA via Iterative Variance Maximization

>[!important] Definition
>Let $X_{i} \in \mathbb{R}^{d},\, i=1\,{,}\ldots{,}\,n$ be i.i.d. samples from distribution $\mathcal{P}$ with *zero mean* $$ \mathbb{E}_{  }\left[ X_{i} \right] = 0.$$
>
>Using the *orthogonality constraint*, the objective of the *subspace optimization problem* can be decomposed into two parts
>$$
>\sum_{i=1}^{n} \lVert X_{i} - U\,U^{T}\,X_{i} \rVert_{2}^2 = \sum_{i=1}^{n} \lVert X_{i} \rVert_{2}^2 - \sum_{i=1}^{n}\text{tr}\left( U^{T}X_{i}\,X_{i}^{T}U \right) 
>$$ 
>Thus we can reformulate the **principle component analysis (PCA)** as the following optimization problem
>$$
>\begin{align}
>\max_{U \in \mathbb{R}^{d \times s}}& \frac{1}{n} \text{tr}\left[ U^{T} \left(  \sum_{i=1}^{n} X_{i}\,X_{i}^{T}\right) U \right]  \\[10pt]
>\text{s.t. }& U^{T}\,U = I
>\end{align}
>$$
>
>- Let $$V_{i} = U^{T}\,X_{i} \in \mathbb{R}^{s}$$ be linear projection (*encoded representation*) of a samples $X_{i}$. Then  $\mathbb{E}_{  }\left[ V_i \right] = 0$ and are i.i.d.
>- Then the **objective function of PCA** can be formulated as $$\frac{1}{n}\sum_{i=1}^{n}\sum_{j=1}^{s} (V_{i}^{j})^2 = \sum_{j=1}^{s}\text{Var}(V^{j}).$$ 
>- *PCA* aims at finding a set of $s$ **linear projection direction** $$U := [u_{1} \,{,}\ldots{,}\,u_{s}]$$ such that the **variance** of projected samples is *maximized* 
>$$
>\begin{align}
>\max_{u_{1} \,{,}\ldots{,}\,u_{s}}& \sum_{j=1}^{s}\text{Var}(V^{j}) = \sum_{j=1}^{s} \mathbb{E}\left[  \left\langle u_{j} ,  X\right\rangle^2 \right] =  \sum_{j=1}^{s} \left\langle u_{j} ,  \Sigma u_{j}\right\rangle \\[10pt]
>\text{s.t. }&u_{i}^{T}\,u_{j} = \delta_{i,j}, \quad i,j = 1\,{,}\ldots{,}\,s 
>\end{align}
>$$

^feea32



>[!important] Definition
>Formally, the **principle component analysis** is described by the following *iterative optimization algorithm*
>- For $j=1\,{,}\ldots{,}\,s <d$:
>	- the *j*-th **principle component direction** $u_{j}$ of $X$ is the solution of the following **variance maximization problem** $$\begin{align*}u_{j} = \arg\max_{u \in \mathbb{S}^{d-1}}&\; \mathbb{E}\left[  \left\langle u , X \right\rangle^2  \right] := \left\langle u ,\Sigma\,u  \right\rangle \\[10pt]\text{s.t. }& \left\langle u_{i} , u \right\rangle = 0, \quad i=1\,{,}\ldots{,}\,j-1\end{align*}$$

^d06ebc

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]

>[!info]
>We can see a similar formulation in [[Iterative Maximum Entropy Learning for AdaBoost]]


### Solution of PCA from Spectral Theorem

>[!important] Theorem (Solution of PCA)
>Let $X_{i} \in \mathbb{R}^{d},\, i=1\,{,}\ldots{,}\,n$ be i.i.d. samples from distribution $\mathcal{P}$ with *zero mean* $$ \mathbb{E}_{  }\left[ X_{i} \right] = 0.$$ Denote the *sample covariance matrix* of $X$ as
>$$
>S = \frac{1}{n} X^{T}\,X = \frac{1}{n} \sum_{i=1}^{n} X_{i}\,X_{i}^{T}
>$$
>where the *design matrix* is defined as 
>$$
>X = \left[ \begin{array}{c}X_{1}^{T} \\ X_{2}^{T} \\ \ldots \\ X_{n}^{T} \end{array} \right] =   \left[ \begin{array}{cccc}X_{1}^{1} & X_{1}^{2} & \ldots & X_{1}^{d} \\ X_{2}^{T} & X_{2}^{2} & \ldots & X_{2}^{d} \\ \ldots &  \ldots &  \ldots &  \ldots \\ X_{n}^{T} & X_{n}^{2} & \ldots & X_{n}^{d} \end{array} \right] \in \mathbb{R}^{n\times d}
>$$
>
>Suppose that the **eigen-decomposition** of $S$ is given by $$S = U\,\Lambda\,U^{T}$$ where
>- $$\Lambda = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{d}), \quad \text{ where }  \lambda_{1} \ge \lambda_{2} \,{\ge}\ldots{\ge}\,\lambda_{d} \ge 0$$ be *eigenvalues* of $S$
>- $$U = [u_{1} \,{,}\ldots{,}\,u_{d}] \in \mathcal{O}(d)$$ is the orthogonal matrix, whose columns $u_{i}$ are *eigenvectors* of $S$ corresponding to eigenvalue $\lambda_{i}$ 
>
>
>Then the optimal solution to the **principle component analysis problem**
>$$
>\begin{align}
>\max_{U \in \mathbb{R}^{d \times s}}&  \text{tr}\left[ U^{T} S  U \right] := \left\langle S \,,\, U U^{T} \right\rangle_{tr} \\[10pt]
>\text{s.t. }& U^{T}\,U = I
>\end{align}
>$$
>is the set $$U^{*} = \left[ u_{1} \,{,}\ldots{,}\, u_{s}\right] $$ whose columns are **eigenvectors** of $S$ corresponding to **top $s$ largest eignvalues**.

^ab6364


>[!important] Definition
>We call the *eigenvector* $u_{j}$ corresponding to the  *j-th largest eigenvalue*  of $S$ as the *j-th* **principle component directions** of $X$. 
>
>- Denote $$V^{j} := X\,u_{j} \in \mathbb{R}^{n}$$ as the  *j-th* **principle component** of $X$. 
>- For $j=1$, we call $u_{1}$ is the **first principle component direction** of $X$ and $V^{1}$ the **first principle component** of $X$  
>
>- The *eigenvalues* corresponds to the *$1$-st principle component direction* has the **maximum variance**  $$\lambda_{1} = \text{Var}(Xu_{1}) = \max_{u} \text{Var}(Xu)$$


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Gaussian Random Vector]]

### PCA as Low-Rank Approximation


>[!important] Definition
>The problem of **principle component analysis** can also be formulated as a **low-rank approximation problem**
>$$
>\min_{\text{rank}(B) = s}\lVert S - B \rVert_{2}^2
>$$
>where $\lVert \cdot \rVert_{2}$ is the *$L_{2}$ operator norm* for linear operator,  and  $S$ is the *sample covariance matrix*
>$$
>S = \frac{1}{n} X^{T}\,X = \frac{1}{n} \sum_{i=1}^{n} X_{i}\,X_{i}^{T}
>$$

- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]
- [[Singular Value Decomposition of Linear Map]]
- [[Operator p-Norm of Matrix]]


### PCA as Hard Spectral Filtering

- [[Spectral Theorem in Functional Calculus Form]]


### Kernel PCA

- [[Kernel Principal Component Analysis]]


## Explanation


>[!info]
>PCA algorithm is the basis for **dimensionality reduction** via linear projection.


>[!info]
>**PCA** can be formulated according to many perspectives: 
>- **Linear Auto-Encoder** or **Linear Dimensionality Reduction**: 
>	- PCA consists of two parts: a *linear encoder* and a *linear decoder*. 
>	- The algorithm learns both encoding and decoding mapping by minimizing the **reconstruction error** $$\min_{W\in \mathbb{R}^{s \times d},\, U \in \mathbb{R}^{d \times s}}\sum_{i=1}^{n}\lVert X_{i} - U\,W\,X_{i} \rVert_{2}^2$$
>	- The solution has $W = U^{T}$.
>- **Subspace Tracking / Optimization on Manifold** 
>	- PCA find a set of $s$ *orthonormal vectors* $U := [u_{1}\,{,}\ldots{,}\,u_{s}]$ in $\mathbb{R}^{d}$ so that the projection on $\mathcal{R}_{U}$ *preserves* as much *energy* as possible $$\begin{align}\min_{U \in \mathbb{R}^{d \times s}}& \sum_{i=1}^{n}\lVert X_{i} - U\,U^{T}\,X_{i} \rVert_{2}^2 \\\text{s.t. }& U^{T}\,U = I\end{align}$$
>	- It can be formulated as **optimization on manifold** $$\begin{align}\min_{U}& \sum_{i=1}^{n}\lVert X_{i} - P_{\mathcal{R}(U)}\,X_{i} \rVert_{2}^2 \\ \text{s.t. }& U \in St(d, s) \end{align}$$
>	- $St(d,s)$ is the **Stiefel manifold** $$St(d, s)  := \left\{U \in \mathbb{R}^{d \times s}: U^{T}\,U = I  \right\}.$$
>	- Note that principle components (i.e. eigenvalues) are *invariant under orthogonal transformation* on data $X$
>- **(Iterative) Variance Maximization**: 
>	- PCA finding the $s$ *orthonormal directions* that *maximizes* the total *variance* of projected components
>	- In other word, it finds *orthonormal directions* so that the projections on these directions **preserve most of the variance**
>	- $$\begin{align}\max_{u_{1} \,{,}\ldots{,}\,u_{s} \in \mathcal{S}^{d-1}}&  \sum_{j=1}^{s} \mathbb{E}\left[  \left\langle u_{j} ,  X\right\rangle^2 \right] =  \sum_{j=1}^{s} \left\langle u_{j} ,  \Sigma u_{j}\right\rangle \\[10pt]\text{s.t. }&u_{i}^{T}\,u_{j} = \delta_{i,j}, \quad i,j = 1\,{,}\ldots{,}\,s \end{align}$$
>	- We can approximate the mean and covariance $\Sigma$ using sample mean and sample covariance $S$
>	- The algorithm can find the principle component directions *iteractively*
>	- For $j=1\,{,}\ldots{,}\,s <d$:
>		- Solve the optimization problem $$\begin{align*}u_{j} = \arg\max_{u \in \mathbb{S}^{d-1}}&\; \mathbb{E}\left[  \left\langle u , X \right\rangle^2  \right] := \left\langle u ,\Sigma\,u  \right\rangle \\[10pt]\text{s.t. }& \left\langle u_{i} , u \right\rangle = 0, \quad i=1\,{,}\ldots{,}\,j-1\end{align*}$$
>- **Low Rank Approximation**:
>	- PCA can be seen as approximating the sample covariance matrix with a rank-$s$ matrix  $$\min_{\text{rank}(B) = s}\lVert S - B \rVert_{2}^2$$
>	- The optimal solution is the **eigen-decomposition** with **top $s$ eigenvalues** $$B = U\Lambda_{\lceil s \rceil}U^{T}$$
>	- The $s$ **principle components** are $$\Lambda_{\lceil s \rceil} = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{s}), \quad \text{ where }  \lambda_{1} \ge \lambda_{2} \,{\ge}\ldots{\ge}\,\lambda_{s} \ge 0$$
>	- The $s$ **principle component directions** as eigenvectors corresponding to top $s$ eigenvalues
>- **Spectral Filtering**
>	- The solution of PCA can be seen as the **spectral filtering** of sample covariance $S$
>	- $$f(S) = U f\left(\Lambda\right) U^{T}$$ where $$f(\lambda) = \left\{\begin{array}{ll} \lambda & \text{ if } \lambda \ge \lambda_{cutoff} \\ 0 & \text{ otherwise }   \end{array} \right.$$
>- **Probabilistic Principle Component Analysis**
>	- Probabilistic PCA can be seen as the maximum likelihood estimation for the **latent variable model** where both prior of latent factors and likelihood are *Gaussian*. $$\left\{\begin{align*} p(h) &= \mathcal{N}(h \;|\; 0\,;\, I)\\[5pt] p(x|h) &=\mathcal{N}(x\;|\; Vh\,;\,  \sigma^2I)\end{align*}\right.$$ where $V$ has *orthogonal columns*.
>	- We assume the observations have zero mean (centered).
>	- The marginal distribution on observations is $$p(x) = \mathcal{N}(x\;|\;0 \,;\, VV^{T} + \sigma^2I)$$
>	- taking limit of $\sigma\to 0$, we can recover PCA as the **noise-free limit**.



## Probabilistic Principle Component Analysis

- [[Factor Analysis]]
- [[Probabilistic Principle Component Analysis]]


## Random Matrix Theory

- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]



## Other Dimensionality Reduction Method

- [[Independent Component Analysis]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Nonnegative Matrix Factorization]]
- [[Canonical Correlation Analysis]]



-----------
##  Recommended Notes and References


- [[Probabilistic Principle Component Analysis]]
- [[Gaussian Random Vector]]
- [[Factor Analysis]]
- [[Latent Variable Models]]
- [[Canonical Correlation Analysis]]
- [[Quadratic Programming]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Singular Value Decomposition of Linear Map]]


- [[Curse of Dimensionality]]
- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]


- [[Elements of Statistical Learning by Hastie]] pp 66 - 80, 534 - 347
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 936
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] pp 236 - 258
- [[High Dimensional Probability An Introduction by Vershynin]] pp 46, 99, 102
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 279
- [[Foundations of Machine Learning by Mohri]] pp 347–351, 356–358
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 6, 8 - 11
- [[Deep Learning Foundations and Concepts by Bishop]] pp 497 - 505, 506, 565