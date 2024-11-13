---
tags:
  - concept
  - statistics/estimation
keywords:
  - maximum_likelihood_estimation
  - kl_divergence
topics:
  - statistics/estimation
name: Maximum Likelihood Estimation
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Maximum Likelihood Estimation

![[Likelihood Function#^f6d78c]]

>[!important] Definition
>Let $\overline{\Theta}$ be the closure of $\Theta \subset \mathbb{R}^{d}$. 
>
>A $\hat{\theta} \in \overline{\Theta}$ satisfying 
>$$
>\begin{align*}
>\ell(\hat{\theta} ; X) = \max_{\theta \in \overline{\Theta}}\,\ell(\theta; X)
>\end{align*}
>$$
>is called a **maximum likelihood estimate (MLE)** of $\theta$. 
>
>- If, In addition,  $\hat{\theta} := \hat{\theta}(X)  \in \overline{\Theta}$ is a *Borel function* of sample $X$  *$\mu$-almost everywhere*, then $\hat{\theta}$ is called a **maximum likelihood estimator (MLE)** of $\theta$. 
>- For any measurable function $g: \Theta \to \mathbb{R}^{p}$ where $p \le d$, if $\hat{\theta}$ is a *maximum likelihood estimator (MLE)* of $\theta$, then $$\hat{\nu} = g(\hat{\theta})$$ is an *MLE* of $\nu = g(\theta).$

^646b70

- [[Likelihood Function]]
- [[Point Estimator]]
- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]
- [[Borel Measure]]

## Explanation

>[!info]
>As an estimator, the MLE $$\hat{\theta} := \hat{\theta}(X)$$ is defined $\mu$-almost everywhere.

- [[Pointwise Almost Everywhere Convergence]]

## Likelihood Equation and Log-Likelihood Equation

>[!important] Definition
>If the likelihood functions  $\ell(\theta)$ is **differentiable** on  $\text{int}(\Theta)$, the *first-order optimality condition* provides the criteria for **MLE candidates** $\hat{\theta} \in \overline{\Theta}$, which should satisfy the **likelihood equation**
>$$
>\frac{ \partial}{ \partial \theta }\ell(\hat{\theta}; x) = 0.  
>$$

- [[Interior of Set]]

>[!important] Definition
>Since $\log(x)$ is strictly increasing, and differentiable, $\hat{\theta}$ is a *maximum likelihood estimator (MLE)* of $\theta$ *if and only if* it maximizes the **log-likelihood function** $\log \ell(\theta)$. 
>
>In particular, **MLE candidates** $\hat{\theta} \in \overline{\Theta}$ solve the **log-likelihood equation**
>$$
>\frac{ \partial}{ \partial \theta }\log \ell(\hat{\theta}; x) = 0.  
>$$

- [[Log-Likelihood Score Function and Fisher Score]]


>[!info]
>Note that $\theta$’s satisfying the *likelihood equation* may be **local** or **global minima,** **local** or **global maxima**, or simply **stationary points**. 
>
>Also, extrema may occur at the **boundary** of $\Theta$ or when $\lVert \theta \rVert \to \infty$. 
>
>Furthermore, if $\ell(\theta)$ is **not always differentiable**, then extrema may occur at **nondifferentiable** or **discontinuity points** of $\ell(\theta)$. 
>
>Hence, it is important to analyze the entire likelihood function to find its maxima.

## Asymptotic Analysis

- [[Asymptotic Efficiency of Maximum Likelihood Estimation]]
- [[Fisher Information]]


## MLE problem via KL divergence

- [[Maximum Likelihood Estimation via KL Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Information Projection and Moment Projection]]






-----------
##  Recommended Notes and References


- [[Point Estimator]]
- [[Likelihood Function]]




- [[All of Statistics A Concise Course by Wasserman]]
- [[Theory of Point Estimation by Lehmann]]
- [[Mathematical Statistics by Shao]] pp 274 - pp 275
- [[Elements of Statistical Learning by Hastie]]