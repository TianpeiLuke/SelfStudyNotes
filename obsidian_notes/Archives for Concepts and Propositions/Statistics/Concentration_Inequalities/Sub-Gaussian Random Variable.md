---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - sub-gaussian_distribution
topics:
  - statistics
name: Sub-Gaussian Random Variable
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Sub-Gaussian Random Variable

>[!info] Chernoff Bound for Normal distribution
>Let $X$ be a **centered Normal random variable** with variance $\sigma^2$. Then
>$$
> \begin{align*}
> \psi_X(\lambda) = \frac{\lambda^2 \sigma^2}{2},\, \quad \lambda_t = \frac{t}{\sigma^2}
> \end{align*} 
>$$
>and, therefore for every $t > 0$, 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) &= \frac{t^2}{2\sigma^2}.
> \end{align*} 
>$$ 
>Hence, **Chernoff's inequality** implies, for all $t > 0$,
>$$
> \begin{align*}
> \mathcal{P}\{X \ge t\} &\le \exp \left( -\frac{t^2}{2\sigma^2} \right).
> \end{align*}
>$$ 


>[!important] Definition
>A *centered* random variable $X$ is said to be **sub-Gaussian** with **variance factor** $\nu$ if
>$$
> \begin{align}
> \psi_X(\lambda) &\le  \frac{\lambda^2 \nu}{2}, \quad \text{ for every }\lambda \in \mathbb{R}.
> \end{align}
>$$  
>We denote the collection of such random variables by $\mathcal{G}(\nu)$.

- [[Algorithm Big-O Notations and Dominance Relation]]

## Explanation


## Sub-Gaussian Properties

>[!important] Proposition (Sub-Gaussian Properties)
>Let $X$ be a random variable. 
>
>Then the following properties are **equivalent**; the parameters $K_i > 0$ appearing in these
> properties differ from each other by *at most an absolute constant factor*.
>
>- The **tails** of $X$ satisfy
>$$
> \begin{align*}
> \mathcal{P}\left\{ \lvert X \rvert \ge t \right\}  \le 2 \exp\left(-\frac{t^2}{K_1^2}\right),\quad\; \forall\, t \ge 0.
> \end{align*}
> $$
> 
>- The $p$-**moments** of $X$ satisfy
>$$ 
> \begin{align*}
> \lVert X \rVert_{L^{p}}  = \left(\mathbb{E}\left[ \lvert X \rvert^{p}  \right]\right)^{1/p} \le K_2 \sqrt{p},\quad \forall\, p \ge 1.
> \end{align*}
>$$
> 
>- The **moment-generating function (MGF)** of $X^2$ satisfies
>$$
> \begin{align*}
> \mathbb{E}\left[\exp(\lambda^2 X^2) \right] \le \exp(K_3^2 \;\lambda^2) \quad \forall\, \lambda \text{ such that } \lvert \lambda \rvert  \le \frac{1}{K_3}
> \end{align*}
>$$
>
>- The **MGF** of $X^2$ is **bounded** at some point, namely
>$$
> \begin{align*}
> \mathbb{E}\left[\exp\left(\frac{X^2}{K_{4}^2}\right) \right]  \le 2.
> \end{align*}
>$$ 
> 
>Moreover, if $\mathbb{E}\left[  X \right] = 0$ then properties $(1)$-$(4)$ are also **equivalent** to the following one.
> 
>- The **MGF** of $X$ satisfies
>$$
> \begin{align*}
> \mathbb{E}\left[  \exp(\lambda X) \right] \le  \exp(K_5^2\,\lambda^2),\quad \forall\, \lambda \in \mathbb{R}.
> \end{align*}
>$$ 


- [[Hoeffding Inequality]]
- [[Lp Space]]
- [[Moment Generating Function]]
- [[Sub-Gaussian Norm]]


## Examples

- [[Sub-Gaussian Norm]]

>[!example]
>Any **bounded random variable** $X$ is **sub-gaussian** with
>$$
> \begin{align*}
> \lVert X \rVert_{\psi_2}\le C \lVert X \rVert_{\infty}
> \end{align*}
>$$
> where $C = 1/\sqrt{\log 2}$.







-----------
##  Recommended Notes and References

- [[Sub-Gaussian Norm]]
- [[Hoeffding Inequality]]

- [[Chernoff Bound for Gaussian distribution]]
- [[Cramér–Chernoff Method]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]] pp 21 -  28
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]