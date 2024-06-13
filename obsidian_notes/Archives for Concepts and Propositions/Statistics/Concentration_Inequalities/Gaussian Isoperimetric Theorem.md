---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - gaussian_isoperimetric_theorem
topics:
  - concentration_inequality
name: Gaussian Isoperimetric Theorem
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Gaussian Isoperimetric Theorem


>[!important] Gaussian Concentration Theorem
> Let $\mathcal{N}$ be the **standard Gaussian measure** on $\mathbb{R}^n$ and let $A \in \mathscr{B}(\mathbb{R}^n)$ be a *Borel set*. 
> 
> Then
>$$  
> \begin{align}
> \liminf\limits_{t \to 0}\frac{\mathcal{N}(A_t) - \mathcal{N}(A)}{t} &\ge \gamma \left(\mathcal{N}(A)\right), 
> \end{align}
>$$  
>where $A_t := \set{x: d(x, A) < t}$ be the **$t$-blowup** of $A$ and $$\gamma(x) := \varphi \circ \Phi^{-1}(x)$$ is the **Gaussian isoperimetric function**.
>
>Moreover, if $A$ is a **half-space** defined by $$A := \set{x \in \mathbb{R}^n: x_1 \le z},$$ then the **equality holds** and
>$$
> \begin{align}
> \liminf\limits_{t \to 0}\frac{\mathcal{N}(A_t) - \mathcal{N}(A)}{t} &= \gamma\left(\mathcal{N}(A)\right) = \varphi(z),
> \end{align}
>$$   
>where $\varphi$ is the *density* of standard Gaussian measure.

^66aeb2

- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Gaussian Cumulative Distribution Function]]
- [[Gaussian Isoperimetric Function]]
- [[Blowup of Sets]]

## Equivalent to Gaussian Concentration Theorem

- [[Gaussian Concentration Theorem]]


>[!important]
>The **Gaussian concentration theorem** is **equivalent** to the **Gaussian isoperimetric theorem**.
>
>By *Gaussian concentration theorem*,  we can show that 
>$$
> \begin{align*}
> &\liminf\limits_{t \to 0}\frac{\mathcal{N}(A_t) - \mathcal{N}(A)}{t} \\
> &\ge \liminf\limits_{t \to 0}\frac{\Phi\left(\Phi^{-1}(\mathcal{N}(A)) + t\right) - \Phi\left(\Phi^{-1}(\mathcal{N}(A))\right) }{t} \\
> &= \Phi'\left(\Phi^{-1}(\mathcal{N}(A))\right) \\
> &= \varphi(\Phi^{-1}(\mathcal{N}(A))) \\
> &= \gamma(\mathcal{N}(A)).
> \end{align*}
>$$ 

- [[Gaussian Cumulative Distribution Function]]



-----------
##  Recommended Notes and References

- [[Gaussian Concentration Theorem]]

- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Radon-Nikodym Derivative]]
- [[Cumulative Distribution Function of Random Variable]]

- [[Blowup of Sets]]

- [[Isoperimetry Problem in Probability Metric Space]]

- [[Concentration Inequalities by Boucheron]]