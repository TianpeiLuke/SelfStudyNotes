---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - entropic_regularization
  - optimal_transport
  - dual_formulation
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: entropic regularized optimal transport in dual form
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Entropic Regularized Optimal Transport via Dual Formulation

>[!info] Recall the setting
>Suppose 
>- $(X, \mathscr{F}, d)$ is a *measurable topological spaces* with metric $d$.
>- $\alpha$ and $\beta$ are two unsigned *Radon probability measures*. That is, 
>  $$
>  \alpha \in \mathcal{M}_{+}(X), \quad \beta \in \mathcal{M}_{+}(Y)
> $$
>- $\mathcal{M}_{+}(X)$ is *the space of all probability measures* on $X$.
>- $P^{X}$ and $P^{Y}$ are *canonical projections* from $X \times Y$ onto $X$ and $Y$, respectively.
>- $P^{X}_{\#}\pi$ and  $P^{Y}_{\#}\pi$ are *push-forward measures* of $\pi$ by projections above.

>[!info] Entropic-Regularized Optimal Transport (Measure)
>The **entropic-regularized optimal transport** is formulated as the following convex optimization problem
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(X \times Y) } & \int_{X \times Y} c \;d \pi + \lambda   \int_{X \times Y}   \log \left(\frac{d \pi}{d \alpha \otimes d \beta}\right)  d \pi  + \lambda \int_{X \times Y} \left(d \alpha \otimes d \beta - d \pi \right) \\
\text{s.t. }&  P_{\#}^{X}\pi = \alpha \\
& P_{\#}^{Y}\pi = \beta
\end{align*}
>$$

- [[Entropic Regularized Optimal Transport in Measure]]

>[!important] Dual Form of Entropic-Regularized Optimal Transport (Measure)
>The **entropic-regularized optimal transport** is reformulated by the *dual form* of convex optimization problem
>$$
\begin{align}
\sup_{(\mu,\nu) \in \mathcal{C}(X) \times \mathcal{C}(Y)} & \int_{X}\mu\, d\alpha  + \int_{Y}\nu \, d\beta  - \lambda \int_{X \times Y} \left(\exp\left(\frac{-c + \mu \oplus \nu}{\lambda}\right) - 1\right)\; d\alpha \, d\beta,  
\end{align} 
>$$
>where $(\mu \oplus \nu)(x, y) = \mu(x) + \nu(y)$ and $\mathcal{C}(X)$ is *the spaces of continuous functions* on $X$; similarly for $\mathcal{C}(Y)$.

>[!important] Dual Form of Entropic-Regularized Optimal Transport (Probability)
>The **dual form** of **entropic-regularized optimal transport** can be interpreted in probability space
>$$
\begin{align}
\sup_{(\mu,\nu) \in \mathcal{C}(X) \times \mathcal{C}(Y)} & \mathbb{E}_{X \sim \alpha}\left[ \mu(X) \right]   + \mathbb{E}_{Y \sim \beta}\left[ \nu(Y) \right]   - \lambda \,\mathbb{E}_{ (X,Y) \sim \alpha \otimes \beta }\left[ \exp\left(\frac{-c(X, Y) + \mu(X) + \nu(Y)}{\lambda}\right) - 1 \right],
\end{align} 
>$$
>


## Proof




## Explanation










-----------
##  Recommended Notes and References

- [[Tikhonov Regularization in Optimization and Learning]]
- [[Optimal Transport in Space of Measures]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]