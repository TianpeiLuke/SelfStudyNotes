---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - optimal_transport
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: Optimal Transport in Space of Measures
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Optimal Transport as Optimization on Space of Radon Measures


>[!important] Optimal Transport (Measure Space) 
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
>such that that **average cost** of transporting measure $\alpha$ on $X$ to measure $\beta$ on $Y$ is **minimized**. The average transportation cost is defined as 
>$$
>\int_{X \times Y} c \;d \pi
>$$

- [[Radon Measure]]
- [[Product Measure]]
- [[Fubini Theorem]]


>[!important] Optimal Transport (Optimization on Space of Radon Measures) 
>The **optimal transport** is defined as the following **optimization problem** on the *space of all Radon measures*:
>$$
>\begin{align*}
>\inf_{\pi \in \mathcal{M}_{+}(X \times Y) } & \int_{X \times Y} c \;d \pi\\
\text{s.t. }&  P_{\#}^{X}\pi = \alpha \\
& P_{\#}^{Y}\pi = \beta
\end{align*}
>$$
>where $P^{X}: X \times Y \to X$ is the *canonical projection* onto the first coordinate, $$P^{X}(x, y) = x.$$ 
>Similarly, $P^{Y}: X \times Y \to Y$ is the *canonical projection* onto the second coordinate, $$P^{Y}(x, y) = y.$$ 
>Both $P^{X}$ and $P^{Y}$ are measurable function on $\mathcal{M}_{+}(X \times Y).$

- [[Measurable Function]]
- [[Canonical Projection]]
- [[Fubini Theorem]]

>[!important]
>$P_{\#}^{X}\pi$ is called the **push-forward measure** of $\pi$ by $P^X$, which is defined as
>$$
>(P_{\#}^{X}\pi)(A) := \pi \circ (P^X)^{-1}(A) = \pi(\{(x,y) \in X\times Y: x\in A \}), \quad \forall A \in \mathscr{X}
>$$
>Similarly, $P_{\#}^{Y}\pi$ is called the **push-forward measure** of $\pi$ by $P^Y$,
>$$
>(P_{\#}^{Y}\pi)(B) := \pi \circ (P^Y)^{-1}(B) = \pi(\{(x,y)\in X\times Y: y\in B \}), \quad \forall B \in \mathscr{Y}
>$$

- [[Push-forward Measure and Push-forward Operator]]
- [[Product Measure]]
- [[Fubini Theorem]]

>[!important]
>Define $\mathcal{L}_{c}(\alpha, \beta)$ be the optimal value of the above optimal transport problem. 


## Optimal Transport between Probability Measures

>[!important] Optimal Transport (Optimization on the Space of Joint Probability) 
>Let the coupling $\pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y})$ is the **joint probability measure** of  $(X, Y)$ over $\mathcal{X} \times \mathcal{Y}$ and $\alpha$ and $\beta$ be the **distribution** of $X$ on space $\mathcal{X}$ and $Y$ on space $\mathcal{Y}$, respectively. 
>
>The **optimal transport** problem can be formulated as
>$$
> \begin{align}
> \inf_{\pi \in \mathcal{M}_{+}(\mathcal{X} \times \mathcal{Y})}& \mathbb{E}_{(X,Y) \sim \pi}\left[ c(X, Y) \right]  \\
> \text{s.t. }&  X \sim \alpha,  \nonumber \\
> & Y\sim \beta  \nonumber
> \end{align}
>$$ 
>where  $X \sim \alpha$ means that the random variable $X$ has **(marginal) distribution** $\alpha$. Similarly,  $Y \sim \beta$ means that the random variable $Y$ has **(marginal) distribution** $\beta$.

- [[Probability Space]]
- [[Fubini Theorem]]


>[!info]
>- For simplicity, we define _the space of all **coupling**_ as a space of unsigned Radon measures on $X \times Y$ whose marginal measure is $\alpha$ and $\beta$ 
>  $$
>  \Gamma_{+}(\alpha, \beta) := \left\{ \pi \in \mathcal{M}_{+}(X \times Y): P_{\#}^X \pi = \alpha, \; P_{\#}^{Y} \pi = \beta  \right\}
> $$ 

- [[Product Measure]]


## Explanation












-----------
##  Recommended Notes and References

- [[Product Measure]]

- [[Optimal Transport in Discrete Setting]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]