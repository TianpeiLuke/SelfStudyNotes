---
tags:
  - concept
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - ergodic_theorem
topics:
  - functional_analysis
  - stochastic_process
name: Ergodic Theorem
date of note: 2024-06-23
---

## Concept Definition

>[!important]
>**Name**: Ergodic Theorem


### Individual Ergodic Theorem

>[!important] Birkhoff Ergodic Theorem (Probability Space)
>Let $(\Omega,\mathscr{F}, \mathcal{P})$ be a *probability space*, and $T\in \mathcal{L}(\Omega)$ be a **measure preserving transformation** with respect to $\mathcal{P}$.
>
>Then $T$ is **ergodic** *if and only if* for every $g\in L^1(\Omega, \mathcal{P})$, 
>$$
>\begin{align*}
>\lim_{ n \to \infty }\left[ \frac{1}{n} \sum_{k=0}^{n-1}\,g\left(T^{k}(\omega)\right) \right] &= \int_{\mathcal{X}}g\,d\mathcal{P}\quad \omega\text{-a.s.}
>\end{align*}
>$$

- [[Ergodic Transformation]]
- [[Measure Preserving Transformation]]
- [[Probability Space]]
- [[Real Analysis by Royden]] pp 493

>[!important] Birkhoff Ergodic Theorem (Finite Measure Space, version 2)
>Let $(\mathcal{X},\mathscr{F}, \mu)$ be a *measure space*, and $T\in \mathcal{L}(\Omega)$ be a **measure preserving transformation** with respect to $\mu$.
>
>Then for every $g\in L^1(\mathcal{X}, \mu)$, 
>$$
>\begin{align*}
>\lim_{ n \to \infty }\left[ \frac{1}{n} \sum_{k=0}^{n-1}\,g\left(T^{k}(x)\right) \right] &= \hat{g}(x)\quad x\text{-a.s.}
>\end{align*}
>$$
>where $\hat{g}\in L^1(\mathcal{X}, \mu)$ and is **invariant** under $T$, i.e.
>$$
>\hat{g}(Tx) = \hat{g}(x).
>$$
>
>If $\mu(\mathcal{X}) < \infty$, i.e. $\mu$ is **finite**, then
>$$
> \int_{\mathcal{X}}\hat{g}\,d\mu =  \int_{\mathcal{X}}g\,d\mu.
>$$
>
>If, furthermore, $T$ is **ergodic**, then 
>$$
>\hat{g}(x) = \frac{1}{\mu(\mathcal{X})} \int_{\mathcal{X}}g\,d\mu\quad x\text{-a.s.}
>$$

- [[Measure Preserving Transformation]]
- [[Probability and Measure by Billingsley]] pp 314
- [[Functional Analysis by Reed]] pp 60
- [[Real Analysis by Royden]] pp 493
- Halmos, P. R. (2017). _Lectures on ergodic theory_. Courier Dover Publications. pp 18

>[!info]
>This theorem applies to all finite measure space.

- [[Finite and sigma-Finite Measure]]

### Mean Ergodic Theorem

>[!important] Koopman's Lemma
>Let $(\mathcal{X},\mathscr{F}, \mu)$ be a *measure space*, and $T\in \mathcal{L}(\Omega)$ be a **measure preserving transformation** with respect to $\mu$.
>
>Define a map $U_{t}: L^2(\mathcal{X}, \mu) \to L^2(\mathcal{X}, \mu)$ as 
>$$
> \left(U_{t}f\right)(w) = f\left(T_{t}\,w\right), \quad \forall\, f\in L^2(\mathcal{X}, \mu).
>$$
>
>Then $U_{t}$ is an **unitary operator**.

- [[Unitary Operator in Hilbert Space]]
- [[Adjoint of Bounded Operator in Banach Space]]
- [[Pullback of Covector Fields]]
- [[Functional Analysis by Reed]] pp 57

>[!important] von Neumann's Ergodic Theorem (Mean Ergodic Theorem)
>Let $U$ be an **unitary operator** on a *Hilbert space* $\mathcal{H}$. Let $P$ be the **orthogonal projection** onto $$\left\{ f \in \mathcal{H}: U f = f  \right\}. $$ 
>
>Then, for any $f\in \mathcal{H}$, 
>$$
>\begin{align*}
>\lim_{ n \to \infty } \frac{1}{n} \sum_{k=0}^{n-1}U^{k} f &= P\,f. 
>\end{align*}
>$$

- [[Hilbert Space]]
- [[Projection Operator in Hilbert Space]]
- [[Functional Analysis by Reed]] pp 57

>[!important] Corollary
>Let $T_{t}$ be **$\mu$-ergodic**. Then for any $f\in L^2(\mathcal{X}, \mu)$, 
>$$
>\lim_{ T \to \infty } \frac{1}{T}\int_{0}^{T}\,f\left(T_{t}\,w\right)\,dt = \int_{\mathcal{X}}\,f\,d\mu \quad \text{ in }L^2 \text{ sense.}
>$$
>i,e,
>$$
>\lim_{ T \to \infty } \, \int_{\mathcal{X}}\,\left|\frac{1}{T}\int_{0}^{T}\,f\left(T_{t}\,w\right)\,dt    - f \right|^2\, d\mu = 0.
>$$

- [[Ergodic Transformation]]
- [[Convergence in Lp norm]]


## Explanation

>[!important]
>Note that the RHS of Ergodic theorem $\mathcal{P}\,g$ is **independent** of the choice of $\omega\in \Omega$.
>
>That is, the limit is a **constant function**.




-----------
##  Recommended Notes and References

- [[Ergodic Theorem for Positive Recurrent Markov Process]]

- [[Measure Preserving Transformation]]
- [[Ergodic Transformation]]



- [[Probability and Measure by Billingsley]] pp 314
- [[Real Analysis by Royden]] pp 493
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 18, pp 31
- [[Functional Analysis by Reed]]
- [[Monte Carlo Statistical Methods by Robert]]
