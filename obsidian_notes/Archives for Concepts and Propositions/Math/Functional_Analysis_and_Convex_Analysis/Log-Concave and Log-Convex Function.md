---
tags:
  - concept
  - math/convex_analysis
keywords:
  - log_convex_function
  - log_concave_function
topics:
  - convex_analysis
name: Log-Concave and Log-Convex Function
date of note: 2024-06-28
---

## Concept Definition

>[!important]
>**Name**: Log-Concave and Log-Convex Function

>[!important] Defintiion
>A function $f: \mathbb{R}^n \to \mathbb{R}$ is **logarithmically concave** or **log-concave** if 
>- $f(x) >0$ for all $x \in \text{dom}(f),$ and 
>- $\log(f)$ is *concave*.

^b7fd75

>[!important] Defintiion
>A function $f: \mathbb{R}^n \to \mathbb{R}$ is **logarithmically convex** or **log-convex** if $1 / f$ is *log-concave*. 
>
>That is, 
>- $f(x) >0$ for all $x \in \text{dom}(f),$ and 
>- $\log(f)$ is *convex*.

### Direct Definition

>[!important] Defintiion
>A function $f: \mathbb{R}^n \to \mathbb{R}$ is **logarithmically concave** or **log-concave** if 
>- $\text{dom}(f)$ is *convex*, 
>- $f(x) >0$ for all $x \in \text{dom}(f),$ and 
>- for all $x, y \in \text{dom}(f)$, and $0 \le \alpha \le 1$,  $$f\left(\alpha x + (1- \alpha)\,y\right) \ge f(x)^{\alpha}\,f(y)^{1 - \alpha}.$$

^7490df


>[!important] Defintiion
>A function $f: \mathbb{R}^n \to \mathbb{R}$ is **logarithmically convex** or **log-convex** if 
>- $\text{dom}(f)$ is *convex*, 
>- $f(x) >0$ for all $x \in \text{dom}(f),$ and 
>- for all $x, y \in \text{dom}(f)$, and $0 \le \alpha \le 1$,  $$f\left(\alpha x + (1- \alpha)\,y\right) \le f(x)^{\alpha}\,f(y)^{1 - \alpha}.$$

## Explanation

>[!info]
>A *log-concave* function is **quasi-concave** function. And *log-convex* function is **quasi-convex** function.


- [[Cumulative Distribution Function of Random Variable]]
- [[Gaussian Random Variable]]

>[!info]
>$$
>\text{convex function } \implies \text{log-convex function } \implies \text{quasi-convex function } 
>$$

- [[Quasi-Convex Function]]
- [[Convex Function]]


>[!info]
>$$
>\text{concave function } \implies \text{log-concave function } \implies \text{quasi-concave function } 
>$$


## Operations that Preserve the Log-Concavity

### Product

>[!important] Proposition
>The **product** of **log-concave** functions is also **log-concave**. 


### Marginalization


>[!important] Proposition
>Let $f: \mathbb{R}^{n} \times \mathbb{R}^m \to \mathbb{R}$ be **log-concave function**.
>
>Then $$g(x) = \int_{\mathbb{R}^m}f(x, y)dy$$ is **log-concave function**


![[Prékopa-Leindler Inequality#^63fb27]]

- [[Prékopa-Leindler Inequality]]

>[!info] Proof
>Define 
>$$
>\begin{align*}
>H(y) &:= f(\alpha x_{1} + (1- \alpha) x_{2}, y),\\
>F(y) &:= f(x_{1}, y),\\
>G(y) &:= f(x_{2}, y),
>\end{align*}
>$$
>
>Since $f$ is *log-concave*
>$$
>f(\alpha (x_{1}, y_{1}) + (1- \alpha) (x_{2}, y_{2}) ) \ge f(x_{1}, y_{1})^{\alpha}\,f(x_{2}, y_{2})^{1 - \alpha}
>$$
>it is equivalent to 
>$$
>H(\alpha y_{1} + (1 - \alpha) y_{2}) \ge F(y_{1})^{\alpha}\;G(y_{2})^{1 - \alpha}
>$$
>
>By **Prékopa-Leindler Inequality**, 
>$$
>\int_{\mathbb{R}^m}H(y)dy \ge \left(\int_{\mathbb{R}^m}F(y)dy \right)^{\alpha}\;\left(\int_{\mathbb{R}^m}G(y)dy \right)^{1 - \alpha}
>$$
>which is equivalent to
>$$
>\int_{\mathbb{R}^m}f(\alpha x_{1} + (1- \alpha) x_{2}, y)dy \ge \left(\int_{\mathbb{R}^m}f(x_{1}, y)dy \right)^{\alpha}\;\left(\int_{\mathbb{R}^m}f(x_{2}, y)dy \right)^{1 - \alpha}
>$$
>
>In other word
>$$
>g(y) := \int_{\mathbb{R}^m}f(x, y)dy
>$$
>is **log-concave**. Q.E.D.


## Example

>[!example]
>The **likelihood function** $\ell(\eta; x)$ of any **exponential family** is **log-concave**.

- [[Exponential Family of Distributions]]






-----------
##  Recommended Notes and References

- [[Log-Concave Measure]]

- [[Convex Function]]
- [[Weak Brunn-Minkowski Inequality]]
- [[Prékopa-Leindler Inequality]]


- [[Convex Optimization by Boyd]] pp 104