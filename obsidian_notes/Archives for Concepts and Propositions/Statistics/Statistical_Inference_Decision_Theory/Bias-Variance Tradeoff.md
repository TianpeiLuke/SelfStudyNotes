---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - bias_variance_tradeoff
topics:
  - statistics/estimation
name: Bias-Variance Tradeoff
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Bias-Variance Tradeoff


![[Regression Problem#^cae88d]]


### Decomposition of Mean Squared Loss

>[!important] Definition
>Consider a **regression problem** where $f: \mathcal{X} \to \mathcal{Y}$ to an *estimator* of response $Y$ given covariate $X$
>
>The *mean squared error* can be decomposed into two terms
>$$
>\begin{align*}
> \mathbb{E}\left[ \lVert Y- f(X) \rVert ^2 \Big| X  \right] &= \mathbb{E}\left[ \lVert Y - \mathbb{E}\left[  f(X) \right] + \mathbb{E}\left[  f(X) \right] - f(X) \rVert ^2 \Big| X \right]\\[5pt]
> &= \mathbb{E}\left[ \lvert Y - \mathbb{E}\left[f(X)\right] \rvert ^2 \Big| X\right]+  \mathbb{E}\left[ \lVert f(X) -  \mathbb{E}\left[  f(X) \right]  \rVert ^2 \Big| X \right]\\[5pt]
> &=  \lvert Y - \mathbb{E}\left[f(X)\right] \rvert ^2 +  \mathbb{E}\left[ \lVert  f(X) - \mathbb{E}\left[  f(X) \right] \rVert ^2 \Big| X \right] \\[5pt]
> &= \text{Bias}^2 + \text{Var}(f(X))
> \end{align*}
> $$ 
> - The first term is the *square* of **bias** of estimator $$\text{Bias} := \left(Y - \mathbb{E}\left[f(X)\right]\right)$$
> - The second term is the **variance** of estimator $$\text{Var}(f(X)) :=  \mathbb{E}\left[ \lVert  f(X) -  \mathbb{E}\left[  f(X) \right] \rVert ^2 \Big| X \right]$$
> 
>The second last equality is due to *orthogonality* 
>$$
> \begin{align*}
> &\mathbb{E}\left[ \left(Y - \mathbb{E}\left[f(X)\right] \right)^T\,\left(\mathbb{E}\left[f(X)\right] - f(X)\right) \right] \\
> &= \left(Y - \mathbb{E}\left[f(X)\right] \right)^T\,\mathbb{E}\left[ \left(\mathbb{E}\left[f(X)\right] - f(X)\right) \right] \\[5pt]
> &= \left(Y - \mathbb{E}\left[f(X)\right] \right)^T\, \left(\mathbb{E}\left[f(X)\right] - \mathbb{E}\left[f(X)\right] \right) = 0.
> \end{align*} 
>$$

- [[Regression Problem]]
- [[Least Square Estimation]]
- [[Generalized Linear Models]]
- [[Bias of Point Estimator and Unbiasedness]]
- [[Minimum Mean Square Estimation]]

### Bias-Variance Tradeoff

>[!important] Definition
>When choosing estimator $f\in \mathcal{F}$ to minimize the *mean squared error*, we are facing two *conflicting objectives*:
>- The **bias** will *decrease* when the hypothesis class $\mathcal{F}$ is more complex; 
>	- This means that the estimator will more *closely fit* the observations in the dataset.
>	- One extreme is the **interpolation**.
>- The **variance** will *decrease* when the hypothesis class $\mathcal{F}$ is less complex; 
>	- This means that the estimator will be more **robust** and *noise-tolerate*.
>	- Low variance implies that the *estimator* will be more *deterministic* and **stable**.
>	- Low variance leads to *better generalization*.
>	  
>	  
>This phenomenon is called the **bias-variance tradeoff**.

- [[Bias of Point Estimator and Unbiasedness]]


## Explanation

- [[Gauss–Markov Theorem]]


## Bias-Complexity Tradeoff

![[Bias-Complexity Tradeoff and Overfitting#^73e1a0]]


>[!important]
> It is easy to see that the *bias-variance tradeoff* is a special case of **bias-complexity tradeoff** when the loss is defined as *the regression loss*.
> -  The **bias term** corresponds to **the approximation error** for the model (e.g. least square model) and
> - the **variance term** corresponds to the **estimation error**.

- [[Bias-Complexity Tradeoff and Overfitting]]


## Monte Carlo Approximation

- [[Monte Carlo and Applications]]
- [[Markov Chain Monte Carlo Methods]]





-----------
##  Recommended Notes and References


- [[Bias-Complexity Tradeoff and Overfitting]]
- [[Point Estimator]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]]
- [[Elements of Statistical Learning by Hastie]] pp 24, 37, 219
- Wikipedia [Bias-variance_tradeoff](https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff)