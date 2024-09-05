---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/dimensionality_reduction
  - machine_learning/latent_variable_model
keywords:
  - principle_component_analysis
  - probabilistic_principle_component_analysis
topics:
  - dimensionality_reduction
  - machine_learning_models
  - unsupervised_models
name: Probabilistic Principle Component Analysis
date of note: 2024-09-04
---

## Concept Definition

>[!important]
>**Name**: Probabilistic Principle Component Analysis

>[!important] Definition
>The **probabilistic principle component analysis (PPCA)** considers the following *factor analysis* model
>$$
>\left\{
>\begin{align*} p(h) &= \mathcal{N}(h \;|\; 0\,;\, I)\\[5pt] p(x|h) &=\mathcal{N}(x\;|\; Vh\,;\,  \sigma^2I)
>\end{align*}
>\right.
>$$ 
>where
>- $h\in \mathbb{R}^{s}$ are *latent variables*, and $x\in \mathbb{R}^{d}$ are *observations*.
>- the **factor loading matrix** $V = [v_{1} \,{,}\ldots{,}\,v_{s}]\in \mathbb{R}^{d\times s}$ has *orthogonal columns*, i.e. $$\left\langle v_{i} , v_{j} \right\rangle =0, \quad i\neq j$$
>
>The *marginal distribution* of observation (i.e. **evidence**) is given by 
>$$
>p(x) = \mathcal{N}(x\;|\;0 \,;\, VV^{T} + \sigma^2I)
>$$

^098ba1

- [[Principle Component Analysis]]
- [[Factor Analysis]]

### Maximum Likelihood Estimation for PPCA

>[!important] Definition
>The **log-likelihood function** for PPCA is given by
>$$
>\begin{align*}
>&\log p(x; V, \sigma) \\[5pt]
>&= -\frac{nd}{2}\log(2\pi) - \frac{n}{2}\log\det\,\lvert VV^{T} + \sigma^2I \rvert  - \frac{1}{2}\sum_{i=1}^{n}\left\langle x_{i} , \left(  VV^{T} + \sigma^2I  \right)^{-1} x_{i} \right\rangle \\[5pt]
>&= - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert VV^{T} + \sigma^2I \rvert + \left\langle \left(  VV^{T} + \sigma^2I  \right)^{-1} ,  S\right\rangle_{tr} \right] 
>\end{align*}
>$$
>where the sample covariance matrix is
>$$
>S = \frac{1}{n}\sum_{i=1}^{n}x_{i}\,x_{i}^{T}
>$$

^a7df83

- [[Maximum Likelihood Estimation]]
- [[Gaussian Random Vector]]

