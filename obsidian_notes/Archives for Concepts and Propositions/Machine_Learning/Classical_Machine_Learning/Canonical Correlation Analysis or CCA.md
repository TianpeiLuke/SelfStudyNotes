---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/latent_variable_model
  - machine_learning/dimensionality_reduction
  - canonical_correlation_analysis
  - CCA
keywords:
  - dimensionality_reduction
  - canonical_correlation_analysis
topics:
  - probabilistic_graphical_model
  - machine_learning_models
  - machine_learning/dimensionality_reduction
name: Canonical Correlation Analysis
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Canonical Correlation Analysis

### CCA as Twin-Tower Linear Auto-Encoders

>[!important] Definition  
>Let $\{(X_{i}, Y_{i})\}_{i=1}^{n}$ be i.i.d. samples where $X_i \in \mathbb{R}^{d_x}$ and $Y_i \in \mathbb{R}^{d_y}$ drawn from a joint distribution $\mathcal{P}$, and assume *zero mean* for each view:
>$$
>\mathbb{E}[X_i] = 0, \quad \mathbb{E}[Y_i] = 0.
>$$
>
>We would like to find *linear projections* of $X$ and $Y$ into a common latent space of dimension $s \ll \min(d_x, d_y)$ such that the *correlation between projected representations* is maximized.
>
>- Define **linear encoders** $W_x \in \mathbb{R}^{s \times d_x}$ and $W_y \in \mathbb{R}^{s \times d_y}$.
>- The projections are: 
>$$
>z^x_i = W_x X_i, \quad z^y_i = W_y Y_i.
>$$


>[!important] Definition
>The goal of **canonical correlation analysis (CCA)** is to learn $W_x$ and $W_y$ such that the empirical correlation between $z^x_i$ and $z^y_i$ is maximized:
>$$
>\max_{W_x, W_y} \quad \text{corr}(W_x X, W_y Y) = \sum_{i=1}^{s} \text{corr}((W_x X)_i,\; (W_y Y)_i)
>$$
>subject to the constraints:
>$$
>\mathbb{E}[W_x X (W_x X)^\top] = I_s, \quad \mathbb{E}[W_y Y (W_y Y)^\top] = I_s,
>$$
>i.e., the projected features are **uncorrelated and normalized** within each view.
>
>This can be interpreted as a **twin-tower linear autoencoder** where:
>- $W_x$, $W_y$ are encoders for $X$ and $Y$ respectively.
>- The **joint latent code** is encouraged to have **maximal cross-view correlation** rather than low reconstruction loss.

- [[Siamese Network or Twin Tower Network for Contrastive Learning]]
- [[Principal Component Analysis or PCA]]
- [[Multi-View Learning]]

### CCA as Optimization on Generalized Steifel Manifolds

>[!important] Definition  
>We can formulate **canonical correlation analysis (CCA)** as the following *optimization over product of Stiefel manifolds*:
>- Let $X \in \mathbb{R}^{d_x \times n}$ and $Y \in \mathbb{R}^{d_y \times n}$ be centered data matrices (i.e., each column is a sample and $\mathbb{E}[X] = \mathbb{E}[Y] = 0$).
>- Let $\Sigma_{XX} = \frac{1}{n}XX^{T}$, $\Sigma_{YY} = \frac{1}{n}YY^{T}$, and $\Sigma_{XY} = \frac{1}{n}XY^{T}$ be the sample covariance and *cross-covariance* matrices.
>
>This is equivalent to the following optimization over **product of generalized Stiefel manifolds**:
>$$
>\max_{\substack{U \in \text{St}_{\Sigma_{XX}}(d_x, s) \\ V \in \text{St}_{\Sigma_{YY}}(d_y, s)}}\text{Tr}\left(U^{T} \Sigma_{XY} V\right)
>$$
>where the **generalized Stiefel manifold** is defined as:
>$$
>\text{St}_{\Sigma}(d, s) := \left\{W \in \mathbb{R}^{d \times s} \;:\; W^{T} \Sigma W = I \right\}
>$$
>Thus, CCA becomes a *correlation maximization* problem over the product of two generalized Stiefel manifolds corresponding to the two input views.

- [[Stiefel Manifold]]
- [[Linear Subspace]]
- [[Projection Map onto Linear Subspace]]

### CCA as Cross-Covariance Maximization

>[!important] Definition
>Let $X \in \mathbb{R}^{d_x \times n}$ and $Y \in \mathbb{R}^{d_y \times n}$ be centered data matrices (i.e., each column is a sample and $\mathbb{E}[X] = \mathbb{E}[Y] = 0$).
>
>In **CCA**, we seek matrices $U \in \mathbb{R}^{d_x \times s}$ and $V \in \mathbb{R}^{d_y \times s}$ such that the projected views $U^{T}X$ and $V^{T}Y$ are **maximally correlated**:
>$$
>\begin{align}
>\max_{U \in \mathbb{R}^{d_x \times s},\; V \in \mathbb{R}^{d_y \times s}} &\; \text{Tr}\left(U^{T} \Sigma_{XY} V\right) \\
>\text{s.t. } & U^{T} \Sigma_{XX} U = I, \quad V^{T} \Sigma_{YY} V = I
>\end{align}
>$$
>where 
>- $\Sigma_{XX} = \frac{1}{n}XX^{T}$, $\Sigma_{YY} = \frac{1}{n}YY^{T}$ are the *sample covariances*, 
>- and $\Sigma_{XY} = \frac{1}{n}XY^{T}$  is *cross-covariance matrice*.


