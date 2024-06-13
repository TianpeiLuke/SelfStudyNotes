---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - gaussian_concentration_theorem
topics:
  - concentration_inequality
name: Gaussian Concentration Theorem
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Gaussian Concentration Theorem


>[!important] Gaussian Concentration Theorem
> Let $\mathcal{N}$ be the **standard Gaussian measure** on $\mathbb{R}^n$ and let $A \in \mathscr{B}(\mathbb{R}^n)$ be a *Borel set*. 
> 
> Then for all $t \ge 0$, 
> $$
> \begin{align}
> \mathcal{N}(A_t) &\ge \Phi\left(\Phi^{-1}\left(\mathcal{N}(A)\right) + t \right).  \\
> \end{align}
>$$  
>where $A_{t}$ is the **$t$-blow-up** of $A$ and $\Phi$ is the *cumulative distribution function* of $\mathcal{N}$.
>
>Equivalently
> $$
> \begin{align}
> \Phi^{-1}(\mathcal{N}(A_t) ) & \ge \Phi^{-1}\left(\mathcal{N}(A)\right) + t \nonumber
> \end{align}
>$$  
>Equality holds if $A$ is a **half-space**.

^e48f3e


- [[Gaussian Cumulative Distribution Function]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Blowup of Sets]]

## Equivalent to Gaussian Isoperimetric Theorem

- [[Gaussian Isoperimetric Theorem]]




-----------
##  Recommended Notes and References


- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Radon-Nikodym Derivative]]
- [[Cumulative Distribution Function of Random Variable]]

- [[Blowup of Sets]]

- [[Isoperimetry Problem in Probability Metric Space]]

- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]