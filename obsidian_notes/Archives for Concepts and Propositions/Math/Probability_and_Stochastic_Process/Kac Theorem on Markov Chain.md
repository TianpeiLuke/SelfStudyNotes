---
tags:
  - concept
  - math/stochastic_process
keywords:
  - Markov_Chain
  - kac_theorem
topics:
  - stochastic_process
name: Kac Theorem on Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Kac Theorem on Markov Chain

### Discrete State Markov Chain

>[!important] Kac Theorem
>Let $(X_{n})$ be a Markov chain with *discrete state space* $\mathcal{X}$.
>
>If $(X_{n})$  is **irreducible recurrent**, then it has a **unique** **invariant distribution** $\pi$, given by
>$$ 
> \begin{align}
> \pi(x) &= \left(\mathbb{E}\left[  \tau_{x} | X_{0} = x \right]\right)^{-1}, \quad \forall x\in \mathcal{X}
> \end{align}
>$$  
 >which is the *reciprocal* of the *expected first return time* of state $x$.

- [[Recurrent Markov Chain]]
- [[Irreducibility of Markov Chain]]

### Harris Chain

>[!important] Kac Theorem
>Let $(X_{n})$ be **$\mu$-irreducible** with an **atom** $\alpha$.
>
>The chain is **positive** *if and only if* $$\mathbb{E}\left[  \tau_{\alpha} | X_{0} = x \right] <\infty, \quad \forall x\in \alpha.$$
>
>Moreover, the **invariant distribution** $\pi$ for $(X_{n})$ satisfies 
>$$
>\pi(\alpha) = \left(\mathbb{E}\left[  \tau_{\alpha} | X_{0} = x \right]\right)^{-1}\,\quad \forall x\in \alpha.
>$$

- [[Invariant Measure and Stationary Distribution]]
- [[Irreducibility of Markov Chain]]
- [[Atom of Markov Chain]]
- [[Stopping Time of Markov Chain]]



>[!important] Kac Theorem
>Let $(X_{n})$ be **$\mu$-irreducible recurrent**.  
>
>Then there exists an **invariant $\sigma$-finite measure** $\pi$ which is **unique** up to a *multiplicative factor*.

- [[Finite and sigma-Finite Measure]]



## Explanation

>[!important]
>For discrete state space $\mathcal{X}$, the Kac Theorem implies that as $n\rightarrow \infty$, for any state $x\in \mathcal{X}$, the **fraction of time** that Markov Chain **stays** *at* $x$ is **unchanged** and is the **reciprocal** of the *expected first return time*.

>[!important]
>The **converse** of Kac Theorem **do not hold** since there exists *transient* $\mu$-irreducible chain with **stationary distribution**.




-----------
##  Recommended Notes and References


- [[Invariant Measure and Stationary Distribution]]
- [[Irreducibility of Markov Chain]]

- [[Classification of States of Markov Chain]]
- [[Stopping Time of Markov Chain]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 224