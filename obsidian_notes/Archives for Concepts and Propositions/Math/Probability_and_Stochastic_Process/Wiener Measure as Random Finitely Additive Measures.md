---
tags:
  - concept
  - math/stochastic_process
keywords:
  - white_noise_process
topics:
  - stochastic_process
name: Wiener Measure as Gaussian Random Signed Measures
date of note: 2024-06-07
---

## Concept Definition

>[!important]
>**Name**: Wiener Measure as Gaussian Random Signed Measures


>[!important] Definition
>Let $(\mathcal{X}, \mathscr{A}, \mu)$ be a *measure space* and $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space*. Let $$\mathscr{A}_{0} := \left\{ A\in \mathscr{A}: \mu(A) < \infty \right\}.$$
>
>Define a *Gaussian random function* 
>$$
>\mathcal{W}: \Omega \to (-\infty, +\infty)^{\mathscr{A}_{0}} \quad \text{ or }\quad \mathcal{W}: \Omega \times \mathscr{A}_{0} \to (-\infty, +\infty)
>$$ 
>so that 
>- For each $\omega \in \Omega$, 
>$$
>\mathcal{W}(\omega, \cdot):  \mathscr{A}_{0} \to (-\infty, +\infty)
>$$ 
>is a *set function* on $\mathscr{A}_{0}$.
>- For each  $A\in \mathscr{A}_{0}$, 
>$$
>\mathcal{W}_{A} := \mathcal{W}(\cdot, A)
>$$
>is a **Gaussian random variable** with *mean* $$\mathbb{E}_{\mathcal{P}}\left[\mathcal{W}_{A}\right] = 0.$$
>- Moreover,  given $A, B\in \mathscr{A}_{0}$,  the **covariance function** of this *Gaussian random function* is given by 
>$$
>\mathbb{E}_{ \mathcal{P} }\left[  \mathcal{W}_{A}\,\mathcal{W}_{B} \right] = \mu(A \cap B).
>$$
>
>The stochastic process $(\mathcal{W}_{A}: A\in \mathscr{A}_{0})$ is a *Gaussian process*, called **the white noise process** with **control measure** $\mu$.

- [[Lectures on Gaussian Processes by Lifshits]]
- [[Signed Measure]]
- [[Gaussian Random Function]]
- [[Gaussian Process]]

>[!important] 
>Following this definition, we see that the **variance of white noise** is
>$$
>\mathbb{E}_{ \mathcal{P} }\left[ \mathcal{W}_{A}^2 \right] = \text{Var}(\mathcal{W}_{A}) = \mu(A).
>$$
>That is
>$$
>\mu(A) = \int_{\Omega} (\mathcal{W}(\omega, A))^2\, d\mathcal{P}(\omega)
>$$


## Sample Path as Finitely Additive Measure 


>[!important] Definition
>Additional properties for the **white noise process**:
>- **Finite additivity**: If $E_1, E_2, \ldots E_{n}\in \mathscr{A}_{0}$ are a *finite sequence* of *disjoint* measurable sets, then 
> $$
> \begin{align*}
> \mathcal{W}\left(\omega\;, \;\bigcup_{k=1}^{n} E_k\right) &= \sum_{k=1}^{n} \mathcal{W}(\omega\;,\; E_k), \quad \omega-\text{a.s.}
> \end{align*}
> $$
>- **Independence**:  If $E_1, E_2, \ldots E_{n}\in \mathscr{A}_{0}$ are *__disjoint__* measurable sets, then 
>$$
>\mathcal{W}_{E_{1}} \,{,}\ldots{,}\,\mathcal{W}_{E_{n}} 
>$$
>are **independent random variables**.
>
>In other word, $\mathcal{W}(\omega)$ is a **finitely additive (signed) measure** for each $\omega$. This measure $\mathcal{W}$ is called **Wiener measure**.

- [[Independent Random Variables]]

>[!important] Proposition
>Let $(\mathcal{X}, \mathscr{A}, \mu)$ be a *measure space*. Let $$\mathscr{A}_{0} := \left\{ A\in \mathscr{A}: \mu(A) < \infty \right\}.$$
>
>Then there exists a **probability space** $(\Omega, \mathscr{F}, \mathcal{P})$ and a **while noise process** $(\mathcal{W}_{A}, A\in \mathscr{A}_{0})$ with **control measure** $\mu$ defined on this space such that, for *almost all* $\omega \in \Omega$, the *sample functions* of the while noise
>$$
>A \mapsto \mathcal{W}_{A}(\omega)
>$$
>are **finitely additive measures** on the (Boolean) algebra $\mathscr{A}_{0}$.

- [[Boolean Algebra]]
- [[Finitely Additive Measure]]

## Brownian Motion via White Noise Integration

>[!important] 
>Let $(\mathbb{R}, \mathcal{L}[\mathbb{R}], m)$ be the **Lebesgue measure space**. Define a family of **indicator functions** $\{ m_{t}(\cdot), t\in \mathbb{R} \}$  as
>$$
>m_{t}(x) = \mathbb{1}\{ x \in (-\infty, t] \}
>$$
>Then 
>$$
>W_{t} := \mathcal{W}((-\infty, t]) = \int_{\mathbb{R}} m_{t}\;d\mathcal{W}
>$$
>is a **Brownian Motion**.
>
>Also this shows that 
>$$
>dW = \mathcal{W}\;dt
>$$

- [[Integration with respect to Wiener Measure]]
- [[Brownian Motion Wiener Process]]




-----------
##  Recommended Notes and References

- [[White Noise Process]]
- [[Brownian Motion Wiener Process]]
- [[Gaussian Process]]

- [[Itô Stochastic Integration]]
- [[Brownian Motion Wiener Process]]

- [[Wasserstein Distance]]
- [[Wasserstein Space]]

- [[Lectures on Gaussian Processes by Lifshits]]
- Wikipedia [White noise analysis](https://en.wikipedia.org/wiki/White_noise_analysis)