---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - statistics/decision_theory
keywords:
  - admissible_decision
topics:
  - statistics/decision_theory
name: Admissibility of Statistical Decision
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Admissibility of Statistical Decision


![[Statistical Decision Problem#^1e4cc1]]

![[Statistical Decision Problem#^e4b559]]

![[Statistical Decision Problem#^36cede]]


>[!important] Definition
>Let $\mathcal{R}$ be a *class of decision rules* (*randomized* or *nonrandomized*). 
>
>A decision rule $T \in \mathcal{R}$ is called **$\mathcal{R}$-admissible** (or **admissible** when $\mathcal{R}$ contains *all possible rules*) if and only if there *does not exist* any $S \in \mathcal{R}$ that is *better* than $T$ (in terms of the *risk*).
>
>That is, for any $S \in \mathcal{R}$
>$$R_{T}\left(\mathcal{P}\right) \le R_{S}\left(\mathcal{P}\right), \quad \forall \mathcal{P} \in \mathscr{P}.$$

- [[Statistical Decision Problem]]


## Explanation

![[Statistical Decision Problem#^a44cc3]]

>[!info]
>If a decision rule $T^{*}$ is **$\mathcal{R}$-optimal**, then it is **$\mathcal{R}$-admissible**.
>
>If $T\in \mathcal{R}$ is **$\mathcal{R}$-admissible** and $S \in \mathcal{R}$ is **$\mathcal{R}$-optimal**, then $T$ and $S$ are **equivalent**.






-----------
##  Recommended Notes and References

- [[Statistical Decision Problem]]



- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 116