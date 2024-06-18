---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - martingale_problem
topics:
  - stochastic_process
  - differential_equation
name: Martingale Problem
date of note: 2024-06-13
---

## Concept Definition

>[!important]
>**Name**: Martingale Problem


![[Infinitesimal Generator of Stochastic Differential Equation#^1bd4b1]]


>[!important] Definition
>The **martingale problem** *for the operator* $L$ is defined as follows:
>
>For each $x\in \mathbb{R}$, $s >0$, find a **probability measure** $$\mathcal{P}_{x,s}: = \mathcal{P}(\cdot| X(s) = x)$$ on $(\Omega, \mathscr{F})$ such that 
>- $$\mathcal{P}_{x,s}(X(u) =x, \; 0 \le u \le s)  = 1$$
>- For any twice differentiable function $f$ *vanishing outside a finite interval* the following process is a **martingale** under $\mathcal{P}_{x,s}$ with respect to $\mathcal{F}_{t}$
>$$
>f\left(X(t)\right) - \int_{s}^{t}\,\left(L\,f\right)\left(X(u)\right)\,du
>$$
>
>If there exists *exactly one solution* to the martingale problem, it is said that the martingale problem is **well-posed**.

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Martingale]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 141

## Explanation




## Construction of Weak Solution to SDE

- [[Construction of Weak Solution to SDE]]



-----------
##  Recommended Notes and References

- [[Weak Solution to Stochastic Differential Equation]]

- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]

- [[Markov Transition Kernel and Transition Function]]


- [[Introduction to Stochastic Calculus by Klebaner]]