---
tags:
  - concept
  - statistics/concentration_inequality
  - math/stochastic_process
  - machine_learning/theory
keywords:
  - vc_class
  - concentration_empirical_process
topics:
  - concentration_inequality
  - stochastic_process
  - machine_learning_theory
name: Concentration of Empirical Process indexed by VC Class
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Concentration of Empirical Process indexed by VC Class

>[!important] Theorem
>Let $\mathcal{F}$ be a class of **Boolean functions**  on a probability space $(\mathcal{X}, \mathscr{F}, \mathcal{P})$ with **finite VC dimension** $d \ge 1$. 
>
>Let $X, X_1 \,{,}\ldots{,}\,X_n$ be **independent** *random variables* in $\mathcal{X}$ distributed according to the *law* $\mathcal{P}$. 
>
>Then 
>$$
> \begin{align}
> \mathbb{E}\left[\lVert \mathcal{P}_{n} - \mathcal{P} \rVert_{\mathcal{F}}  \right] := \mathbb{E}\left[  \sup_{f \in \mathcal{F}}\left(\mathcal{P}_{n}f - \mathcal{P}f\right) \right]  &\le C\sqrt{\frac{d}{n}}, 
> \end{align}
>$$  
>where $d =\text{VC-dim}(\mathcal{F})$ is the **VC-dimension** of $\mathcal{F}$.

- [[VC Dimension]]
- [[Vapnik-Chervonenkis Class]]
- [[Empirical Process and Empirical Measure]]

- [[Dudley Entropy Integral Inequality]]
- [[Glivenko-Cantelli Class]]


## Explanation

>[!info]
>For a class of boolean functions $\mathcal{F}$, the constant $K$ of sub-Gaussian process is $1$ since for any $f, g\in \mathcal{F}$
>$$
>\begin{align*}
>\lVert \mathcal{P}_{n}f - \mathcal{P}_{n}g \rVert_{\psi_{2}} &=  \left\lVert  \frac{1}{n} \sum_{j=1}^n \epsilon_{j}(f-g)(X_{j})  \right\rVert_{\psi_{2}} \\
>&\le \left(\frac{1}{n} \sum_{j=1}^n (f-g)(X_{j})^2 \right)^{1/2} \\
>&= \lVert f - g \rVert_{2} 
\end{align*}
>$$
>
>By [[Dudley Entropy Integral Inequality#^9e072c]], 
>$$
>\begin{align*}
>\mathbb{E}\left[ \lVert \mathcal{P}_{n} - \mathcal{P} \rVert_{\mathcal{F}} | X_{1} \,{,}\ldots{,}\, X_{n}\right] &:= \mathbb{E}\left[ \sup_{f\in \mathcal{F}}\left(\mathcal{P}_{n}f - \mathcal{P}f\right)\right]\\
>&\le \frac{1}{\sqrt{ n }}\, \int_{0}^{1}\sqrt{ \log \mathcal{N}\left(\mathcal{F}, \lVert \cdot \rVert_{2}, \epsilon \right) }\,d\epsilon 
\end{align*}
>$$
>
>Then due to [[Metric Entropy Bound of VC Class]]
>$$
>\log \mathcal{N}(\mathcal{F}, L_2(\mathcal{P}), \epsilon) \le\; C\,d\;\log \left(\frac{2}{\epsilon}\right)
>$$
>we have
>$$
>\begin{align*}
>\mathbb{E}\left[ \lVert \mathcal{P}_{n} - \mathcal{P} \rVert_{\mathcal{F}}  \right] &\le \frac{1}{\sqrt{ n }}\, \int_{0}^{2} \sqrt{ C_{2}\,d\;\log \left(\frac{2}{\epsilon}\right) } d\epsilon\\
>&= \sqrt{ \frac{d}{n} } C_{3} \int_{0}^{2} \sqrt{ \log \left(\frac{2}{\epsilon}\right) } d\epsilon\\
>&= C_{4} \sqrt{ \frac{d}{n} } 
\end{align*}
>$$

- [[Symmetrized Empirical Process]]
- [[Talagrand Contraction Principle]]



-----------
##  Recommended Notes and References

- [[Vapnik-Chervonenkis Class]]
- [[Glivenko-Cantelli Class]]


- [[VC Dimension]]
- [[Empirical Process and Empirical Measure]]
- [[Packing Number of Metric Space]]
- [[Covering Number of Metric Space]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]