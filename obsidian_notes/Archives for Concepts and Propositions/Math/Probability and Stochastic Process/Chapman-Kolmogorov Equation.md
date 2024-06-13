---
tags:
  - concept
  - math/stochastic_process
  - machine_learning_models/mc
keywords:
  - Transition_Kernel
  - chapman_kolmogorov_equation
topics:
  - stochastic_process
name: Chapman-Kolmogorov Equation
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Chapman-Kolmogorov Equation

>[!important] Definition
>Let $\{(X_{n}, \mathscr{F}_{n}), n\ge 0\}$ be a *Markov chain* of random variables on measurable space $(\mathcal{X}, \mathcal{B}(\mathcal{X}))$ and $K: \mathcal{X} \times \mathcal{B}(\mathcal{X}) \to \mathbb{R}$ be the *transition kernel* of the Markov chain.
>
>The **kernel of $n$ transitions** is given by 
>$$
>\begin{align*}
> K^n(x, A) := \int_{\mathcal{X}} K^{n-1}(y, A)\, K(x, dy).
\end{align*}
>$$

- [[Markov Chain and Markov Process]]
- [[Markov Chain Transition Kernel]]
- [[Fubini Theorem]]


>[!important] Theorem (Chapman-Kolmogorov Equation)
>For every $m,n \in \mathbb{N}$, $x\in \mathcal{X}$ and $A \in \mathcal{B}(\mathcal{X})$, 
>$$
>\begin{align*}
> K^{m+n}(x, A) := \int_{\mathcal{X}} K^{n}(y, A)\, K^{m}(x, dy).
\end{align*}
>$$

- [[Fubini Theorem]]
## Explanation

>[!info]
>In general, we can consider $K$ as an **operator** on $L^1(\mu)$. 
>
>That is, we can define
>$$
>K\,h(x) := \int_{\mathcal{X}} h(y)\,K(x, dy)
>$$

- [[Fubini Theorem]]


-----------
##  Recommended Notes and References



- [[Markov Chain and Markov Process]]
- [[Markov Chain Transition Kernel]]

- [[Fubini Theorem]]


- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