### Solution of CCA via Solving Generalized Eigenvalue Problem

>[!important] Theorem (Solution of CCA)  
>Let $\{(X_i, Y_i)\}_{i=1}^n$ be i.i.d. samples with zero mean:
>$$
>\mathbb{E}[X_i] = 0, \quad \mathbb{E}[Y_i] = 0,
>$$
>and let $X \in \mathbb{R}^{d_x \times n}$ and $Y \in \mathbb{R}^{d_y \times n}$ be the *centered design matrices* (each column is a sample). Define the following *empirical covariance matrices*:
>$$
>\Sigma_{XX} = \frac{1}{n} X X^{T}, \quad \Sigma_{YY} = \frac{1}{n} Y Y^{T}, \quad \Sigma_{XY} = \frac{1}{n} X Y^{T}
>$$
>
>Then the solution to the **Canonical Correlation Analysis (CCA)** optimization problem:
>$$
>\begin{align}
>\max_{U \in \mathbb{R}^{d_x \times s},\, V \in \mathbb{R}^{d_y \times s}} &\; \text{Tr}(U^{T} \Sigma_{XY} V) \\[5pt]
>\text{s.t. } & U^{T} \Sigma_{XX} U = I, \quad V^{T} \Sigma_{YY} V = I
>\end{align}
>$$
>is obtained by solving the **generalized eigenvalue problem** for the *whitened cross-covariance matrix*:
>$$
>\Sigma_{XX}^{-1/2} \Sigma_{XY} \Sigma_{YY}^{-1} \Sigma_{YX} \Sigma_{XX}^{-1/2}
>$$
>Let the **eigen-decomposition** be given by:
>$$
>\Sigma_{XX}^{-1/2} \Sigma_{XY} \Sigma_{YY}^{-1} \Sigma_{YX} \Sigma_{XX}^{-1/2} = U \Lambda U^{T}
>$$
>where:
>- $\Lambda = \text{diag}(\rho_1^2, \ldots, \rho_s^2)$ contains the **squared canonical correlations**, with $\rho_1 \ge \rho_2 \ge \ldots \ge \rho_s \ge 0$
>- $U \in \mathbb{R}^{d_x \times s}$ is the matrix of **canonical directions** for $X$
>
>Then the optimal CCA projections are:
>$$
>U^{*} = \Sigma_{XX}^{-1/2} U, \quad V^{*} = \Sigma_{YY}^{-1/2} V,
>$$
>where $V$ is obtained analogously as the eigenvectors of the matrix:
>$$
>\Sigma_{YY}^{-1/2} \Sigma_{YX} \Sigma_{XX}^{-1} \Sigma_{XY} \Sigma_{YY}^{-1/2}
>$$
>These projections yield the maximally correlated latent variables:
>$$
>z_i^x = (U^{*})^{T} X_i, \quad z_i^y = (V^{*})^{T} Y_i
>$$
>with correlation coefficients $\rho_1, \ldots, \rho_s$.

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Gaussian Random Vector]]

### Canonical Directions

>[!important] Definition  
>We call the *left and right eigenvectors* $(u_j, v_j)$ corresponding to the *j-th largest canonical correlation* $\rho_j$ the *j-th* **canonical directions** for $X$ and $Y$, respectively.
>
>- Denote:
>  $$
>  Z_X^{j} := u_j^{T} X \in \mathbb{R}^{n}, \quad Z_Y^{j} := v_j^{T} Y \in \mathbb{R}^{n}
>  $$
>  as the *j-th* **canonical variates** (or *canonical components*) of $X$ and $Y$.
>
>- For $j=1$, $u_1$ is the **first canonical direction** of $X$, and $v_1$ is the **first canonical direction** of $Y$. The pair $(Z_X^1, Z_Y^1)$ is the **first pair of canonical components**, capturing the strongest linear correlation between $X$ and $Y$.
>
>- The *first canonical correlation* is defined as the **maximum correlation** achievable by linear projections of $X$ and $Y$:
>  $$
>  \rho_1 = \max_{u,v} \text{Corr}(u^{T} X,\; v^{T} Y)
>  $$
>  subject to:
>  $$
>  \text{Var}(u^{T} X) = 1, \quad \text{Var}(v^{T} Y) = 1
>  $$
>
>- Each subsequent pair $(u_j, v_j)$ is orthogonal to the previous ones (in the whitened space), and captures the next highest remaining correlation.



## Explanation

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

## CCA as Special Case of Partial Least Square

- [[Partial Least Square]]




-----------
##  Recommended Notes and References



- [[Probabilistic Principal Component Analysis]]
- [[Gaussian Random Vector]]

- [[Factor Analysis]]
- [[Latent Variable Models]]
- [[Partial Correlation]]
- [[Independent Component Analysis or ICA]]

- [[Representation Learning]]

- [[Curse of Dimensionality]]
- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]
- [[Kullback-Leibler Divergence]]

- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 945 - 946, 1043 - 1046
- [[Deep Learning Foundations and Concepts by Bishop]] pp 501
- [[hardoonCanonicalCorrelationAnalysis2004a]] Hardoon, D. R., Szedmak, S., & Shawe-Taylor, J. (2004). Canonical correlation analysis: An overview with application to learning methods. _Neural computation_, _16_(12), 2639-2664.