>[!important] Proposition
>Let 
>$$
>S = U\,\Lambda\,U^{T}
>$$
>be the *eigen-decomposition* of sample covariance $S$ 
>- $$\Lambda = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{d}), \quad \text{ where }  \lambda_{1} \ge \lambda_{2} \,{\ge}\ldots{\ge}\,\lambda_{d} \ge 0$$ be *eigenvalues* of $S$
>- $$U = [u_{1} \,{,}\ldots{,}\,u_{d}] \in \mathcal{O}(d)$$ is the orthogonal matrix, whose columns $u_{i}$ are *eigenvectors* of $S$ corresponding to eigenvalue $\lambda_{i}$ 
>
>Then the **maximum likelihood estimation** of $V$ for **PPCA** has *singular value decomposition*
>$$
>\widehat{V}_{mle} = U_{\lceil s \rceil}\left( K_{s} - \sigma^2 I\right)^{1/2} Q^{T}
>$$
>where 
>- $\Lambda_{ \lceil s \rceil }$ and  $U_{\lceil s \rceil}$ denote the top $s$ largest eigenvalues and their eigenvectors $$U_{\lceil s \rceil} = [u_{1} \,{,}\ldots{,}\,u_{s}], \quad \Lambda_{ \lceil s \rceil } = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{s})$$
>- $K_{s} = \text{diag}\left(k_{1} \,{,}\ldots{,}\,k_{s}\right)$ where $$k_{j} = \left\{\begin{array}{ll}\lambda_{j} & \text{ if } \lambda_{j} \ge \sigma^2 \\[5pt] \sigma^2 & \text{ otherwise }\end{array}\right.$$ For $j$ such that $\lambda_{j} < \sigma^2$, the corresponding $u_{j}$ is *arbitrary*.
>- $Q\in \mathcal{O}(s)$ is an *arbitrary orthogonal matrix* . 
>  
>Moreover, the MLE for **observation variance**  is given by 
>$$
>\sigma_{mle}^2 = \frac{1}{d - s}\sum_{i=s+1}^{d}\lambda_{i}
>$$

#### Proof


>[!info]
>The **necessary condition** for the MLE of $V$ leads to the score equation
>$$
>\begin{align*}
> \nabla_{V} \log p(x; V,\sigma) &= 0 \\[5pt]
> \nabla_{V} \log\det\,\lvert VV^{T} + \sigma^2I \rvert + \nabla_{V}\left\langle \left(  VV^{T} + \sigma^2I  \right)^{-1} ,  S\right\rangle_{tr}   &= 0 \\[5pt]
>\end{align*}
>$$

>[!info]
>By **matrix inversion formula**
>$$
>\begin{align*}
>\frac{1}{\sigma^2} \left( I + \frac{1}{\sigma^2} V\,V^{T} \right)^{-1} &= \frac{1}{\sigma^2}\left(  I - \frac{1}{\sigma^2}V\,\left(I + \frac{1}{\sigma^2}V^{T}V\right)^{-1}\,V^{T} \right) \\[5pt]
>&= \frac{1}{\sigma^2}\left(  I - V\,\text{diag}\left( \frac{1}{\sigma^2+ \lVert v_{1} \rVert^2 } \,{,}\ldots{,}\, \frac{1}{\sigma^2+ \lVert v_{n} \rVert^2 }\right)\,V^{T} \right)
>\end{align*}
>$$

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

>[!info]
>The formula for matrix derivative
>$$
>\nabla_{X} \log \det X = (X^{-1})^{T} = (X^{T})^{-1}
>$$
>So by chain rule,
>$$
>\begin{align*}
>&\nabla_{V} \log\det\,\lvert VV^{T} + \sigma^2I \rvert \\[5pt]
>&= 2\left(VV^{T} + \sigma^2I\right)^{-1}V := 2 C^{-1}\,V
>\end{align*}
>$$
>where $$C := VV^{T} + \sigma^2I$$

>[!info]
>The formula for matrix derivative
>$$
>\nabla_{X} \left\langle  X^{-1}\,,\,  B\,A  \right\rangle_{tr} = \nabla_{X}\, \text{tr}\left(A X^{-1} B\right) = - \left(X^{-1}\, B\,A\, X^{-1}\right)^{T}
>$$
>Then with chain rule
>$$
>\begin{align*}
> &\nabla_{V} \left\langle  C^{-1}\,,\,  S  \right\rangle_{tr} \\[5pt]
> &= -\left(C^{-1}\, S C^{-1}\right)\,\nabla_{V} C \\[5pt]
> &= -2\left(C^{-1}\, S C^{-1}\right)V
>\end{align*}
>$$

>[!info]
>Substituting these two terms we have equation for MLE solution 
>$$
>2C^{-1}V  -2\left(C^{-1}\, S C^{-1}\right)V = 0
>$$
>Since $$C= VV^{T}+ \sigma^2I \succeq \sigma^2I \succ 0,$$ this leads to
>$$
>\begin{align*}
> C^{-1}\left(I - SC^{-1}\right)V &= 0 \\[5pt]
> \implies \left(I - SC^{-1}\right)V &= 0 \\[5pt]
> \implies SC^{-1} V = V
>\end{align*}
>$$
>
>There are *three possible solutions*
>- $V =0$ for trivial solution
>- $C = S$ i.e. $$S = VV^{T} + \sigma^2I \implies VV^{T} = S - \sigma^2I.$$ This leads to $$V = U\left(\Lambda - \sigma^2 I\right)^{1/2} Q^{T}$$
>- $SC^{-1} V = V$ but $C \neq S$ also $V \neq 0$. 
>	- Assume the SVD of $V$ as $$V = ULW^{T}$$ Then the equation becomes $$\begin{align*} SU \left(L^2 + \sigma^2 I\right)^{-1}L W^{T}  &= ULW^{T} \\[5pt] SUL &= U\left(L^2 + \sigma^2 I\right)L  \end{align*}$$
>	- For every *nonzero singular value* $l_{j} \neq 0$, the above equation becomes $$S\,u_{j} = (l_{j}^2 + \sigma^2)\,u_{j}$$ By definition, this implies that $u_{j}$ must be an *eigenvector* of $S$ corresponding to an eigenvalue $\lambda_{j} =  (l_{j}^2 + \sigma^2)$. In other word, the *nonzero singular value* of $V$ is equal to $$l_{j} = \left(\lambda_{j} - \sigma^2\right)^{1 / 2}$$ 
>	- For *zero singular value* $l_{j} = 0$, the equation holds trivally, and $u_{j}$ is *arbitrary*.
>	  
>Compare case 2 and case 3, we find the unified solution.	  

- [[Singular Value Decomposition of Linear Map]]
- Tipping, M. E., & Bishop, C. M. (1999). Probabilistic principal component analysis. _Journal of the Royal Statistical Society Series B: Statistical Methodology_, _61_(3), 611-622.   pp Appendix A



>[!info]
>From the MLE solution, we see that the optimal mapping $V$ is **invariant to the orthogonal transformation** within $s$-dimensional subspace.
>
>That is, $$\hat{V}_{mle} \in Gr(d, s)$$ identifies an optimal **$s$-dimensional subspace** in $\mathbb{R}^{d}$. In other word, the maximum likelihood estimation is solving an *optimization* on **Grassmann manifold** 



## Explanation

>[!quote]
>The *advantage* of **PPCA** over **factor analysis** is that the MLE has a *closed form solution*, as we show in Section 28.3.2.2. The advantage of PPCA over **non-probabilistic PCA** is that the model defines a *proper likelihood function*, which makes it easier to extend in various ways e.g., by creating mixtures of PPCA models.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 934


>[!info]
>The PPCA can be seen as a **PCA** with **$L_2$ regularization**. 
>
>A similar formulation is in **ridge regression**.

- [[Ridge Regression and L2 Regularization]]

## EM Algorithm for PPCA

- [[Expectation-Maximization Algorithm]]


## Nonlinear Kernel via GP-LVM

![[Gaussian Process Latent Variable Model#^501d8c]]

- [[Gaussian Process Latent Variable Model]]



-----------
##  Recommended Notes and References



- [[Factor Analysis]]
- [[Latent Variable Models]]

- [[Principle Component Analysis]]
- [[Gaussian Random Vector]]
- [[Marginal and Conditional Distribution of Gaussian]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 934 - 936
- [[Deep Learning Foundations and Concepts by Bishop]] pp 506
- [[Elements of Statistical Learning by Hastie]]
- Tipping, M. E., & Bishop, C. M. (1999). Probabilistic principal component analysis. _Journal of the Royal Statistical Society Series B: Statistical Methodology_, _61_(3), 611-622.