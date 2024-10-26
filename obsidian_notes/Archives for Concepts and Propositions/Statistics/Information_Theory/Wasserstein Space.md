---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
keywords:
  - wasserstein_space
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: Wasserstein Space
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Wasserstein Space

>[!info] Recall the setting
>Suppose 
>- $(X, \mathscr{F}, d)$ is a *measurable topological spaces* with metric $d$.
>- $\alpha$ and $\beta$ are two unsigned *Radon probability measures*. That is, 
>  $$
>  \alpha \in \mathcal{M}_{+}(X), \quad \beta \in \mathcal{M}_{+}(Y)
> $$
>- $\mathcal{M}_{+}(X)$ is *the space of all probability measures* on $X$.
>- Let $\mathcal{L}_{c}(\alpha, \beta)$ be *the optimal value* of the optimal transport problem above, moving probability measure $\alpha \in \mathcal{M}_{+}(X)$ to a probability measure $\beta \in \mathcal{M}_{+}(Y)$ with cost function $c: X \times X \to \mathbb{R}_{+}$. 
>
>- Then for $p \ge 1$, the **$p$-Wasserstein distance**  between measures $\alpha, \beta \in \mathcal{M}_{+}(X)$ is defined as 
>$$
>\mathcal{W}_{p}(\alpha, \beta) := L^{d^{p}}(\alpha, \beta)^{\frac{1}{p}}
>$$ 
>where $c(x, y) := (d(x, y))^p$ for all $x, y \in X$.

- [[Space of Bounded Signed Measures]]
- [[Wasserstein Distance]]

>[!important] Definition
>Given a **Polish space** $X$, for each $p \ge 1$, the quantity $\mathcal{W}_{p}$ defined above is a **metric** over a bounded space $\mathscr{P}_{p}(X)$ where 
>$$
>\mathscr{P}_{p}(X) := \left\{ \mu \in \mathcal{M}_{+}(X):  \int_{X} |x|^p d\mu < \infty  \right\} \subset \mathcal{M}_{+}(X).
>$$
>
>The *metric space* $(\mathscr{P}_{p}(X), \mathcal{W}_{p})$ is called a **Wasserstein space** of **order $p$**. 
>
>It is denoted as  $\mathbb{W}_{p}(X)$.

- [[Metric Space]]
- [[Radon Measure]]


## Explanation

>[!info]
>Wasserstein space is a **_metric_ space of measures**.

## Weak Convergence

>[!important]
>A sequence of *measures* $\left\{ \mu_{n} \right\}$ *converges* to $\mu$ with respect to the **Wasserstein metric** is equivalent to **weak$^{*}$ (vague) convergence** of $\mu_{n}$ to $\mu$.
>
>$$
>\mu_{n} \stackrel{\mathcal{W}_{p}}{\longrightarrow} \mu \implies \mu_{n} \stackrel{d}{\longrightarrow} \mu
>$$
>For the pushforward measure $\mu_{n} = (X_{n})_{*}\mathcal{P}$, it is equivalent to **convergence in distribution**
>$$
>\mu_{n} \stackrel{\mathcal{W}_{p}}{\longrightarrow} \mu \iff X_{n} \stackrel{d}{\longrightarrow} X \text{ and } X_{n} \stackrel{L^p}{\longrightarrow} X
>$$


- [[Weak-star Topology of Banach Space]]
- [[Convergence in Distribution]]
- [[Push-forward Measure and Push-forward Operator]]




-----------
##  Recommended Notes and References

- [[Optimal Transport in Discrete Setting]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]]