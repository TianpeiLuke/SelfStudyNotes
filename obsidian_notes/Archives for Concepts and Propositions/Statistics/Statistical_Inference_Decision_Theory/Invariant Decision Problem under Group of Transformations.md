---
tags:
  - concept
  - statistics/decision_theory
keywords:
  - invariant_decision_under_group
topics:
  - statistics/decision_theory
name: Invariant Decision Problem under Group of Transformations
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Invariant Decision Problem under Group of Transformations

>[!important] Definition
>Let $X\in \mathcal{X}$ be a sample from $\mathcal{P} \in \mathscr{P}$. Let $\mathcal{G}$ be a **group** of *one-to-one transformations* on $X \in \mathcal{X}$ i.e. for any $g_{i} \in \mathcal{G}$, $$g_{1} \circ g_{2} \in \mathcal{G}, \quad g_{i}^{-1} \in \mathcal{G}.$$
>
>A *decision problem* is said to be **invariant under $\mathcal{G}$** if 
>- the *family* $\mathscr{P}$ is **invariant** under $\mathcal{G}$, i.e. $$\bar{g}: \mathscr{P} \to \mathscr{P}$$ is a *one-to-one transformation* for *each $g\in \mathcal{G}$*  such that $$\bar{g}\left(\mathcal{P}_{X} \right) = \mathcal{P}_{g(X)},$$
>- and the *loss function* $L(\mathcal{P}, a)$ is **invariant** under $\mathcal{G}$, i.e. for every $g\in \mathcal{G}$ and $a\in \mathcal{A},$ there exists a *unique* $\psi_{g}(a) \in \mathcal{A}$ such that $$L(\mathcal{P}_{X}, a) = L(\mathcal{P}_{g(X)}, \psi_{g}(a)).$$

- [[Invariant Family under Group of Transformations]]
- [[Statistical Decision Problem]]
- [[Bijective Function and Inverse Function]]
- [[Group]]

>[!important] Definition
>A *decision rule* $T: \mathcal{X} \to \mathcal{A}$ is said to be **invariant** *under* $\mathcal{G}$ if, for *every* $g\in \mathcal{G}$ and *every* $x\in \mathcal{X}$, $$(T \circ g)(x) = (g \circ T)(x).$$

## Explanation

>[!important]
>**Invariance** means that our decision is **not affected** by *one-to-one transformations* of data.






-----------
##  Recommended Notes and References

- [[Population and Sample and Statistical Problem]]
- [[Statistical Decision Problem]]

- [[Topological Group]]
- [[Group]]

- [[Mathematical Statistics by Shao]] pp 119