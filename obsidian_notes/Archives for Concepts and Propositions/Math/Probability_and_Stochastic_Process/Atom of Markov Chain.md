---
tags:
  - concept
  - math/stochastic_process
keywords:
  - atom_markov_chain
topics:
  - stochastic_process
name: Atom of Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Atom of Markov Chain

>[!important] Definition
>Let $(\mathcal{X}, \mathcal{B}[\mathcal{X}])$ be a  *Borel measurable space*.
>
>A *discrete-time Markov chain* $(X_{n})$ on $\mathcal{X}$ has an **atom** $\alpha \in \mathcal{B}[\mathcal{X}]$ if there exists an associated *non-zero measure* $\nu$ such that 
>$$
> K(x, A) = \nu(A), \quad \forall x \in \alpha, \; \forall A \in \mathcal{B}[\mathcal{X}].
>$$

^ca6ce1

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

>[!important] Definition
>If $(X_{n})$ is *$\mu$-irreducible*, the atom is **accessible** when $\mu(\alpha) > 0$ where $\alpha \in \mathcal{B}[\mathcal{X}]$ is an *atom*.

- [[Communicate as Equivalence State Relation for Markov Chain]]

## Explanation

>[!info]
>The concept of *atom* for **Harris chain** (uncountable state Markov chain) extends the *discrete-state Markov chain*.

>[!important]
>It is too strong to apply the condition of atom to every state since it implies that the *transition kernel* is **constant** on *a set of positive measure*.
>
>This leads to the definition of [[Small Set of Markov Chain]]






-----------
##  Recommended Notes and References


- [[Atomic Algebra]]
- [[Small Set of Markov Chain]]


- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 216