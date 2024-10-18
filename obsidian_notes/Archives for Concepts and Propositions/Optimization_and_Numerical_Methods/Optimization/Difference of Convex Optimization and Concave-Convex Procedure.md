---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - dc_programming
  - difference_of_convex_function
  - convex_concave_procedure
topics:
  - optimization/algorithm
  - optimization/theory
name: Difference of Convex Optimization
date of note: 2024-10-15
---

## Concept Definition

>[!important]
>**Name**: Difference of Convex Optimization and Concave-Convex Procedure

![[Majorization-Minimization Algorithm#^918339]]

![[Majorization-Minimization Algorithm#^aad1a0]]


>[!important] Definition
>The **Difference of Convex (DC) Programming** is defined by the optimization problem
>$$
>\begin{align*}
> \min_{x}\;&\; f_{0}(x) - g_{0}(x)\\[5pt]
> \text{s.t. }\;&\; f_{i}(x) - g_{i}(x) \le 0\quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$
>where $f_{i}, g_{i}$ for all $i=0,1\,{,}\ldots{,}\,m$ are *convex real-valued functions* on $\mathbb{R}^{n}$.

^f02812

- [[Majorization-Minimization Algorithm]]

### Convex-Concave Procedure

>[!important] Definition
>The **concave-convex procedure (CCCP)** developed to reach a *local minimum* of *DC programming* by solving the following problem for each iteration $k$
>$$
>\begin{align*}
> \min_{x}\;&\; M_{0}(x, x_{k})\\[5pt]
> \text{s.t. }\;&\; M_{i}(x, x_{k}) \le 0\quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$
>where the **minorizing surrogate function** is defined as
>$$
>M_{i}(x, x_{k}) := f_{i}(x) - g_{i}(x_{k}) - \left\langle \nabla g_{i}(x_{k}) , x - x_{k} \right\rangle, \quad i=0\,{,}\ldots{,}\,m
>$$
>- This algorithm is a special case of **majorization-minimization algorithm.**

^6d9a69






## Explanation





-----------
##  Recommended Notes and References


- [[Bregman Divergence]]
- [[Convex Optimization Problem]]
- [[Convex Function]]


- [[Expectation-Maximization Algorithm]]

- [[sunMajorizationMinimizationAlgorithmsSignal2017]]; Sun, Y., Babu, P., & Palomar, D. P. (2017). Majorization-Minimization Algorithms in Signal Processing, Communications, and Machine Learning. _IEEE Transactions on Signal Processing_, _65_(3), 794–816. IEEE Transactions on Signal Processing. [https://doi.org/10.1109/TSP.2016.2601299](https://doi.org/10.1109/TSP.2016.2601299); 