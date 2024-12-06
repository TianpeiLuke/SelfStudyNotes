---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
  - machine_learning/theory
  - math/functional_analysis
keywords:
  - epsilon_Isometry
topics:
  - stochastic_process
  - concentration_inequality
  - machine_learning_theory
  - functional_analysis
name: epsilon Isometry
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: epsilon Isometry


>[!important] Definition (Metric Space)
>Let $(X, d_{X})$ and $(Y, d_{Y})$ be two metric spaces. $\epsilon>0$ is a real number.
>
>A map $f: X \to Y$ is called an **$\epsilon$-isometry** if 
>- for any $x, y \in X$
>$$
>\begin{align*}
> | d_{Y}\left(f(x), f(y)\right) - d_{X}(x, y) | < \epsilon
\end{align*}
>$$
>- for any point $y\in Y$, there exists a point $x\in X$ such that $$d_{Y}(f(x), y) < \epsilon.$$
>  
>That is, $f$ preserve *the metric* between $x, y$ **within** $\epsilon$, and leave *no elements in codomain further than*  $\epsilon$ away from the image of domain.

^575618

- [[Metric Space]]

>[!important] Definition (Normed Vector Space)
>Consider an arbitrary set  $A \subset \mathbb{R}^D$ or $A \subset \mathcal{H}$ for *separable Hilbert space* $\mathcal{H}$.  
>
>Given $\epsilon \in (0, 1)$, a map $f : \mathbb{R}^D \to \mathbb{R}^d$ is called an **$\epsilon$-isometry** *on* $A$ if for every pair $a, a' \in A$, we have
>$$
> \begin{align*}
> (1 - \epsilon)\lVert a - a' \rVert_{2}^2 \le \lVert f(a) - f(a') \rVert_{2}^2 \le (1 + \epsilon)\lVert a - a' \rVert_{2}^2.
> \end{align*}
>$$ 

- [[Separable Hilbert Space]]
- [[Norm and Normed Space]]

- [[Isometry and Isometric isomorphism]]


## Explanation







-----------
##  Recommended Notes and References

- [[Isometry and Isometric isomorphism]]

- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Lectures on Gaussian Processes by Lifshits]]