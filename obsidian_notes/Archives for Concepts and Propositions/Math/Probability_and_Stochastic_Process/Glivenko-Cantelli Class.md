---
tags:
  - concept
  - math/stochastic_process
  - math/probability
  - math/functional_analysis
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - glivenko-cantelli_class
topics:
  - stochastic_process
  - concentration_inequality
  - probability
  - functional_analysis
  - machine_learning_theory
name: Glivenko-Cantelli Class
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Glivenko-Cantelli Class

![[Empirical Process and Empirical Measure#^c35b40]]

- [[Empirical Process and Empirical Measure]]


>[!important] Definition
>A family of functions $\mathcal{F}$ is a **Glivenko-Cantelli class** for $\mathcal{P}$ if 
>$$
> \begin{align*}
>  \lVert \mathcal{P}_{n} - \mathcal{P} \rVert_{\mathcal{F}}  &:= \sup_{f \in \mathcal{F}}\; \lvert \mathcal{P}_{n}f - \mathcal{P}f \rvert\; \stackrel{\mathcal{P}}{\longrightarrow} 0
> \end{align*}
>$$ 
> as $n \to \infty$. 

- [[Convergence in Measure]]

>[!important] Definition
>A family of functions $\mathcal{F}$ is a **strong Glivenko-Cantelli class** for $\mathcal{P}$ if 
>$$
> \begin{align*}
>  \lVert \mathcal{P}_{n} - \mathcal{P} \rVert_{\mathcal{F}}  &:= \sup_{f \in \mathcal{F}}\; \lvert \mathcal{P}_{n}f - \mathcal{P}f \rvert\; \stackrel{a.s.}{\longrightarrow} 0
> \end{align*}
>$$ 
> as $n \to \infty$. 

- [[Pointwise Almost Everywhere Convergence]]
- [[Glivenko-Cantelli Theorem]]

## Explanation

>[!important]
>According to [[Glivenko-Cantelli Theorem]], the family of *indicator functions*
>$$
>\mathcal{F} := \left\{ \mathbb{1}_{(-\infty\,,\, z\,]}(\cdot), \quad z\in \mathbb{R} \right\} 
>$$
>is a **strong Gilvenko-Cantelli class** for $\mathcal{P}$.

>[!info]
>If the **empirical measure** $\mathcal{P}_{n}$ *converge* to $\mathcal{P}$ under **weak$^{*}$ topology** of dual space of $\mathcal{F}^{*}$
>$$
>\mathcal{P}_{n} \stackrel{w}{\rightarrow} \mathcal{P}
>$$
>then $\mathcal{F}$ is a **strong Glivenko-Cantelli class**

- [[Weak-star Topology of Banach Space]]
- [[Weak Convergence in Banach Space]]
- [[Convergence in Distribution]]



-----------
##  Recommended Notes and References

- [[Pointwise Almost Everywhere Convergence]]
- [[Convergence in Measure]]
- [[Empirical Process and Empirical Measure]]
- [[Glivenko-Cantelli Theorem]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]