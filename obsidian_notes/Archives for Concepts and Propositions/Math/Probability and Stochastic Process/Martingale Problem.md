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
>For each $x\in \mathbb{R}$, $s >0$, find a **probability measure** $\mathcal{P}_{x,s}$ on $(\Omega, \mathscr{F})$ such that 
>- $$\mathcal{P}_{x,s}(X(u) =x, \; 0 \le u \le s)  = 1$$
>- For any twice differentiable function $f$ *vanishing outside a finite interval* the following process is a **martingale** under $\mathcal{P}_{x,s}$ with respect to $\mathcal{F}_{t}$
>$$
>f\left(X(t)\right) - \int_{s}^{t}\,\left(L\,f\right)\left(X(u)\right)\,du
>$$
>
>If there exists *exactly one solution* to the martingale problem, it is said that the martingale problem is **well-posed**.

- [[Markov Chain and Markov Process]]
- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Martingale]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 141

>[!info]
>The first condition of the martingale problem states that the system **fixed** at a **constant initial state** $x$ *before* $s$.

## Explanation





## Martingale Problem associated with Solution of SDE and Backward Equation


![[Martingale via Solution of SDE and Backward Equation#^c8ae3e]]

![[Martingale via Solution of SDE and Backward Equation#^76bb2e]]

- [[Martingale via Solution of SDE and Backward Equation]]

>[!important]
>The above two theorems show that the **distribution** of a **weak solution of SDE**, $X_{t}$, solves the **Martingale problem**.
>
>The followings shows how to construct such weak solution.

- [[Weak Solution to Stochastic Differential Equation]]

## Construction of Weak Solution to SDE

>[!important] Definition
>A **weak solution** to the SDE
>$$
>\begin{align*}
> dX(t) &= \mu \left(X(t), t\right)\,dt + \sigma\left(X(u), u\right)\,dW
>\end{align*}
>$$
>is defined as a *solution* to **the martingale problem**.

- [[Construction of Weak Solution to SDE]]






-----------
##  Recommended Notes and References

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Weak Solution to Stochastic Differential Equation]]

- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]

- [[Markov Transition Kernel and Transition Function]]


- [[Introduction to Stochastic Calculus by Klebaner]]