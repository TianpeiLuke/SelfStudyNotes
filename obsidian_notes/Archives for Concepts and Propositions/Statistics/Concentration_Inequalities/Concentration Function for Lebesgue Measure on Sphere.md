---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - isoperimetry_theorem
  - uniform_sphere
topics:
  - concentration_inequality
name: Isoperimetric Inequalities for Uniform Distribution over Sphere
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Isoperimetric Inequalities for Uniform Distribution over Sphere

>[!important] Isoperimetric Inequalities for Uniform Distribution over Sphere
>Let $\mathbb{S}^{n - 1}$ be the $(n-1)$-dimensional **unit sphere**.  
>$$\mathbb{S}^{n - 1}=  \set{x \in \mathbb{R}^n: \lVert x \rVert  = 1}$$
>
>For any $t\in [0, 1]$, 
>$$
> \begin{align}
> \alpha_{\mathbb{S}^{n-1}}(t) &\le c \exp \left( -\frac{n t^2}{2} \right) 
> \end{align}
>$$  
>for some constant $c$.

^0898b2

- [[Concentration Function for Metric Measure Space]]
- [[Lebesgue Measure]]


>[!important] Proposition
>For any **$1$-Lipschitz function** $f$ defined on the sphere $\mathbb{S}^{n-1}$, we have the two-sided bound
>$$
> \begin{align}
> \mathcal{P}\set{\,\lvert f(Z) -  \text{med}(f(Z))\rvert\, \ge t} &\le \sqrt{2\pi}\exp\left(-\frac{n t^2}{2}\right)
> \end{align}
>$$  
>Moreover, replacing *median* by the *mean*, we have 
>$$
> \begin{align}
> \mathcal{P}\set{\,\lvert f(Z) - \mathbb{E}\left[ f(Z)\right] \rvert\,  \ge t} &\le 2\sqrt{2\pi}\exp\left( -\frac{n t^2}{8} \right)
> \end{align}
>$$ 

- [[Lipschitz Continuous Function]]

## Explanation




## Blow-Up Phenomenon in High Dimensional Sphere

>[!example] Blow-up Phenomenon
>Let $A$ be a subset of the sphere $\sqrt{n}\, \mathbb{S}^{n-1}$ such that
>$$
> \begin{align*}
> \mathcal{P}(A) > 2 \exp(-c s^2) \quad \text{ for some }s > 0;
> \end{align*}
>$$ 
>
>- Prove that $\mathcal{P}(A_s) > 1/2$.
>- Deduce from this that for any $t \ge s$,
>$$  
> \begin{align*}
> \mathcal{P}\left( A_{2t} \right) > 1 - 2 \exp(-c t^2).
> \end{align*}
>$$  
>Here $c > 0$ is the absolute constant in upper bound of concentration function.
>
>This statement said that for a *small surface area* on $n$-sphere, a *small incremental step* in *all directions* of the *boundary* will lead to a *significant increase* in terms of surface area.

>[!important]
>The **blow-up phenomenon** we just saw may be quite **counter-intuitive** at first sight. 
>
>- How can an **exponentially small set** $A$ undergo such a *dramatic transition* to an **exponentially large set** $A_{2t}$ under such a small perturbation $2t$ ? (Remember that $t$ can be much smaller than the radius $\sqrt{n}$ of the sphere.) 
>
>However perplexing this may seem, this is a **typical phenomenon** in **high dimensions**. 


>[!important]
>It is *reminiscent* of **zero-one laws** in *probability theory*, which basically state that *events* that are determined by **many random variables** tend to have **probabilities either zero or one**.

- [[Kolmogorov Zero-One Law]]



-----------
##  Recommended Notes and References

- [[Lipschitz Continuous Function]]
- [[Lebesgue Measure]]
- [[Isoperimetry Problem in Probability Metric Space]]
- [[Sub-Gaussian Norm]]
- [[Hoeffding Inequality]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]