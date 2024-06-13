---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - entropy_functional
topics:
  - information_theory
  - concentration_inequality
name: Entropy Functional
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Entropy Functional

>[!important] Definition
>The **entropy functional** $\text{Ent}: \Omega \to \mathbb{R}$ is defined by
>$$
>\text{Ent}\left(f\right) := \int_{\mathcal{X}}f\,\log(f) d\mu - \left( \int_{\mathcal{X}}f\,d\mu \right) \;\log \left( \int_{\mathcal{X}}f\, d\mu \right),
>$$
>where the *domain* $\Omega$ of the functional is defined as
>$$
>\Omega := \left\{ f \in L^1(\mathcal{X}, \mu): f \ge 0 \right\}.
>$$

- [[Convex Function]]
## Explanation


>[!info]
>Note that $\Phi(x) = x \log x$ is convex function. From  [[Jensen Inequality]],
>$$
>\text{Ent}(f) := \int \Phi(f) d\mu - \Phi \left(\int f d\mu\right) \ge 0.
>$$


>[!info]
>We can define $f$ as the **Radon-Nikodym derivative**
>$$
>f := \frac{d\mathcal{P}}{d\mu}
>$$
>where $\mathcal{P} \ll \mu$ is some probability measure. $f$ is the *density function* of $\mathcal{P}$ w.r.t. base measure $\mu$.
>
>Then 
>$$
>\begin{align*}
>\text{Ent}\left(f\right) &:= \int_{\mathcal{X}}f\,\log(f) d\mu - \left( \int_{\mathcal{X}}f\,d\mu \right) \;\log \left( \int_{\mathcal{X}}f\, d\mu \right)\\
>&= \int_{\mathcal{X}}\frac{d\mathcal{P}}{d\mu}\,\log \left( \frac{d\mathcal{P}}{d\mu} \right) d\mu - \left( \int_{\mathcal{X}}\frac{d\mathcal{P}}{d\mu}\,d\mu \right) \;\log \left( \int_{\mathcal{X}}\frac{d\mathcal{P}}{d\mu}\, d\mu \right)\\
>&= \int_{\mathcal{X}}\log \left( \frac{d\mathcal{P}}{d\mu} \right) d\mathcal{P}\\[10pt]
>&= \mathbb{KL}\left( \mathcal{P} \left\|\right. \mu \right)
\end{align*}
>$$
>where 
>$$
>\int \frac{d\mathcal{P}}{d\mu} d\mu = \int d\mathcal{P} = 1,
>$$ 
>and $1 \log(1) = 0.$
>
>This is the **origin** of the name **"entropy"**.

- [[Radon-Nikodym Derivative]]
- [[Kullback-Leibler Divergence]]





-----------
##  Recommended Notes and References


- [[Kullback-Leibler Divergence]]



- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]