---
tags:
  - concept
  - math/stochastic_process
keywords:
  - ergodicity
  - Markov_Chain
topics:
  - stochastic_process
name: Ergodic Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Ergodic Markov Chain

### Discrete State Markov Chain

>[!important] Definition
>A *discrete-state Markov chain* is  **irreducible**, **positive recurrent** and **aperiodic**, then it is called **ergodic**.

- [[Positive Recurrent Markov Chain]]
- [[Aperiodic Markov Chain]]
- [[Irreducibility of Markov Chain]]

### Harris Chain

>[!important] Definition
>Let  $(X_{n})$  be a Markov chain with kernel $K$ and uncountable state. 
>
> Suppose that
> - $(X_{n})$ is **Harris positive**, thus *Harris recurrent*, and
> - $(X_{n})$ has **invariant measure** $\pi$.
>   
>An *atom* $\alpha \in \mathcal{B}(\mathcal{X})$ is called **ergodic** if 
>$$\lim_{ n \to \infty } \lvert K^n(\alpha, \alpha) - \pi(\alpha) \rvert = 0 $$

- [[Positive Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]

- [[Monte Carlo Statistical Methods by Robert]] pp 231
## Explanation


>[!important]
>The concept of **ergodic Markov chain** requires additional condition for **aperiodic** but this condition is **unnecessary** for *erogdic theorem* to hold.  
>
>The ergodicity of *Markov chain* is **stronger** than the ergodicity of *shift transformation*. 

- [[Aperiodic Markov Chain]]
- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]
- [[Ergodic Transformation]]

- [different-uses-of-the-word-ergodic](https://mathoverflow.net/questions/74503/different-uses-of-the-word-ergodic/74503)


## Asymptotic Analysis

>[!important] Theorem
>A discrete state Markov chain is **irreducible** and **positive recurrent** having **invariant measure** $\pi$ and transition kernel $K$
>
>-  If the Markov chain is also **aperiodic**, then the limit
>$$ 
> \begin{align}
> \lim_{n\rightarrow \infty} \lvert K^{n}(x, y) -\pi(y) \rvert &= 0, \quad \forall x, y\in \mathcal{X}
> \end{align} 
>$$ 
> 
>- If the Markov chain is **periodic** with *period* $d$, then there exists $r \in \mathbb{N}_{+}$,  $0\le r\le d-1$ such that
>$$ 
> \begin{align}
> K^{n}(x, y) &= 0, \quad \forall x, y\in \mathcal{X}
> \end{align}
> $$ 
> **unless** $n = m\,d + r$ for some $m\in \mathbb{N}_{+}$ and
>$$ 
> \begin{align}
> \lim_{m\rightarrow \infty}\lvert K^{m\,d + r}(x, y) - \pi(y)\,d \rvert &= 0 \quad \forall x, y\in \mathcal{X}
> \end{align}
>$$  
>Note that *periodicity* only appears on **discrete time Markov chain**.
> 

- [[Irreducibility of Markov Chain]]
- [[Positive Recurrent Markov Chain]]
- [[Aperiodic Markov Chain]]
- [[Periodicity of State of Markov Chain]]



>[!info] 
>The existence of one **ergodic atom** is **sufficient** to show **convergence** of transition kernel to invariant measures


>[!important] Theorem
>If $(X_{n})$ is **Harris positive** on **countable state** $\mathcal{X}$, and if there *exists* an **ergodic atom** $\alpha \subset \mathcal{X}$, then *for every* $x\in \mathcal{X}$, 
>$$
>\lim_{ n \to \infty } V\left( K^n(x, \cdot) , \pi \right) := \lim_{ n \to \infty }  \sup_{A \in \mathcal{B}(\mathcal{X})}\lvert K^n(x, A) - \pi(A) \rvert  = 0 
>$$
>where the distance is the **total variation distance** between two measures
>$$
> \begin{align}
> V(\mathcal{P},\mathcal{Q}) &:= \sup_{A \in \mathscr{F}} |\mathcal{P}(A) - \mathcal{Q}(A)| 
> \end{align}
>$$ 

- [[Monte Carlo Statistical Methods by Robert]] pp 231
- [[Positive Recurrent Markov Chain]]
- [[Total Variation between Measures]]

>[!important] Theorem
>If $(X_{n})$ is **positive recurrent aperiodic** Markov chain on **countable state** $\mathcal{X}$, then for any $x\in \mathcal{X}$
>$$
>\lim_{ n \to \infty } V\left( K^n(x, \cdot) , \pi \right) := \lim_{ n \to \infty }  \sup_{A \in \mathcal{B}(\mathcal{X})}\lvert K^n(x, A) - \pi(A) \rvert  = 0 
>$$
>where the distance is the **total variation distance** between two measures
>$$
> \begin{align}
> V(\mathcal{P},\mathcal{Q}) &:= \sup_{A \in \mathscr{F}} |\mathcal{P}(A) - \mathcal{Q}(A)| 
> \end{align}
>$$ 

- [[Positive Recurrent Markov Chain]]
- [[Aperiodic Markov Chain]]
- [[Monte Carlo Statistical Methods by Robert]] pp 234

### Harris Chain

>[!important] Theorem
>If $(X_{n})$ is **Harris positive** and  **aperiodic** Markov chain, then for any *initial distribution* $\mu$
>$$
>\lim_{ n \to \infty } V\left( \mu\,K^n , \pi \right) := \lim_{ n \to \infty }  \sup_{A \in \mathcal{B}(\mathcal{X})}\left\lvert  \int_{x\in \mathcal{X}}K^n(x, A)\mu(dx) - \pi(A)  \right\rvert  = 0 
>$$
>where the distance is the **total variation distance** between two measures
>$$
> \begin{align}
> V(\mathcal{P},\mathcal{Q}) &:= \sup_{A \in \mathscr{F}} |\mathcal{P}(A) - \mathcal{Q}(A)| 
> \end{align}
>$$ 

- [[Positive Recurrent Markov Chain]]
- [[Aperiodic Markov Chain]]

>[!important] Proposition
>If $\pi$ is an **invariant measure** for $\mathcal{P}$, then for any *initial distribution* $\mu$
>$$
>V\left( \mu\,K^n , \pi \right) := \sup_{A \in \mathcal{B}(\mathcal{X})}\left\lvert  \int_{x\in \mathcal{X}}K^n(x, A)\mu(dx) - \pi(A)  \right\rvert  = 0 
>$$
>is decreasing in $n$. 




-----------
##  Recommended Notes and References

- [[Ergodic Theorem for Positive Recurrent Markov Process]]

- [[Aperiodic Markov Chain]]
- [[Irreducibility of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]