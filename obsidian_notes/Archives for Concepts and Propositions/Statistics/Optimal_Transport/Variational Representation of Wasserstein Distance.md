---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - wasserstein_distance_dual
  - variational_inference
topics:
  - information_theory
  - information_geometry
  - optimization
  - functional_analysis
  - optimal_transport
name: Dual Representation of Wasserstein Distance
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Dual Representation of Wasserstein Distance

>[!info] Recall the setting
>Suppose 
>- $(\mathcal{X}, \mathscr{F})$ and $(\mathcal{Y}, \mathscr{G})$ are two *measurable topological spaces*. 
>- $\alpha: \mathscr{F} \to \mathbb{R}_{+}$ and $\beta: \mathscr{G} \to \mathbb{R}_{+}$ are two unsigned *Radon probability measures*. That is, 
>  $$
>  \alpha \in \mathcal{M}_{+}(\mathcal{X}), \quad \beta \in \mathcal{M}_{+}(\mathcal{Y})
> $$
>- The space of all **coupling** is a space of unsigned Radon measures on $\mathcal{X} \times \mathcal{Y}$ whose marginal measure is $\alpha$ and $\beta$ 
>  $$
>  \Gamma_{+}(\alpha, \beta) := \left\{ \pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y}): P_{\#}^{\mathcal{X}} \pi = \alpha, \; P_{\#}^{\mathcal{Y}} \pi = \beta  \right\}
> $$ 
>- $c: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}_{+}$ defines **the cost of transportation** from position $x\in \mathcal{X}$ to position $y \in \mathcal{Y}$.
>- For Wasserstein distance, we assume $\mathcal{X}=\mathcal{Y}$ and is a *metric space* $(\mathcal{X}, d)$.


>[!info]
>for $p \ge 1$, the **$p$-Wasserstein distance**  between measures $\alpha, \beta \in \mathcal{M}_{+}(\mathcal{X})$ is defined as 
>$$
>\begin{align*}
>\mathcal{W}_{p}(\alpha, \beta) := \left(\inf_{\pi \in \mathcal{G}_{+}(\alpha, \beta)} \mathbb{E}_{(X,Y) \sim \pi}\left[ (d(X, Y))^p \right]  \right)^{1/p}
>\end{align*}
>$$
>
>Consider $p=1$, then $1$-Wasserstein distance is
>$$
>\mathcal{W}_{1}(\alpha, \beta) := \inf_{\pi \in \mathcal{G}_{+}(\alpha, \beta)} \mathbb{E}_{(X,Y) \sim \pi}\left[ d(X, Y) \right]  
>$$

- [[Optimal Transport in Space of Measures]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]


>[!important] Dual Representation of $\mathcal{W}_{1}$
>Suppose $\mathcal{X}$  is a **separable complete metric space**  (**Polish space**) with metric $d: \mathcal{X} \times \mathcal{X} \to \mathbb{R}_{+}$.  Let $\alpha, \beta \in \mathcal{M}_{+}(\mathcal{X})$  be *unsigned Radon measures*. Assume that $\alpha$ and $\beta$ both have *bounded supports*.
>
>The **dual representation** of the $1$-Wasserstein distance is
>$$
>\begin{align*}
>\mathcal{W}_{1}(\alpha, \beta) &= \sup\left\{ \int_{\mathcal{X}}f\;d\alpha -  \int_{\mathcal{X}}f\;d\beta:  \;\forall f \in \mathcal{C}(\mathcal{X}) \text{ with } \text{Lip}(f) \le 1 \right\}
\end{align*}
>$$
>where $\mathcal{C}(\mathcal{X})$ is the space of all *real-valued continuous functions* on $\mathcal{X}$ and $\text{Lip}(f)$ is the *best Lipschitz constant*
>$$
>\text{Lip}(f) := \min\{K: d_{\mathbb{R}}(f(x), f(y)) \le K\,d(x, y), \forall x, y \in \mathcal{X} \}
>$$

- [[Variational Formulation of Optimal Transport]]
- [[Lipschitz Continuous Function]]
- [[Riesz-Markov Representation Theorem]]


## Explanation

>[!info]
>The condition $\text{Lip}(f) \le 1$ implies that $f: \mathcal{X} \to \mathbb{R}$ is **contraction-like map**.

- [[Contraction Function]]


>[!info]
>By [[Riesz-Markov Representation Theorem]], there exists an *one-to-one correspondence* 
>$$
>\alpha \mapsto I_{\alpha} := \int_{\mathcal{X}} \cdot\, d\alpha
>$$
>on the space of *continuous functions* with compact support. 
>
>It makes sense to see that **the difference of linear functionals** with respect to **different measures** can be used to define *the distance between these measures.*
>
>In the case of Wasserstein distance, the linear functionals are defined on space of **Lipschitz continuous functions.**


>[!important]
>The **functional interpretation** of the dual representation can be seen as:
>$$
>\mathcal{W}_{1}(\alpha, \beta) := \sup_{f \in \mathcal{C}_{Lip}(\mathcal{X})}\left\{ I_{\alpha}(f) - I_{\beta}(f)  \right\}
>$$
>where for any $\mu \in \mathcal{M}_{+}(\mathcal{X})$,  the functional $I_{\mu}:\mathcal{C}(\mathcal{X}) \to \mathbb{R}$ is defined as 
>$$
>I_{\mu}(f) := \int_{\mathcal{X}} f d\mu
>$$
>and $\mathcal{C}_{Lip}(\mathcal{X})$ is the space of Lipschitz continuous functions.


## Proof













-----------
##  Recommended Notes and References

- [[Optimal Transport in Discrete Setting]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]

- [[Empirical Process and Empirical Measure]]