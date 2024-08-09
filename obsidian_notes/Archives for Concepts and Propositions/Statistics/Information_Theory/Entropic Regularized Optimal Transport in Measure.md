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
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: entropic regularized optimal transport
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Entropic Regularized Optimal Transport

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
>- The *optimal transport* is defined as the following **optimization problem** on the *space of all Radon measures*:
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(X \times Y) } & \int_{X \times Y} c \;d \pi\\
\text{s.t. }&  P_{\#}^{X}\pi = \alpha \\
& P_{\#}^{Y}\pi = \beta
\end{align*}
>$$  

- [[Optimal Transport in Space of Measures]]
- [[Product Measure]]
- [[Fubini Theorem]]
- [[Space of Bounded Signed Measures]]

>[!important]
>This section introduces a family of numerical schemes to approximate solutions to *Kantorovich formulation* of **optimal transport** and its many generalizations. It operates by adding an **entropic regularization penalty** to the original problem. This regularization has several important advantages:
> - the minimization of the regularized problem can be solved using a simple **alternate minimization** scheme, which only required matrix-vector multiplication, 
> 
> - the resulting approximate distance is **smooth** with respect to input histogram weights and positions of the Diracs and can be differentiated using **automatic differentiation**.

- [[Tikhonov Regularization in Optimization and Learning]]
- [[Automatic Differentiation]]

>[!important] Definition
>We introduce the **entropic regularization** term to the primal problem:
>$$
> \begin{align}
> \mathbb{KL}\left( \pi \left\|\right. \alpha \otimes \beta \right) &:= \int_{X \times Y}   \log \left(\frac{d \pi}{d \alpha \otimes d \beta}\right)  d \pi +   \int_{X \times Y} \left(d \alpha \otimes d \beta - d \pi \right)
> \end{align}
>$$

- [[Kullback-Leibler Divergence]]
- [[Product Measure]]
- [[Fubini Theorem]]
- [[Mutual Information]]


>[!important] Definition
>The above is called the **mutual information** 
>$$I(X; Y) := \mathbb{KL}\left( \pi \left\|\right. \alpha \otimes \beta \right),$$
>where $\pi$ is the joint distribution of $(X, Y)$, and $\alpha$, and $\beta$ are the marginal distributions of $X$ and $Y$, respectively.

- [[Mutual Information]]

>[!important] Entropic-Regularized Optimal Transport (Measure)
>The **entropic-regularized optimal transport** is formulated as the following convex optimization problem
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(X \times Y) } & \int_{X \times Y} c \;d \pi + \lambda   \int_{X \times Y}   \log \left(\frac{d \pi}{d \alpha \otimes d \beta}\right)  d \pi + \lambda \int_{X \times Y} \left(d \alpha \otimes d \beta - d \pi \right)  \\
\text{s.t. }&  P_{\#}^{X}\pi = \alpha \\
& P_{\#}^{Y}\pi = \beta
\end{align*}
>$$

- [[Product Measure]]

>[!important] Entropic-Regularized Optimal Transport (Probability)
>The **entropic-regularized optimal transport** is reformulated for the space of probability measures $(X, Y) \sim \pi$:
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y})}& \mathbb{E}_{(X,Y) \sim \pi}\left[ c(X, Y) \right]  + \lambda \; I(X; Y)  \\
\text{s.t. }&  X \sim \alpha \\
& Y \sim \beta
\end{align*}
>$$


## Explanation







-----------
##  Recommended Notes and References


- [[Tikhonov Regularization in Optimization and Learning]]

- [[Product Measure]]

- [[Optimal Transport in Space of Measures]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]