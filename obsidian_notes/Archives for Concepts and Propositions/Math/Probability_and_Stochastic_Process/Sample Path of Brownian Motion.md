---
tags:
  - concept
  - math/stochastic_process
keywords:
  - sample_path_brownian_motion
topics:
  - stochastic_process
name: Sample Path of Brownian Motion
date of note: 2024-06-09
---

## Concept Definition

>[!important]
>**Name**: Sample Path of Brownian Motion

## Hölder Continuity

>[!important] Lemma (Hölder Continuity of Sample Path)
>Let $(X_{t})$ be stochastic process with **continuous sample path a.s.** such that
>$$
> \mathbb{E}\left[ \lvert X_{t} - X_{s} \rvert^{\beta}  \right] \le \lvert t - s \rvert^{1+\alpha} 
>$$
>for some constants $\beta, \alpha>0$ and $C \ge_{0}$ and for all times $t ,s \ge 0.$
>
>Then for each $T >0$, almost every $\omega$, and each $$0 < \gamma < \frac{\alpha}{\beta},$$ there exists a constant $K := K(\omega, \gamma , T)$ such that 
>$$
>\begin{align*}
> \lvert X(\omega, t) - X(\omega, s)\rvert  \le K \lvert t - s \rvert^{\alpha} 
>\end{align*}
>$$
>for all $0 \le s,t \le T.$


>[!important] Theorem (Hölder Continuity of Brownian Sample Path)
>Let $(W_{t})$ be a **Wiener process**.
>
>Then for each $T >0$, and **almost every** $\omega$, the sample path $$\omega \to W(\omega, t)$$ is **uniformly Hölder continuous** on $[0,T]$ for each exponent **$0 < \gamma < \frac{1}{2}.$**
>
 >That is, for $$0 < \gamma < \frac{1}{2},$$  for each $T >0$, and *almost every* $\omega$,  there exists a constant $K$ such that 
>$$
>\begin{align*}
> \lvert W(\omega, t) - W(\omega, s)\rvert  \le K \lvert t - s \rvert^{\alpha} 
>\end{align*}
>$$
>for all $0 \le s,t \le T.$

^192097

- [[Hölder Condition and Hölder Continuous Function]]
- [[Brownian Motion Wiener Process]]

## Nowhere Differentiability

>[!important] Theorem
>- For each $$\frac{1}{2} < \gamma \le 1$$ and **almost every** $\omega$, the sample path $$\omega \to W(\omega, t)$$ is **nowhere Hölder continuous** with *exponent* $\gamma.$
>- In particular, for *almost every* $\omega$, the sample path $$\omega \to W(\omega, t)$$ is **nowhere differentiable** and is of **infinite variation** on each *subinterval.*

^46cc20

- [[Space of Functions with Bounded Variation]]

>[!info]
>The sample path of Brownian motion is **not** of *bounded variation* $$\lVert W(\omega, t) \rVert_{TV} = \infty, \quad \forall \omega \in \Omega.$$

>[!info]
>Note that
>$$
>\text{ bounded variation function } \subset \text{ differentiable function } \subset \text{ Lipschitz continuous function} \subset \text{ Hölder continuous function}
>$$

### Proof

>[!important]
>The idea underlying the proof:
>if 
>$$
>\begin{align*}
> \lvert W(\omega, t) - W(\omega, s)\rvert  \le K \lvert t - s \rvert^{\gamma} 
>\end{align*}
>$$
>for all $t$, then $$\left\lvert W\left(\omega, \frac{j+1}{n}\right) - W\left(\omega, \frac{j}{n}\right) \right\rvert \le \frac{M}{n^\gamma}$$ for all $n \gg 1$ and at least $N$ values of $j$. 
>
>But these are **independent** events of **small probability**. The probability that the above inequality holds for **all** these $j$’s is a **small number** to the **large power** $N$, and is therefore **extremely small**.


## Explanation

>[!important]
>The **Markov property** partially “explains” the **nondifferentiability** of *sample paths* for Brownian motion. 
>
>If $W(\omega, s)=b$, say, then the *future behavior* of $W(\omega, t)$ *depends* **only** upon this fact and **not on how** $W(\omega, t)$ **approached the point** $b$ as $t\to s_{-}$. 
>
>Thus the sample path $W(\omega, \cdot)$ “*cannot remember*” *how to leave* $b$ in such a way that it will have a tangent there.









-----------
##  Recommended Notes and References

- [[Hölder Condition and Hölder Continuous Function]]
- [[Brownian Motion Wiener Process]]

- [[Stochastic Process]]

- [[Introduction to Stochastic Differential Equations by Evans]]