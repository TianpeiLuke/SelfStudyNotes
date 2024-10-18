---
tags:
  - concept
  - math/real_analysis
keywords:
  - riemann_integration
  - riemann_upper_integration
  - riemann_lower_integration
topics:
  - real_analysis
name: Riemann Integration
date of note: 2024-06-06
---

## Concept Definition

>[!important]
>**Name**: Riemann Integration

>[!important] Definition
>Let $f: [a,b] \to \mathbb{R}$ be a *bounded function*, i.e. there exists some $M >0$ such that $$|f(x)| \le M$$ for all $x\in [a, b].$ Let  $\mathcal{P}$ be *all possible partitions* of $[a,b]$.
>
 >The **Riemann lower integral** of $f$ is defined as
>$$
>\begin{align*}
>L(f) := \sup\left\{L(f, P): P\in \mathcal{P}  \right\}
>\end{align*}
>$$
>where $L(f, P)$ is the *Darboux lower sum* with respect to a partition $P\in \mathcal{P}$.
>
>Similarly, the **Riemann upper integral** of $f$ is defined as
>$$
>\begin{align*}
>U(f) = \sup\left\{ U(f, P): P\in \mathcal{P} \right\}
>\end{align*}
>$$
>where $U(f, P)$ is the *Darboux upper sum* with respect to a partition $P\in \mathcal{P}$.

- [[Darboux Lower Sum and Darboux Upper Sum]]
- [[Supremum and Infimum of Sets]]


>[!important] Proposition
>For any bounded function $f: [a,b] \to \mathbb{R}$, $$L(f) \le U(f).$$

>[!important] Definition 
>Let $f: [a,b] \to \mathbb{R}$ be a *bounded function*. 
>
>We say that $f$ is **Riemann-integrable** if $$L(f) = U(f).$$ We denote it as $f\in \mathcal{R}$ and
>$$
>\int_{a}^{b}f(x)\,dx = U(f) = L(f)
>$$

### Original Version

>[!important] Definition (Original Version)
>Let $[a, b]$ be an interval of positive length, and $f : [a, b] \rightarrow \mathbb{R}$ be a *bounded function*. 
>
>- A **tagged partition** $$P \equiv ((x_{0}, x_{1},\,\ldots\,, x_{n}); (x'_{1},\,\ldots\,, x'_{n}))$$ of $[a, b]$ is a finite sequence of real numbers $$a = x_0 < x_1 < \cdots < x_{n} = b,$$ together with *additional numbers* $x_{i-1} \le  x'_{i} \le  x_{i}$ for *each* $1\le i\le n$. We abbreviate $(x_{i}- x_{i-1})$ as $\Delta x_{i}$. 
>
>- The quantity $$\Delta(P) \equiv \sup_{1\le i\le n} \Delta x_{i}$$ will be called the **norm** *of the tagged partition*. 
>
>The **Riemann sum** $\mathcal{R}(f ; P)$ of $f$ *with respect to* the *tagged partition* $P$ is denoted as
>$$
> \begin{align*}
> \mathcal{R}(f ; P) &\equiv \sum_{i=1}^{n}f(x'_{i})\Delta x_{i}
> \end{align*}
>$$  
>
>Then $f$ is said to be **Riemann integrable** if there exist a number $\int_{a}^{b}f(x)dx$ such as for any $\epsilon>0$, there *exists* $\delta>0$, *for all* $P$ *such that* $\Delta(P) < \delta$,  
>$$
> \begin{align*}
> \left|\mathcal{R}(f ; P) - \int_{a}^{b}f(x)dx \right| \le \epsilon
> \end{align*}
>$$ 
> holds.



## Explanation

>[!info]
>The **existence** of *Riemann lower integral* and *Riemann upper integral* is guaranteed for bounded function $f$ on closed set $[a,b]$, since the *Darboux lower sum* and *Darboux upper sum* are *partially ordered*.
>$$
>P \subseteq Q \implies L(f, P) \le L(f, Q), \;\; U(f, P) \ge U(f, Q).
>$$

>[!important]
>We can denote Riemann upper integral and lower integral as
>$$
>U(f) := \overline{\int_{a}^{b}}f(x)\,dx, \quad L(f) := \underline{\int_{a}^{b}}f(x)\,dx.
>$$


## Criterion of Riemann Integrability

- [[Criterion of Riemann-Stieltjes Integrability]]


## Riemann-Stieltjes Integration

- [[Riemann–Stieltjes Integration]]



-----------
##  Recommended Notes and References



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Principles of Mathematical Analysis by Rudin]] pp 121
- Abbott, S. (2015). _Understanding analysis_. Springer.