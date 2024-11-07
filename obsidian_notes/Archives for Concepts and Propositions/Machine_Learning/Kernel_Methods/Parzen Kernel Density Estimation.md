---
tags:
  - concept
  - machine_learning/density_estimation
keywords:
  - kernel_density_estimation
  - parzen_density_estimator
topics:
  - machine_learning/density_estimation
name: Parzen Kernel Density Estimation
date of note: 2024-11-04
---

## Concept Definition

>[!important]
>**Name**: Parzen Kernel Density Estimation

![[Reproducing Kernel of RKHS#^8b1e73]]

>[!important] Definition
>Let $\left\{ X_{i} \right\}_{i=1}^{n}$ be i.i.d. *random samples* from a distribution $P$ on $(\mathcal{X}, \mathscr{F})$, and let $p_{X}(x)$ be the *probability density function*. 
>
>- Assume that $\mathcal{X} \subseteq \mathbb{R}$.
>  
>A **Parzen kernel estimate** of the probability density function $p_{X}$ is given by 
>$$
>\hat{f}_{X}(x) := \frac{1}{nh}\,\sum_{i=1}^{n}\,K_{h}(X_{i}, x) :=  \frac{1}{nh}\,\sum_{i=1}^{n}\,K_{h}\left(\frac{x - X_{i}}{h}\right)
>$$
>where $K_{\lambda}: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$ is a *reproducing kernel* of a *reproducing kernel Hilbert space (RKHS)* $\mathcal{H}$, which is given by $$K_{h}(y, x) := \frac{1}{h} K\left(\frac{x - y}{h}\right).$$
>- The parameter $h$ is called the **window width**, also called the **smoothing parameter** or the **bandwidth**.
>- The *smooth Parzen estimate* can be seen as the *empirical measure* **operating** on  the kernel function $$\hat{f}_{X}(x) = P_{n}\,K_{h}(\cdot, x) = \int_{\mathcal{X}}\,K_{h}(y, x)P_{n}(dy)$$ where $P_{n}$ is the *empirical measure* $$P_{n} := \frac{1}{n} \sum_{i=1}^{n}\delta_{X_{i}}$$

- [[Probability Density Function of Random Variable]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Empirical Process and Empirical Measure]]
- [[Riesz-Markov Representation Theorem]]


## Explanation

>[!quote]
>The **Parzen density estimate** is the equivalent of the **local average**, and improvements have been proposed along the lines of local regression on the log scale for densities;
>
>- [[Elements of Statistical Learning by Hastie]] pp 209

![[Lebesgue Density from Radon-Nikodym Derivative#^5093e6]]

- [[Lebesgue Density from Radon-Nikodym Derivative]]
- [[Lebesgue Measure]]





-----------
##  Recommended Notes and References




- [[Probability Space]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[All of Nonparametric Statistics by Wasserman]] pp 125 - 145
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 770
- [[Elements of Statistical Learning by Hastie]] pp 208 - 215
- [[Density Estimation for Statistics and Data Analysis by Silverman]] pp 15
- [[Learning with Kernels by Schölkopf]]