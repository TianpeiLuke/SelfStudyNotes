---
tags:
  - concept
  - math/functional_analysis
  - statistics/nonparameteric_estimation
  - machine_learning/kernel_methods
keywords:
  - b_spline_functions
topics:
  - machine_learning/kernel_methods
  - statistics/nonparametric_estimation
name: B-Spline Functions
date of note: 2024-11-04
---

## Concept Definition

>[!important]
>**Name**: B-Spline Functions

>[!important] Definition
>The **B-Spline function** of degree order $n$ in $\mathbb{R}^{d}$ is defined *recursively* as the *convolution* of *indicator functions*
>$$
>B_{n} = B_{n-1} * I_{B}
>$$ 
>where
>- $I_{B}$ is the indicator function on a *unit box* $[1 /2 , 1 / 2]^{d}$ or *unit ball* $B(0,1)$ in $\mathbb{R}^{d}$; 
>-  the convolution operation $$f * g = \int f(t)g(\tau- t)dt.$$

- [[Convolution Operation]]
- [[Characteristic Function of Set]]



## Explanation



## Kernel

![[Positive Definite Kernel Examples#^ba3d76]]

- [[Positive Definite Kernel Examples]]


-----------
##  Recommended Notes and References


- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[All of Nonparametric Statistics by Wasserman]] pp 125 - 145
- [[Learning with Kernels by Schölkopf]] pp 46
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 87 - 88
- Wikipedia [B-spline](https://en.wikipedia.org/wiki/B-spline)