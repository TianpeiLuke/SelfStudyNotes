---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning_models/mc
keywords:
  - Markov_properties
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_models
name: Markov Chain
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Markov Chain

>[!important] Definition
>Given a *transition kernel* $K$, a sequence $(X_{t}, t\ge 0)$ of random variables is a **Markov chain** or **Markov Process**, denoted as $(X_{t})$,  if, 
>- for any $t \in \mathbb{N}$, the *conditional distribution* of $X_{t}$ given $(X_{t-1} ,{,}\ldots{,}\,X_{0}) = ( x_{t-1}\,{,}\ldots{,}\,x_{0})$ is **the same as** the *distribution* of $X_{t}$ given $X_{t-1} = x_{t-1}.$
> 
> That is,
>$$
>\begin{align*}
>\mathcal{P}\left(X_{k+1} \in A \;|\; X_{t-1}=x_{t-1} \,{,}\ldots{,}\,X_{0}=x_{0}\right) &= \mathcal{P}\left(X_{k+1} \in A \;|\; X_{t-1}=x_{t-1}\right) \\
>&= \int_{A} K(x_{k}, dx)
\end{align*}
>$$

- [[Markov Chain Transition Kernel]]
- [[Stochastic Process]]

>[!important] Definition
>Let   $(X_{t}, t\in T)$ be a **Markov process**:
>- For each $t\in T$,  $X_{t} \in S$ where $S$ is the **state space**. 
>- If $T = \mathbb{N}$, then the Markov process is called the **discrete-time Markov process**. The state space $S$ is a **countable set** for *discrete-time Markov process*.
>- If $T = \mathbb{R}$, then the Markov process is called the **continuous-time Markov process**. The state space $S$ is also **countable**.
>- If $S$ is **uncountable**, the Markov chain is called **Harris chain**.

- [[Countable Set and Uncountable Set]]


>[!important] Definitions
>**Markov Chain** $(X_t)_t$ is a *probabilistic graphical model* over a *chain graph* $\mathcal{G}=(\mathcal{V}, \mathcal{E}_{C})$,  where each random variable $X_t$ only has **exactly one children** $X_{t+1}$ and **one parent** $X_{t-1}$. Denote the index of variable $t$ as the time. Markov chain  $(X_t)_t$ is also a *stochastic process*. 

>[!important] Definition
>The chain is **time homogeneous**, or simply **homogeneous**, if
>$$
>\mathcal{P}(X_{t_{1}} \,{,}\ldots{,}\, X_{t_{k}} | X_{t_{0}} = x_{t_{0}}) = \mathcal{P}(X_{t_{1} - t_{0}} \,{,}\ldots{,}\, X_{t_{k} - t_{0}} | X_{0} = x_{0})
>$$
>for any $k$, and every $k+1$ multi-index, $t_{0} \leq t_{1} \,{\leq}\ldots{\leq}\,t_{k}.$

## Properties

>[!important]
>The key interpretation of Markov property is that "**given the present, the history and future are independent**."


>[!important] Proposition (Weak Markov property) 
>For *every initial distribution* $X_{0} \sim \mathcal{P}_{0}$ and every (n+1) sample $(X_{0} \,{,}\ldots{,}\, X_{n})$, the following equation is satisfied:
> $$
> \mathbb{E}_{0}\left[h\left(X_{n+1}, X_{n+2}, \ldots \right) | x_{1} \,{,}\ldots{,}\,x_{n} \right] = \mathbb{E}_{x_{n}}\left[h\left(X_{1}, X_{2}, \ldots \right) \right].
> $$ 
> It is seen that the **transition probability** does not depend on the time $t$, i.e. Markov chain is **time-invariant**.



>[!info]
>The **strong Markov property** can be shown that 
>$$
>\mathbb{E}_{0}\left[h\left(X_{\zeta+1}, X_{\zeta+2}, \ldots \right) | x_{1} \,{,}\ldots{,}\,x_{\zeta} \right] = \mathbb{E}_{x_{\zeta}}\left[h\left(X_{1}, X_{2}, \ldots \right) \right]
>$$ 
>for stopping time $\zeta = n$

- [[Strong Markov Property]]
- [[Stopping Time of Markov Chain]]



## Key concepts of Markov Chain

- [[Markov Chain Transition Kernel]]

## Continuous Time Markov Process





-----------
##  Recommended Notes and References

- [[Markov Chain Transition Kernel]]
- [[Martingale]]
- [[Filtration]]

- [[Stochastic Process]]

- [[Monte Carlo Statistical Methods by Robert]]