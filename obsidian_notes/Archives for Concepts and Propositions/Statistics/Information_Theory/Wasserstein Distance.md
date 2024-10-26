---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - wasserstein_distance
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: Wasserstein Distance
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Wasserstein Distance

>[!info] Recall the setting
>Suppose 
>- $(\mathcal{X}, \mathscr{F})$ and $(\mathcal{Y}, \mathscr{G})$ are two *measurable topological spaces*. 
>- $\alpha: \mathscr{F} \to \mathbb{R}_{+}$ and $\beta: \mathscr{G} \to \mathbb{R}_{+}$ are two unsigned *Radon probability measures*. That is, 
>  $$
>  \alpha \in \mathcal{M}_{+}(\mathcal{X}), \quad \beta \in \mathcal{M}_{+}(\mathcal{Y})
> $$
>- $c: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}_{+}$ defines **the cost of transportation** from position $x\in \mathcal{X}$ to position $y \in \mathcal{Y}$.

- [[Space of Bounded Signed Measures]]

>[!info]
>The optimal value of **optimal transport** is defined as 
>$$
>\begin{align*}
>\mathcal{L}_{c}(\alpha, \beta) := \min_{\pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y})}& \mathbb{E}_{(X,Y) \sim \pi}\left[ c(X, Y) \right]  \\
> \text{s.t. }&  X \sim \alpha,  \nonumber \\
> & Y\sim \beta  \nonumber
>\end{align*}
>$$

- [[Optimal Transport in Discrete Setting]]
- [[Optimal Transport in Space of Measures]]

>[!important] Definition
>Suppose $\mathcal{X} = \mathcal{Y}$  is a **metric space** with metric $d: \mathcal{X} \times \mathcal{X} \to \mathbb{R}_{+}$. Let $\mathcal{L}_{c}(\alpha, \beta)$ be *the optimal value* of the optimal transport problem above. 
>
>Then for $p \ge 1$, the **$p$-Wasserstein distance**  between measures $\alpha, \beta \in \mathcal{M}_{+}(\mathcal{X})$ is defined as 
>$$
>\mathcal{W}_{p}(\alpha, \beta) := L^{d^{p}}(\alpha, \beta)^{\frac{1}{p}},
>$$ 
>where $c(x, y) := (d(x, y))^p$ for all $x, y \in \mathcal{X}$.

- [[Metric Space]]
- [[Radon Measure]]

>[!info]
>for $p \ge 1$, the **$p$-Wasserstein distance**  between measures $\alpha, \beta \in \mathcal{M}_{+}(\mathcal{X})$ is defined as 
>$$
>\begin{align*}
>\mathcal{W}_{p}(\alpha, \beta)^p := \inf_{\pi \in \mathcal{G}_{+}(\alpha, \beta)}& \mathbb{E}_{(X,Y) \sim \pi}\left[ (d(X, Y))^p \right]  
>\end{align*}
>$$
>where
>$$
>  \Gamma_{+}(\alpha, \beta) := \left\{ \pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y}): P_{\#}^{\mathcal{X}} \pi = \alpha, \; P_{\#}^{\mathcal{Y}} \pi = \beta  \right\}
>$$ 
>Consider $p=1$, then $1$-Wasserstein distance is
>$$
>\mathcal{W}_{1}(\alpha, \beta) := \inf_{\pi \in \mathcal{G}_{+}(\alpha, \beta)} \mathbb{E}_{(X,Y) \sim \pi}\left[ d(X, Y) \right]  
>$$

## Explanation

>[!info] 
>We can confirm that $\mathcal{W}_{p}(\alpha, \beta)$ is a valid **metric** between $\alpha, \beta \in \mathcal{M}_{+}(\mathcal{X})$, i.e. 
> 
> - **Symmetric**: for all $\alpha, \beta \in  \mathcal{M}_{+}(\mathcal{X})$, 
>   $$\mathcal{W}_{p}(\alpha, \beta) = \mathcal{W}_{p}( \beta, \alpha)$$
> - **Definiteness**: $$\mathcal{W}_{p}(\alpha, \beta) = 0, \text{ iff } \alpha = \beta$$
> - **Triangular inequality**:  for all $\alpha, \beta, \gamma \in \mathcal{M}_{+}(\mathcal{X})$. 
>   $$\mathcal{W}_{p}(\alpha, \beta)  \le \mathcal{W}_{p}(\alpha, \gamma)  + \mathcal{W}_{p}(\gamma, \beta).$$
> 
> Note that the first two are trivial. Only triangular inequality need to be verified.
  

>[!important] Proposition
>The quantity $\mathcal{W}_{p}$ defined above is a **metric** over $\mathscr{P}_{p}(\mathcal{X})$ where 
>$$
>\mathscr{P}_{p}(\mathcal{X}) := \left\{ \mu \in \mathcal{M}_{+}(\mathcal{X}): \int_{\mathcal{X}} |x|^p d\mu < \infty  \right\} \subset \mathcal{M}_{+}(\mathcal{X})
>$$

>[!important] Definition
>Given a **Polish space** $X$, for each $p \ge 1$, we define a **Wasserstein space** of *order $p$*, called $\mathbb{W}_{p}(\mathcal{X})$, as the space $\mathscr{P}_{p}(\mathcal{X})$, endowed with *the metric* $\mathcal{W}_{p}.$

>[!info]
>Wasserstein space is a **_metric_ space of measures**.

- [[Wasserstein Space]]


## Dual Representation of $\mathcal{W}_{1}$

- [[Variational Representation of Wasserstein Distance]]





-----------
##  Recommended Notes and References


- [[k-Means Clustering]]
- [[Optimal Transport in Discrete Setting]]


- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]]
