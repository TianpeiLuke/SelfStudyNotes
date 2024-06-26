---
tags:
  - concept
  - math/functional_analysis
keywords:
  - delta_function
topics:
  - functional_analysis
name: Delta Function
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Delta Function

>[!info]
>Let $b\in \mathbb{R}$. Define a *linear functional* $\delta_{b}$ as 
>$$
> \delta_{b}(\varphi) = \varphi(b), 
>$$
>i.e. $\delta_{b}$ is an **evaluation functional**. 
>
>Since $$|\delta_{b}(\varphi)| \le \lVert \varphi \rVert_{0,0},$$
>we have $\delta_{b} \in \mathscr{S}'(\mathbb{R}).$
>
>Note that there exists **no function** $g$ so that 
>$$
>   \delta_{b}(\varphi)  := (\iota\,\delta_{b})(\varphi) = \int_{-\infty}^{+\infty} g(x)\,\varphi(x)\,dx
>$$
>even if there exists **point measure** $\mu_{b} := \delta_{b}$ so that 
>$$
> \delta_{b}(\varphi)  := (\iota\,\delta_{b})(\varphi) = \int_{-\infty}^{+\infty} \varphi(x)\,d\mu_{b}.
>$$

- [[Dirac Measure]]

>[!important] Definition
>We define the **delta function** at $b\in \mathbb{R}$ using the **symbolic expression** 
>$$
> \delta_{b}(\varphi)  = \int_{-\infty}^{+\infty} \varphi(x)\, \delta(x - b) \,dx.
>$$ 
>This above expression is not a valid integration.

- [[Evaluation Functional]]
- [[Riesz Representation Theorem]]

## Explanation


>[!important]
>The *delta function* $\delta(x - b)$ is just an *expression* for **evaluation functional** $\delta_{b} \in \mathscr{S}'(\mathbb{R})$ as a **tempered distribution**.





-----------
##  Recommended Notes and References



- [[Space of Tempered Distributions]]
- [[Space of Functions of Rapid Decrease and Schwartz Class]]

- [[Functional Analysis by Reed]]