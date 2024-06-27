---
tags:
  - concept
  - statistics/decision_theory
keywords:
  - invariant_family_group_transform
topics:
  - statistics/decision_theory
name: Invariant Family under Group of Transformations
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Invariant Family under Group of Transformations

>[!important] Definition
>Let $X\in \mathcal{X}$ be a sample from $\mathcal{P} \in \mathscr{P}$. Let $\mathcal{G}$ be a **group** of *one-to-one transformations* on $X \in \mathcal{X}$ i.e. for any $g_{i} \in \mathcal{G}$, $$g_{1} \circ g_{2} \in \mathcal{G}, \quad g_{i}^{-1} \in \mathcal{G}.$$
>
>A *family* of distributions $\mathscr{P}$ is said to be **invariant under $\mathcal{G}$** if $$\bar{g}: \mathscr{P} \to \mathscr{P}$$ is a *one-to-one transformation* for *each $g\in \mathcal{G}$*  such that $$\bar{g}\left(\mathcal{P}_{X} \right) = \mathcal{P}_{g(X)}$$ where $\mathcal{P}_{X} := X_{*}\mathcal{P}$ is the *distribution* of sample $X$.

- [[Population and Sample and Statistical Problem]]
- [[Probability Distribution of Random Variable]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Bijective Function and Inverse Function]]
- [[Group]]

## Explanation

>[!info]
>$\mathscr{P}$ is **invariant** under $\mathcal{G}$ if and only if for each $g\in \mathcal{G}$, 
>- the **distribution of $g(X)$** is also *in the family* $\mathscr{P}$ and 
>- the map from distribution of $X$ to distribution of $g(X)$, $$\mathcal{P}_{X} \mapsto \mathcal{P}_{g(X)}$$  is **bijective** 





-----------
##  Recommended Notes and References

- [[Population and Sample and Statistical Problem]]
- [[Statistical Decision Problem]]

- [[Topological Group]]
- [[Group]]

- [[Mathematical Statistics by Shao]] pp 119