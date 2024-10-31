---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - optimal_transport_dual
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: Optimal Transport in Space of Measures Dual
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Dual Formulation of Optimal Transport Problem


>[!info] Recall
>Suppose 
>- $(X, \mathscr{F})$ and $(Y, \mathscr{G})$ are two *measurable topological spaces*. 
>- $\alpha: \mathscr{F} \to \mathbb{R}_{+}$ and $\beta: \mathscr{G} \to \mathbb{R}_{+}$ are two unsigned **Radon measures**. That is, 
>  $$
>  \alpha \in \mathcal{M}_{+}(X), \quad \beta \in \mathcal{M}_{+}(Y)
> $$
>- $c: X \times Y \to \mathbb{R}_{+}$ defines **the cost of transportation** from position $x\in X$ to position $y \in Y$.
>
>The **optimal transport** under *Kantorovich relaxation* is defined as finding an **optimal coupling** as a *Radon measure* on **joint space** $X \times Y$,
>$$
>\pi \in \mathcal{M}_{+}(X \times Y)
>$$
>such that that **average cost** of transporting measure $\alpha$ on $X$ to measure $\beta$ on $Y$ is **minimized**. 
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(X \times Y) } & \int_{X \times Y} c \;d \pi\\
\text{s.t. }&  P_{\#}^{X}\pi = \alpha \\
& P_{\#}^{Y}\pi = \beta
\end{align*}
>$$

- [[Optimal Transport in Space of Measures]]

>[!important] Dual Optimization Problem for Optimal Transport
>Given $\alpha \in \mathcal{M}_{+}(\mathcal{X})$ and $\beta \in \mathcal{M}_{+}(\mathcal{Y})$, and the cost function $c: X \times Y \to \mathbb{R}_{+}$.
>
>The **dual formulation** of the **optimal transport** is defined as the following 
>$$
>\begin{align*}
>\sup_{f \in \mathcal{BC}(\mathcal{X}), g \in \mathcal{BC}(\mathcal{Y})}\;&  \int_{\mathcal{X}} f \,d\alpha + \int_{\mathcal{Y}} g\, d\beta\\
>\text{s.t.}\;& f(x) + g(y) \le c(x, y), \quad \forall x \in \mathcal{X}, y \in \mathcal{Y} 
\end{align*}
>$$
>where $\mathcal{BC}(\mathcal{X})$ is the space of *bounded continuous functions* on $\mathcal{X}$. Similarly, for $\mathcal{BC}(\mathcal{Y})$.

- [[Space of Bounded Continuous Function]]
- [[Riesz-Markov Representation Theorem]]

## Explanation



>[!important] Proposition
>Suppose $\mathcal{X}$ and $\mathcal{Y}$ are both *compact Hausdorff spaces* and the cost function $c: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}_{+}$ is a *continuous function.*
> 
>Then there **exists a solution** $(f, g)$ for the *dual optimization* problem above. 
>
>And the **solution** has the form $f \in c\text{-conc}(\mathcal{X})$ and $g \in \bar{c}\text{-conc}(\mathcal{Y})$, and $g$ is the **c-transform (c-conjugate function)** of $f$, which is defined as 
>$$
>g(y) = f^c(y) := \inf_{x \in \mathcal{X}}\{ c(x, y) - f(x) \}, \;\forall y\in \mathcal{Y}.
>$$
>
>In particular, the optimal dual value can be obtained via 
>$$
>\begin{align*}
>\sup_{f \in c\text{-conc}(\mathcal{X})}\;&  \int_{\mathcal{X}} f \,d\alpha + \int_{\mathcal{Y}} f^c\, d\beta
\end{align*}
>$$

- [[C-Transform and C-Conjugate Function]]

>[!important] Definition
>The **optimal solution** $f^{*} \in c\text{-conc}(\mathcal{X})$ in above dual problem are called **Kantorovich potentials** for the optimal transport from $\alpha$ to $\beta$. 

- [[Variational Representation of Wasserstein Distance]]



-----------
##  Recommended Notes and References


- [[Optimal Transport in Discrete Setting]]

- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 311