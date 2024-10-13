---
tags:
  - concept
  - statistics/inference
  - statistics/estimation
  - optimization/algorithm
  - optimization/linear_optimization
  - optimization/theory
keywords:
  - least_absolute_deviations
  - sparsity
topics:
  - statistics/inference
  - statistics/estimation
  - optimization/theory
  - optimization/algorithm
name: Least Absolute Deviations Solution via Barrier Method and Iterative Least Square
date of note: 2024-10-11
---

## Concept Definition

>[!important]
>**Name**: Least Absolute Deviations Solution via Barrier Method and Iterative Least Square

![[Linear Regression#^06ce34]]

![[Linear Regression#^24812d]]

- [[Linear Regression]]

![[Least Absolute Deviations#^5fb0d6]]

![[Least Absolute Deviations#^ee1435]]

- [[Least Absolute Deviations]]

### LAD as Linear Programming

>[!important]
>Define the **auxiliary variables** $\xi = (\xi_{1} \,{,}\ldots{,}\,\xi_{m})\in \mathbb{R}^{m}$ so that 
>$$\xi_{s} \ge \left\lvert Y_{s} - \mu_{s}(X_{s}; \beta) \right\rvert := \left\lvert Y_{s} - \sum_{i=1}^{d}\beta_{i}\,X_{s}^{i} - \beta_{0}  \right\rvert, \quad s=1\,{,}\ldots{,}\,m.$$
>so
>$$
> -\xi_{s} \le Y_{s} - \mu_{s}(X_{s}; \beta)  \le \xi_{s}
>$$
>
>The **least  absolute deviations (LAD) problem** can be formulated as a **linear optimization problem**
>$$
>\begin{align*}
> \min_{\beta \in \mathbb{R}^{n}, \, \xi \in \mathbb{R}^{m}}\;&\; \left\langle  1\,,\, \xi   \right\rangle \\[5pt]
> \text{s.t. }\;&\; X\beta - \xi \preceq y \\[5pt]
> &\; -X\beta - \xi \preceq -y
>\end{align*}
>$$
>or in matrix form
>$$
>\begin{align*}
> \min_{\beta \in \mathbb{R}^{n}, \, \xi \in \mathbb{R}^{m}}\;&\; \left\langle  1\,,\, \xi   \right\rangle \\[5pt]
> \text{s.t. }\;&\; \left[ \begin{array}{cc} X & - I \\[5pt] - X & - I\end{array} \right] \left[ \begin{array}{c} \beta \\[5pt] \xi \end{array} \right] \preceq \left[ \begin{array}{c} y \\[5pt]-y \end{array} \right]
>\end{align*}
>$$

^538310

- [[Linear Optimization Problem]]

### Barrier Method Solution as Iterative Weighted Least Square

![[Barrier Method for Linear Optimization#^87009c]]


>[!info]
>We can use the **Barrier method** to solve this problem, which for each $t>0$ solve the **Newton equation**
>$$
>\begin{align*}
>\left[ \begin{array}{cc} X^{T} & - X^{T} \\[5pt] - I & - I\end{array} \right] \left[ \begin{array}{cc} D_{1} &  \\[5pt]  & D_{2}\end{array} \right] \left[ \begin{array}{cc} X & - I \\[5pt] - X & - I\end{array} \right]\left[ \begin{array}{c}\Delta \beta \\[5pt] \Delta \xi \end{array} \right]  &= - \left[ \begin{array}{c} X^{T}g_{1}\\[5pt] g_{2} \end{array} \right] 
>\end{align*}
>$$
>where 
>-  $D_{1}$ measure the inverse of **squared distance** between **regression residual** and **lower bound**$$D_{1} = \text{diag}\left(y - X\beta + \xi \right)^{-2}$$
>- $D_{2}$ measure the inverse of **squared distance** between **regression residual** and **upper bound** $$D_{2} = \text{diag}\left(-y + X\beta + \xi \right)^{-2}$$
>- $g_{1}$ measure the *inverse* of the **difference** the **distances** from *residual* to **upper bound** and the distance to **lower bound** $$g_{1} = \text{diag}\left(y - X\beta + \xi \right)^{-1}1 - \text{diag}\left(-y + X\beta + \xi \right)^{-1}1$$
>- $g_{2}$ measure the *inverse* of the **gap** between $1 / t$ and **absolute deviations** $$g_{2} = t\,1 - \text{diag}\left(y - X\beta + \xi \right)^{-1}1 + \text{diag}\left(-y + X\beta + \xi \right)^{-1}1$$

^9104d2

- [[Newton Method]]
- [[Barrier Method for Linear Optimization]]
- [[Primal-Dual Interior Point Method for Linear Optimization]]

>[!important]
>Apply block elimination on $\Delta \xi$, we have the **normal equation** for *incremental* $\beta$ $\Delta \beta$
>$$
>X^{T}\,D\,X\,\Delta \beta = - X^{T}g
>$$
>where
>- $$D := 4D_{1}D_{2}(D_{1} + D_{2})^{-1} = 2 \left(\text{diag}(\xi)^2 + \text{diag}(y -X\beta)^2\right)^{-1}$$
>- $$g := g_{1} + (D_{1} - D_{2})(D_{1} + D_{2})^{-1}g_{2}$$
>  
>Then we can compute the step for auxiliary variables $\Delta \xi$  as $$\Delta \xi = (D_{1} + D_{2})^{-1}\left[-g_{2} + (D_{1} - D_{2})A\,\Delta \beta\right]$$  

^cb93bb

- [[Normal Equations and Newton System of Equations]]

>[!important]
>This shows that the **LAD estimation** can be computed by solving a series of **weighted least square problems**
>$$
>\min_{\Delta\beta}\; \lVert W (X\, \Delta\beta - \hat{b})  \rVert_{2}^{2} 
>$$
>where 
>- $$W := D^{1 / 2}$$
>- $$\hat{b} = -D^{-1}\,g $$

^4d5e6e

- [[Least Square Estimation]]
- [[Algorithms for Least Square Estimation Problem]]


## Explanation


>[!quote]
>the cost of solving the **$\ell_{1}$-norm approximation** problem is the cost of solving a relatively small number of **weighted least-squares problems** with the same matrix $A$, and weights that change at each iteration. If $A$ has structure that allows us to solve the least-squares problem *fast* (for example, by exploiting sparsity), then we can solve $$X^{T}\,D\,X\,\Delta \beta = - X^{T}g$$ fast.
>
>-- [[Convex Optimization by Boyd]] pp 618



## $\ell_{1}$ vs. $\ell_{2}$ Regression Problem

![[Least Square Estimation#^9775a7]]

- [[Least Square Estimation]]





-----------
##  Recommended Notes and References



- [[Least Absolute Deviations]]
- [[LASSO and Sparsity-Induced Least Square]]
- [[Laplace Distribution]]


- [[Mathematical Statistics by Shao]] pp 123
- [[Theory of Point Estimation by Lehmann]] pp 484
- [[Convex Optimization by Boyd]] pp 617 - 618