---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - entropy_functional
  - sub_additivity
  - tensorization_entropy
topics:
  - concentration_inequality
  - information_theory
name: Sub-Additivity of Phi Entropy Functional
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Sub-Additivity of $\Phi$-Entropy Functional

>[!important] Proposition
>Let $\mathcal{C}$ denote the class of *functions* $\Phi: [0, \infty) \to \mathbb{R}$ that are 
>- **continuous** and **convex** on $[0, \infty)$, 
>- **twice differentiable** on $(0, \infty)$, and 
>- such that 
>	- either $\Phi$ is **affine** or 
>	- $\Phi''$ is **strictly positive** and $1/\Phi''$ is **concave**. 
>  
>For all $\Phi \in \mathcal{C}$, the **entropy functional** $H_{\Phi}$ is **sub-additive**. 
>
>That is,
>$$
> \begin{align}
>  \mathbb{E}\left[ \Phi(X) \right] - \Phi( \mathbb{E}\left[X\right]) &\le \sum_{i=1}^{n}  \mathbb{E}\left[ \mathbb{E}_{(-i)}\left[\Phi(X)\right] - \Phi(\mathbb{E}_{(-i)}\left[X\right]) \right],\\
> \Leftrightarrow H_{\Phi}(X) &\le  \mathbb{E}\left[ \sum_{i=1}^{n} H_{\Phi}^{(-i)}(X) \right]\nonumber
> \end{align}
>$$  
>where $$H_{\Phi}^{(-i)}(X) := \mathbb{E}_{(-i)}\left[\Phi(X)\right] - \Phi(\mathbb{E}_{(-i)}\left[X\right])$$ is the **conditional entropy** and,  $\mathbb{E}_{(-i)}\left[ \cdot \right]$ denotes **conditional expectation** conditioned on the vector $Z$ with $i$-th element *leaving out*.
>$$Z_{(-i)}:= (Z_1 \,{,}\ldots{,}\, Z_{i-1}, Z_{i+1} \,{,}\ldots{,}\, Z_n).$$

- [[Phi Entropy Functional]]
- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Jackknife Estimator of Variance]]


>[!important] Tensorization property of $\Phi$-Entropy Functional
>$$
>H_{\Phi, \otimes_{i=1}^n \mu_{i} }(X) \le  \mathbb{E}_{\otimes_{i=1}^n \mu_{i} }\left[ \sum_{i=1}^{n} H_{\Phi, \mu_{i}}(X) \right]
>$$
>where each $H_{\Phi, \mu_{i}}(X)$ take expectation on $\mu_{i}$ only.





## Explanation














-----------
##  Recommended Notes and References

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Entropy Functional]]
- [[Phi Entropy Functional]]

- [[Jackknife Estimator of Variance]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]