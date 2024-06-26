---
tags:
  - concept
  - math/stochastic_process
keywords:
  - time-reversible_markov_chain
  - detailed_balance_equation
topics:
  - stochastic_process
name: Time-Reversible Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Time-Reversible Markov Chain

>[!important] Definition
>A *discrete-state Markov chain* $(X_t)_t$ is called **time-reversible**, if it has *invariant measure* $\pi$ and the *detailed balance equation* is satisfied:
>$$
> \begin{align}
> \pi(x)K(x, y) &=  \pi(y)K(y, x),\quad \forall x, y\in \mathcal{X}.  
> \end{align}
>$$ 

- [[Detailed Balance Equation]]
- [[Invariant Measure and Stationary Distribution]]


>[!important] Definition
>The **reversed process** $(Y_{n})_n := (X_{T-n})_{n}$ is a *Markov chain* and its *transition probability*
>$$ 
> \begin{align}
> Q(x,y) &= \frac{\pi(y)K(y,x)}{\pi(x)}
> \end{align}
>$$  
>Note that $(Y_{n})_n$ and $(X_n)_n$ are **statistically equivalent** since $Q(x,y) = K(x,y)$.


## Explanation



## Properties

>[!important] Proposition
>For states $(x_0,x_1,\ldots, x_{m}) \subset \mathcal{X}$ of a **time-reversible** Markov chain, the **cycle-tour property** holds, i.e.
>$$
> \begin{align}
> & \mathbb{E}\left[ \tau_{x_1} | X_0 = x_0 \right]  + \mathbb{E}\left[ \tau_{x_2} | X_0 = x_1 \right] + \ldots + \mathbb{E}\left[ \tau_{x_0} | X_0 = x_m \right] \nonumber \\[10pt]
> &= \mathbb{E}\left[ \tau_{x_m} | X_0 = x_0 \right] + \mathbb{E}\left[ \tau_{x_{m-1}} | X_0 = x_m \right] + \ldots +  \mathbb{E}\left[ \tau_{x_0} | X_0 = x_1 \right]
> \end{align}
>$$ 

- [[Stopping Time of Markov Chain]]


## Ergodic Chain

>[!important] Theorem
>An **ergodic** Markov chain $(X_n)_n$ for which $K(x,y) =0$ whenever $K(y, x) = 0$ is **time-reversible** *if and only if* starting from *any state* $x$, *any path back to* $x$ has the 
>**same probability** as its **reverse path**. 
>
>That is, for path $$x \rightarrow x_1\rightarrow x_2 \rightarrow \ldots \rightarrow x_k \rightarrow x$$ and its *reverse path* $$x \leftarrow x_1 \leftarrow x_2 \leftarrow \ldots  \leftarrow x_k \leftarrow x,$$
>$$
> \begin{align}
> K(x, x_1)\,K(x_1, x_2)\,\ldots\,K(x_k, x) &= K(x, x_k)\,\ldots\,K(x_2, x_{1})\,K(x_1, x), \quad \forall x,x_1,\ldots, x_k\in \mathcal{X}
> \end{align} 
>$$ 

- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]

## Criterion for Reversibility for Discrete State Markov Chain

>[!important] Theorem
>Let $(X_{n})$ be *discrete state Markov chain* with transition kernel $K$ and countable state space $\mathcal{X}$.  Suppose $\pi$ is a *probability distribution* on $\mathcal{X}$.
>
>If there exists   a **stochastic matrix** $Q$  (i.e. row sum is one) indexed by $\mathcal{X}$ such that 
>$$
> \pi(x)\,Q(x, y) = \pi(y)\,K(y, x), \quad \forall x,y\in \mathcal{X}
>$$
>
>Then $\pi$ is an **invariant distribution** with respect to $K$.




-----------
##  Recommended Notes and References

- [[Detailed Balance Equation]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]