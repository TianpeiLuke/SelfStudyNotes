---
tags:
  - concept
  - machine_learning/models
  - machine_learning/kernel_methods
  - machine_learning/density_estimation
keywords:
  - k_nearest_neighbor
  - k_nearest_neighbor_density_estimation
topics:
  - machine_learning/density_estimation
  - machine_learning/kernel_methods
name: k Nearest Neighbor Density Estimation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: k Nearest Neighbor Density Estimation

![[Parzen Kernel Density Estimation#^da5707]]

- [[Parzen Kernel Density Estimation]]

>[!important] Definition
>Let $\left\{ X_{i} \right\}_{i=1}^{n}$ be i.i.d. *random samples* from a distribution $P$ on $(\mathcal{X}, \mathscr{F})$, and let $p_{X}(x)$ be the *probability density function*. 
>
>- Assume that $\mathcal{X} \subseteq \mathbb{R}$.
>
>Denote the distance between two points as $d(x, y)$. 
>- For given $x\in \mathcal{X}$, arrange all $y\in \mathcal{X}$ according the distance $d(x, y)$ in **ascending order** $$d^{(1)}(x)  \,{\le}\ldots{\le}\, d^{(k)}(x) \,{\le}\ldots{\le}\, d^{(n)}(x)$$ 
>  
>The **$k$-th nearest neighbor density estimate** is defined by 
>$$
>\hat{f}_{X}(x) = \frac{k-1}{2\,n\,d^{(k)}(x)}
>$$  
>where
>- the integer $k$ controls the *degree of smoothing*. Typically choose $$k \asymp \sqrt{n}$$

- [[k Nearest Neighbor Classification]]

### Generalized K-Nearest Neighbor Estimate

![[Parzen Kernel Density Estimation#^592bda]]

- [[Parzen Kernel Density Estimation]]
- [[Density Estimation for Statistics and Data Analysis by Silverman]] pp 21

## Explanation

>[!quote]
>The **nearest neighbour** dass of estimators represents an attempt to adapt the amount of **smoothing to the 'local' density** of data. The degree of smoothing is controlled by an integer $k$, chosen to be considerably smaller than the sample size; typically $k \approx \sqrt{ n }.$
>
>-- [[Density Estimation for Statistics and Data Analysis by Silverman]] pp 19


![[Lebesgue Density from Radon-Nikodym Derivative#^5093e6]]

- [[Lebesgue Density from Radon-Nikodym Derivative]]




-----------
##  Recommended Notes and References



- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Mathematical Statistics by Shao]] pp 332
- [[Density Estimation for Statistics and Data Analysis by Silverman]] pp 19, 96 - 100
- [[Learning with Kernels by Schölkopf]]
- Devroye, L., Györfi, L., & Lugosi, G. (2013). _A probabilistic theory of pattern recognition_ (Vol. 31). Springer Science & Business Media.
