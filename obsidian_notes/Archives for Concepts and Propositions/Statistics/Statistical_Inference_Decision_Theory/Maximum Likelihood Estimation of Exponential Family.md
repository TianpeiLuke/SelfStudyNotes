---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - math/convex_analysis
  - math/information_theory
  - exponential_family
keywords:
  - maximum_likelihood_estimation
  - exponential_family
topics:
  - statistics/estimation
name: Maximum Likelihood Estimation of Exponential Family
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Maximum Likelihood Estimation of Exponential Family

![[Maximum Likelihood Estimation#^646b70]]

>[!important] Definition
>Let $\mathcal{D} := \{ X_{1} \,{,}\ldots{,}\, X_{n}\}$ be a set of i.i.d. samples from an *exponential family* where the probability density function with respect to a $\sigma$-finite measure $\nu$
>$$
> f_{\eta}(x) := \frac{d\mathcal{P}_{\eta}}{d\nu}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>where $T: \mathcal{X} \to \mathbb{R}^{d}$ is a sufficient statistic of parameter $\eta \in \Omega$ and $A(\eta)$ is the *log-partition function*. Define the *primal feasible region* is $$\Omega := \{ \eta \in \mathbb{R}^{d}: A(\eta) < \infty \}.$$
>
>The **maximum likelihood estimation** $\hat{\eta}$ of parameter $\eta \in \Omega$ given samples $\mathcal{D}$ is obtained by solving the **convex optimization problem**
>$$
>\begin{align*}
> \min_{\eta \in \Omega} \;& - \sum_{i=1}^{n}\left\langle  \eta\,,\, T(X_{i})   \right\rangle + A(\eta)
>\end{align*}
>$$
>Note that $A(\eta)$ is *convex function* and the feasible region $\Omega \subset \mathbb{R}^{d}$ is a *convex subset*. 
>
>Explicitly, 
>$$
>\begin{align*}
> \hat{\eta}_{mle} =  \arg\min_{\eta \in \Omega} \left\{    - \sum_{i=1}^{n}\left\langle  \eta\,,\, T(X_{i})   \right\rangle + \log \int_{\mathcal{X}}\exp \left(\left\langle  \eta\,,\, T(x) \right\rangle\right) \,h(x)\,d\nu(x)\right\}
>\end{align*}
>$$
>Given the *uniqueness of optimal solution*, the MLE $\hat{\eta} := \hat{\eta}(\mathcal{D})$ is unique.

- [[Log-Partition Function of Exponential Family]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]

### Gradient of Log-likelihood

![[Exponential Family of Distributions#^c95a01]]

>[!info]
>Given the above special form of score function (i.e. gradient of log-likelihood)

## Explanation


## Solution of MLE

>[!important]
>Since the MLE problem is convex for exponential family, the **necessary and sufficient condition** for **maximum likelihood estimator** $\hat{\eta}_{mle}$ is that
>$$
>\begin{align*}
> &\nabla_{\eta}\; \ell(\hat{\eta}_{mle}; \mathcal{D}) = 0 \\
>\implies&  \nabla_{\eta} A\left(\hat{\eta}_{mle}\right) = \frac{1}{n}\sum_{i=1}^{n}T(X_{i})\\[5pt]
> \implies& \hat{\eta}_{mle} = \left(\nabla A\right)^{-1}\left(\frac{1}{n}\sum_{i=1}^{n}T(X_{i})\right)
\end{align*}
>$$
>Moreover the MLE of  **mean parameter** $\hat{\mu}$
>$$\hat{\mu}_{mle} = \nabla A(\hat{\eta}_{mle}) = \frac{1}{n}\sum_{i=1}^{n}T(X_{i}).$$
 > is **unbiased** 
>$$
>\mu = \mathbb{E}_{ f_{\eta} }\left[  T(X) \right] =  \mathbb{E}_{ f_{\eta} }\left[  \hat{\mu}_{mle}\right]
>$$

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Generalized Linear Models]]
- [[Bias of Point Estimator and Unbiasedness]]


## UMVUE

>[!important]
>Note that the **Hessian** of *log-likelihood* is the **Fisher Information matrix** of $\eta$
>$$
>\nabla_{\eta}^2\; \ell(\eta; \mathcal{D}) = \nabla_{\eta}^2\;A(\eta) = I(\eta)
>$$
>The second-order sufficient condition for optimal solution of convex problem is that
>$$
>\nabla_{\eta}^2\; \ell(\eta; \mathcal{D}) = I(\eta) \succ 0
>$$
>Similarly, under **mean  parameterization**, $$\nabla_{\mu}^2\; \ell(\eta(\mu); \mathcal{D}) = (I(\mu))^{-1} $$

![[Fisher Information for Exponential Family#^713d66]]

- [[Fisher Information for Exponential Family]]
- [[Positive Semidefinite Transformation]]

>[!important] 
>From above proposition, the **variance-convariance matrix** of sufficient statistic $T$ is 
>$$
>\text{Cov}\left(T, T\right) = I(\hat{\eta}_{mle}) = \left[ I(\hat{\mu}_{mle}) \right]^{-1} 
>$$
>The **converse** holds true as well, according to [[Cramér-Rao Lower Bound]], which is attained for the exponential family.
>
>By [[Rao-Blackwell Theorem]], this concludes that 
>$$\hat{\mu}_{mle} = \nabla A(\hat{\eta}_{mle}) = \frac{1}{n}\sum_{i=1}^{n}T(X_{i})$$
 >is the **uniformly minimum variance unbiased estimator** of $\mu$.

- [[Rao-Blackwell Theorem]]
- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Cramér-Rao Lower Bound]]



-----------
##  Recommended Notes and References



- [[Exponential Family of Distributions]]


- [[Likelihood Function]]
- [[Sufficient Statistics]]


- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]

- [[Kullback-Leibler Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]

- [[Convex Optimization Problem]]


- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Elements of Information Theory by Cover]]
- [[All of Statistics A Concise Course by Wasserman]]

