---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - math/stochastic_process
keywords:
  - gaussian_process
  - gaussian_process_latent_variable_model
topics:
  - probabilistic_graphical_model
  - machine_learning_models
  - stochastic_process
name: Gaussian Process Latent Variable Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gaussian Process Latent Variable Model

![[Probabilistic Principle Component Analysis#^098ba1]]

![[Probabilistic Principle Component Analysis#^a7df83]]

### From PPCA to Dual PPCA

>[!important] Definition
>The **dual** form of **probabilistic principle component analysis** can be formulated as below.
>
>Assume that $V\in \mathbb{R}^{d\times s}$ is a **random linear mapping** with *i.i.d. rows*. Also the design matrix
>$$
>X = \left[ \begin{array}{c}x_{1}^{T} \\ x_{2}^{T} \\ \ldots \\ x_{n}^{T} \end{array} \right] =   \left[x^{1} \,,\, x^{2}\, ,\, \ldots \,,\, x^{d}  \right]   \in \mathbb{R}^{n\times d}
>$$
>
>We consider a regression problem where the *conditional distribution* of response (*observations*) $x \in \mathbb{R}^{d}$ given covariates (or *states* , *index variables*) $h\in \mathbb{R}^{s}$
>$$
>\left\{
>\begin{align*}
> p(V) &= \prod_{i=1}^{d}\mathcal{N}(v_{i}\;|\; 0, I) \quad \text{ where }v_{i} \text{ is i-th row} \\[5pt]
> p(x_{i}\,|\,h_{i},\, V, \sigma) &= \mathcal{N}(x_{i}\;|\; Vh_{i}\,;\, \sigma^2I ), \quad i=1\,{,}\ldots{,}\,n
>\end{align*}
>\right.
>$$
>
>
>The **marginalized likelihood function** for $x$ is given by 
>$$
>\begin{align*}
>&\log p(X \,|\, H, \sigma) \\[5pt]
>&= -\frac{nd}{2}\log(2\pi) - \frac{d}{2}\log\det\,\lvert HH^{T} + \sigma^2I \rvert  - \frac{1}{2}\sum_{j=1}^{d}\left\langle x^{j} , \left(   HH^{T} + \sigma^2I  \right)^{-1} x^{j} \right\rangle \\[5pt]
>&= - \frac{d}{2}\left[ n\log(2\pi) + \log\det\,\lvert  HH^{T} + \sigma^2I \rvert + \left\langle \left(   HH^{T}  + \sigma^2I  \right)^{-1} ,  J\right\rangle_{tr} \right] 
>\end{align*}
>$$
>where 
>- the index matrix/state matrix $$H = \left[ \begin{array}{c}h_{1}^{T}\\ \ldots \\ h_{n}^{T} \end{array} \right]   \in \mathbb{R}^{n\times s}$$
>- the sample kernel matrix is $$J = \frac{1}{d} X\,X^{T} =  \frac{1}{d}\sum_{j=1}^{d}x^{j}\,(x^{j})^{T} \in \mathbb{R}^{n\times n}$$
>- the **linear kernel matrix** is defined as $$K_{h} := HH^{T}  + \sigma^2I.$$ Note that $K_{h}\in \mathbb{R}^{n\times n}$
>  
>Note that $(X_{h}, h\in \mathcal{H})$ defined above is a **Gaussian process** with state $h$ as index variable.

- [[Regression Problem]]
- [[Probabilistic Principle Component Analysis]]
- [[Gaussian Process]]
- [[RKHS of Gaussian Process]]

>[!important] Definition
>We can find the optimal states/index variables $H^{*} :=  [h_{1}^{*} \,{,}\ldots{,}\,h_{n}^{*}]^{T}$ that **maximize the marginal likelihood**
>$$
>H^{*} = \arg\max_{H} - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert  HH^{T} + \sigma^2I \rvert + \left\langle \left(   HH^{T}  + \sigma^2I  \right)^{-1} ,  J\right\rangle_{tr} \right] 
>$$
>
>The optimal solution of above problem satisfies the equation
>$$
>\begin{align*}
> J \left(   HH^{T}  + \sigma^2I  \right)^{-1} H = H
>\end{align*}
>$$
>Thus the *SVD* of optimal state solution $H$ can be obtained in **closed form**
>$$
>H^{*} = V_{\lceil s \rceil}\left( P_{s} - \sigma^2 I\right)^{1/2} R^{T}
>$$
>where
>- $\Lambda_{ \lceil s \rceil }$ and  $V_{\lceil s \rceil}$ denote the top $s$ largest eigenvalues and their eigenvectors for $J$ $$V_{\lceil s \rceil} = [v_{1} \,{,}\ldots{,}\,v_{s}], \quad \Lambda_{ \lceil s \rceil } = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{s})$$
>- $P_{s} = \text{diag}\left(p_{1} \,{,}\ldots{,}\,p_{s}\right)$ where $$p_{j} = \left\{\begin{array}{ll}\lambda_{j} & \text{ if } \lambda_{j} \ge \sigma^2 \\[5pt] \sigma^2 & \text{ otherwise }\end{array}\right.$$ For $j$ such that $\lambda_{j} < \sigma^2$, the corresponding $u_{j}$ is *arbitrary*.
>- $R\in \mathcal{O}(s)$ is an *arbitrary orthogonal matrix* . 


- [[Probabilistic Principle Component Analysis#Maximum Likelihood Estimation for PPCA]]

### Gaussian Process Latent Variable Model as Nonlinear Dual PPCA

>[!important] Definition
>The **Gaussian process latent variable model (GP-LVM)** is a generalization of *dual probabilistic principle component analysis* where the *linear kernels* is replaced by *nonlinear kernels*
>$$
> K_{h}:= HH^{T}  + \sigma^2I \implies K_{h} = [K(h_{i}, h_{j})]_{i,j\in [n]}
>$$
>where $K: \mathcal{H}\times \mathcal{H} \to \mathbb{R}_{+}$ is a *covariance kernel*. 
>
>That is, the **GP-LVM** replace the *linear encoder* with a *nonlinear encoder* $h \mapsto f(h)$, represented by *Gaussian process*
>$$
>\left\{
>\begin{align*}
> \;p(f) &= \text{GP}(K) \\[5pt]
> \;p(x\,|\,f(h),\, \sigma) &= \mathcal{N}(x\;|\; f(h)\,;\, \sigma^2I )
>\end{align*}
>\right.
>$$
>
>The **marginal log-likelihood** function is given by
>$$
>\log p(X\,|\, H; K) = - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert  K_{h}\rvert + \left\langle   K_{h}^{-1} ,  J\right\rangle_{tr} \right] 
>$$
>where  the **kernel matrix**$$K_{h} = [K(h_{i}, h_{j})]_{i,j\in [n]}$$


- [[Gaussian Process]]
- [[Reproducing Kernel of RKHS]]
- [[RKHS of Gaussian Process]]


### Identifying Optimal State / Index via Marginal Likelihood Maximization

>[!important] Definition
>We can find the optimal states/index variables $H^{*} :=  [h_{1}^{*} \,{,}\ldots{,}\,h_{n}^{*}]^{T}$ that **maximize the marginal likelihood**
>$$
>H^{*} = \arg\max_{H} - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert  K_{h}\rvert + \left\langle   K_{h}^{-1} ,  J\right\rangle_{tr} \right] 
>$$ 
>
>Note that 
>- The loss function is $$\mathcal{L}(K, J) = - \frac{n}{2}\left[ d\log(2\pi) + \log\det\,\lvert  K_{h}\rvert + \left\langle   K_{h}^{-1} ,  J\right\rangle_{tr} \right]$$
>- $$\nabla_{K}\mathcal{L}(K, J) := \nabla_{K} \log p(X | H; K) = K^{-1}\,J\,K^{-1} - K^{-1}$$
>- We can derive the derivative of kernel with respect to each state $$\frac{ \partial K }{ \partial h_{i} } $$
>- By chain rule, we have the **gradient** of *log-marginal likelihood function* $$\frac{ \partial  }{ \partial h_{i} }\mathcal{L}(K, J) = 2\left[  K^{-1}\,J\,K^{-1} - K^{-1} \right]\, \frac{ \partial K }{ \partial h_{i} }, \quad i=1\,{,}\ldots{,}\,n$$
>- We can apply automatic differentiation to solve the gradient with respect to loss
>- The optimization problem can be solved via *iterative algorithms* such as 
>	- **stochastic gradient descent (SGD)**
>	- **(scaled) conjugate gradient descent (SCG)**

- [[Conjugate Gradient Algorithm Nonlinear]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Automatic Differentiation]]


## Explanation

>[!info]
>-  **PPCA**
>	- assumes that the **states/index variables** $x$ are *random with a prior*, 
>	- assume a **linear mapping** $V$ is **deterministic** but *unknown*
>	- use MLE to estimate the linear mapping
>- **GP-LVM** 
>	- assumes that the *states/index variables* are **deterministic** but **unknown**
>	- assume the mapping is **nonlinear** with **known kernel form** $K$
>	- use CG/SGD to estimate the *unknown state/index variables* $x$
>	  
>We can consider GP-LVM as the **nonlinear extension** of the  **dual form** of *PPCA*.	  

^501d8c

- [[Probabilistic Principle Component Analysis]]

>[!info]
>By assuming index/state is *fixed unknown*, we move from **parametric model** to **non-parameteric model** as the model parameter from $$C\in \mathbb{R}^{d\times d} \implies K \in \mathbb{R}^{n\times n}.$$

- [[Parametric Models]]
- [[Nonparametric Models and Semi-Parametric Models]]




-----------
##  Recommended Notes and References


- [[Probabilistic Principle Component Analysis]]
- [[Gaussian Process]]
- [[Factor Analysis]]
- [[Latent Variable Models]]

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]
- [[RKHS of Gaussian Process]]

- [[Regression Problem]]
- [[Linear Dynamic System]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[State-Observation Models]]

- [[Conjugate Gradient Algorithm Nonlinear]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 948 - 949
- Lawrence, N. (2003). Gaussian process latent variable models for visualisation of high dimensional data. _Advances in neural information processing systems_, _16_.

