---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - gaussian_concentration_theorem
  - gaussian_concentration_inequality
topics:
  - concentration_inequality
name: Gaussian Concentration Inequality (Sharp Bound)
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Gaussian Concentration Inequality


>[!important] Gaussian Concentration Inequality
>Let $Z = (Z_1 \,{,}\ldots{,}\, Z_n)$ be a vector of $n$ **independent standard normal** random variables. 
>
>Let $f : \mathbb{R}^n \to \mathbb{R}$ denote an **$L$-Lipschitz function**, that is, there exists a constant $L > 0$ such that for all $x, y \in \mathbb{R}^n$,
>$$
> \begin{align*}
> |f(x) - f(y)| &\le  L\lVert x - y \rVert.
> \end{align*}
>$$  
>
>Then, for all $\lambda \in \mathbb{R}$,
>$$
> \begin{align}
> \psi_{f(Z) -  \mathbb{E}\left[f(Z)\right] }(\lambda) &\le \frac{L^2 \lambda^2}{2} 
> \end{align}
>$$ 

^29f0a7

- [[Lipschitz Continuous Function]] ^764ff7
- [[Gaussian Random Vector]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Herbst Argument]]

>[!important] The Tsirelson-Ibragimov-Sudakov Inequality
>Let $Z = (Z_1 \,{,}\ldots{,}\, Z_n)$ be a vector of $n$ **independent standard normal** random variables. 
>
>Let $f : \mathbb{R}^n \to \mathbb{R}$ denote an **$L$-Lipschitz function**. 
>
>Then, for all $t > 0$, 
>$$
> \begin{align}
> \mathcal{P}\set{f(Z) -  \mathbb{E}\left[f(Z)\right]  \ge t } &\le \exp \left( - \frac{t^2}{2 L^2} \right). 
> \end{align}
>$$ 

^275d78



>[!important] Gaussian Concentration Inequality (Sharp Bound)
> Let $$Z = (Z_1 \,{,}\ldots{,}\,Z_n)$$ be a vector of $n$ **independent** **standard normal** random variables. 
> 
> Let $f : \mathbb{R}^n \to \mathbb{R}$ denote an **$L$-Lipschitz function**. 
> 
> Then, for all $t > 0$, 
> $$
> \begin{align}
> \mathcal{P}\set{f(Z) - \text{med}(f(Z)) \ge t } &\le 1 - \Phi \left(\frac{t}{L}\right). 
> \end{align}
>$$  
>where $\Phi(t)$ is the *cumulative distribution function* of standard normal random variable.

^5bdfe6

- [[Gaussian Cumulative Distribution Function]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]

- [[Gaussian Isoperimetric Theorem]]
- [[Gaussian Concentration Theorem]]

>[!important]
>The inequality above cannot be improved in general as for $$f(x) = n^{-1/2}\sum_{i=1}^n x_i,$$ **equality is achieved** for all $t > 0$.

## Explanation

>[!important]
>An **important feature** of the theorem is that the right-hand side **does not depend on the dimension $n$**. 
>
>This inequality has served as a benchmark for the development of *concentration inequalities* during the last three decades. 



>[!important]
>Note that by **Gordon's inequality**
>$$
> \begin{align*}
> 1 - \Phi(t) &\le \left( \frac{1}{\sqrt{2\pi}} \right)\frac{1}{t} \exp \left( -\frac{t^2}{2} \right) = \frac{1}{t}\varphi(t)
> \end{align*}
>$$  
>
>The first Gaussian concentration inequality fails to capture the *corrective factor* $t^{-1}$. 








-----------
##  Recommended Notes and References


- [[Lipschitz Continuous Function]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Radon-Nikodym Derivative]]
- [[Cumulative Distribution Function of Random Variable]]

- [[Blowup of Sets]]

- [[Isoperimetry Problem in Probability Metric Space]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]