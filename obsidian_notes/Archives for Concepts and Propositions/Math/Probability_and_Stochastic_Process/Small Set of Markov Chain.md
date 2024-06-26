---
tags:
  - concept
  - math/stochastic_process
keywords:
  - small_set_markov_chain
topics:
  - stochastic_process
name: Small Set of Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Small Set of Markov Chain


![[Atom of Markov Chain#^ca6ce1]]


>[!important] Definition
>Let $(X_{n})$ be a *discrete-time Markov chain* with *transition kernel* $K$.
>
>A set $C$ is **small** if there exists $n\in \mathbb{N}$ and a *nonzero measure* $\nu_{n}$ such that 
>$$
>K^{n}(x, A) \ge \nu_{n}(A)\,
>$$
>for all $x\in C$ and $A \in \mathcal{B}[\mathcal{X}]$.

- [[Atom of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

## Explanation

>[!info]
>It is too strong to apply the condition of **atom** to every state since it implies that the *transition kernel* is **constant** on *a set of positive measure*.

>[!important]
>The small set is a **generalization of atom**, with **minorizing condition**.
>
>In particular, there exists a set $C \in \mathcal{B}[\mathcal{X}]$, a constant $\epsilon >0$, and a *probability measure* (called **the minorizing measure**) $\nu$ such that 
>$$
>K(x, A) \ge \epsilon\,\nu(A), \quad \forall x \in C, \; \forall A\in \mathcal{B}[\mathcal{X}].
>$$  
>
>The probability measure $\nu$ thus appears as a **constant component** of the *transition kernel* on $C$.

>[!info]
>In sufficiently regular Markov chain, every **compact** set is small.

- [[Compactness]]

## Sufficient Condition

>[!important] Theorem
>Let $(X_{n})$ be a **$\mu$-irreducible chain** on $\mathcal{X}$ and $\mathcal{B}[\mathcal{X}]$ be the Borel $\sigma$-algebra of $\mathcal{X}$. 
>
>For every set $A \in \mathcal{B}[\mathcal{X}]$ such that $\mu(A) >0$, there exists $n \ge 1$ and a **small set** $C \subset A$ such that the associated **minorizing measure** satisfies $\nu_{n}(C) > 0$.
>
>Moreover, $\mathcal{X}$ can be **decomposed** in a **denumerable partition** of **small sets**. 




-----------
##  Recommended Notes and References

- [[Periodicity of State of Markov Chain]]
- [[Atomic Algebra]]



- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 216