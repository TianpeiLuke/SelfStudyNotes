---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - helly_selection_theorem
  - normed_space
  - dual_normed_space
  - separable_space
  - bounded_linear_functional
  - weak_convergence_banach_space
topics:
  - functional_analysis
  - topology
name: Helly Selection Theorem
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Helly Selection Theorem

### Real Line

>[!important] Helly Selection Theorem (Real-Line)
>Let $\{ \psi_{n} \}_{n\in \mathbb{N}}$ be a sequence of **increasing real-valued functions** on $\mathbb{R}$.
>
 >Suppose that it is **uniformly bounded**, i.e. there are $a, b\in \mathbb{R}$ such that $$a \le \psi_{n} \le b$$ for every $n\in \mathbb{N}$. 
 >
 >Then the sequence $\{ \psi_{n} \}_{n\in \mathbb{N}}$ admits a **pointwise convergent subsequence**.


### Weak$^{*}$ Convergence in Dual Space


>[!important] Helly Selection Theorem (Separable Normed Space)
>Let $\mathcal{X}$ be a **separable normed vector space**.
>
>Then every **bounded** sequence $\{ \psi_{n} \}$ in **dual space** $\mathcal{X}^{*}$ has a *subsequence* that converges **pointwise** on $\mathcal{X}$ to $\psi \in \mathcal{X}^{*}$.
>
>That is, $\{ \psi_{n} \}$ has a *subsequence* that converges to $\psi$ with respect to **weak$^*$ topology**.
>$$
>\{ \psi_{n} \} \subset B \subset \mathcal{X}^{*} \implies (\exists\, \{ \psi_{n_{k}} \} \subset \{ \psi_{n} \} )\;\; \psi_{n_{k}} \stackrel{w^{*}}{\longrightarrow} \psi
>$$


- [[Separable Space]]
- [[Pointwise Convergence]]
- [[Weak Convergence in Banach Space]]
- [[Sequential Compactness]]
- [[Bolzano-Weierstrass Theorem]]
- [[Real Analysis by Royden]] pp 283

- We can write it explicitly.

>[!important] Helly Selection Theorem (Separable Normed Space)
>Let $\mathcal{X}$ be a **separable normed vector space** and $\{ \psi_{n} \}$ be a sequence in **dual space** $\mathcal{X}^{*}$ that is **bounded**, that is, there exists an $M \ge 0$ such that 
>$$
> \lvert \psi_{n}(f) \rvert \le M\,\lVert f \rVert, \quad \forall f\in \mathcal{X}, \forall n  
>$$
>
>Then there exists a *subsequence* $\{ \psi_{n_{k}} \} \subset \{ \psi_{n} \}$ and $\psi \in \mathcal{X}^{*}$ such that 
>$$
>\lim_{ k \to \infty } \psi_{n_{k}}(f) = \psi(f),\, \quad \forall f\in \mathcal{X}. 
>$$

- [[Real Analysis by Royden]] pp 171

### Convergence in Distribution

>[!important] Helly Selection Theorem (Cumulative Distributions)
>For every sequence $\{ F_{n} \}$ of **cumulative distribution functions**, there *exists* a subsequence $\{ F_{n_{k}} \}$ and a **non-decreasing, right-continuous** function $F$ such that 
>$$
> \lim_{ k \to \infty } F_{n_{k}}(x) = F(x)
>$$ 
>at **continuity points** $x$ of $F$.

^b0ca99

- [[Cumulative Distribution Function of Random Variable]]
- [[Convergence in Distribution]]
- [[Portmanteau Theorem]]
- [[Semi-Continuous Function]]
- [[Probability and Measure by Billingsley]] pp 336
- [[A Probability Path by Resnick]] pp 309

>[!important] Helly Selection Theorem (Measures)
>Let $(\mathcal{X}, \mathscr{F})$ be a measurable space. 
>
>For every *sequence* of **probability measures** $\{ \mu_{n} \}$ on $\mathscr{F}$, the following two statements are **equivalent**:
>- there exists a *subsequence* $\{ \mu_{n_{k}} \} \subset \{ \mu_{n} \}$ on $\mathscr{F}$ and a *probability measure* $\mu$ on $\mathscr{F}$ such that $$\mu_{n_{k}} \stackrel{d}{\longrightarrow} \mu,$$ i.e. $\mu_{n_{k}}$ converges to $\mu$ **in distribution**.
>- the sequence of measures $\{ \mu_{n} \}$ is **tight.**

- [[Convergence in Distribution]]
- [[Tightness of Measures]]
- [[Probability and Measure by Billingsley]] pp 336

- We present the *sufficient condition*
>[!important] Theorem
>Let $(\Omega, \mathscr{F})$ be a Hausdorff measurable space. 
>
>If a collection $\{ \mu_{n} \}$ of **probability measures** defined on $\mathscr{F}$ is **tight**, then there exists a *subsequence* $$\{\mu_{n_{k}}\} \subset \{ \mu_{n} \}$$ and a **probability measure** $\mu$ on $\mathscr{F}$ such that 
>$$
>\mu_{n_{k}} \stackrel{d}{\longrightarrow} \mu.
>$$

- [[Probability and Measure by Billingsley]] pp 380

>[!important] Corollary
>Let $(\Omega, \mathscr{F})$ be a Hausdorff measurable space. 
>
>If $\{ \mu_{n} \}$ is a sequence of **tight probability measures**, and if **every** *subsequence* $\{\mu_{n_{k}}\} \subset \{ \mu_{n} \}$ converges to $\mu$ **in distribution**,  where $\mu$ is a **probability measure** on $\mathscr{F}$. That is, $$\mu_{n_{k}} \stackrel{d}{\longrightarrow} \mu$$ 
>
>Then $\{ \mu_{n} \}$ converges to $\mu$ **in distribution**, i.e.
>$$
>\mu_{n} \stackrel{d}{\longrightarrow} \mu.
>$$

- [[Probability and Measure by Billingsley]] pp 381

## Explanation


>[!important]
>For *separable Banach space*, the above theorem states that a **bounded subset**  in $X^{*}$ is **sequential compact** under **weak$^*$ topology**, i.e. **weak sequential compactness**.

- [[Sequential Compactness]]

>[!info]
>In [[Helly Selection Theorem#^b0ca99]], the limit function $F$ **need not to be a c.d.f. itself**.


## Banach-Alauglu Theorem

![[Banach-Alaoglu Theorem#^ef7478]]

>[!important]
>**Banach-Alaoglu** theorem generalize the result from **Helly selection theorem**. 
>
>Any compact set is sequentially compact by [[Bolzano-Weierstrass Theorem]].

- [[Banach-Alaoglu Theorem]]
- [[Bolzano-Weierstrass Theorem]]


-----------
##  Recommended Notes and References



- [[Separable Space]]
- [[Pointwise Convergence]]
- [[Tightness of Measures]]
- [[Weak Convergence in Banach Space]]
- [[Weak Topology of Banach Space]]

- [[Reflexive Normed Space and Bidual of Normed Space]]
- [[Dual Normed Space and Dual Banach Space]]


- [[Hilbert Space]]
- [[Banach Space]]
- [[Norm and Normed Space]]

- [[Cumulative Distribution Function of Random Variable]]
- [[Convergence in Distribution]]
- [[Portmanteau Theorem]]


- [[A Probability Path by Resnick]] pp 309
- [[Real Analysis by Royden]] pp 171, 283
- [[Probability and Measure by Billingsley]] pp 336
- Wikipedia [Helly_selection_theorem](https://en.wikipedia.org/wiki/Helly%27s_selection_theorem)