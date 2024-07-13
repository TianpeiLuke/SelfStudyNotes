---
tags:
  - concept
  - machine_learning/theory
  - reinforcement_learning/theory
  - statistics/decision_theory
  - math/stochastic_process
keywords:
  - sequential_decision_process
  - stochastic_process
  - statistical_decision_theory
topics:
  - machine_learning_theory
name: Sequential Decision Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sequential Decision Process

![[Statistical Decision Problem#^1e4cc1]]


>[!important] Definition
>Let $X_{1}, X_{2}, \ldots$ be a *stochastic process*, and $\mathcal{X}_{i}$ be the state space for $X_{i}$. Denote $X_{1:t} := (X_{1} \,{,}\ldots{,}\,X_{t})$. For every $t\in T$,  the *joint probability density* $f_{t}(x_{1:t}\,;\, \theta)$  is from a *parametric family* $\mathcal{P}_{\Theta}$ where $\theta\in \Theta$.
>- If $X_{i}$ are *independent identically distribution* with p.d.f. $f_{\theta}(x)$, we say that $X_{1}, X_{2}, \ldots$ is a **sequential sample** from the density $f_{\theta}(x)$. And the joint probability is the *product measure* $$f_{t}(x_{1:t}\,;\, \theta) = \prod_{i=1}^{t}f_{\theta}(x_{t})$$
>
>A **sequential decision** is a *sequence* of **actions** $(a_{1}, a_{2} \,{,}\ldots{,}\,)$, where at each  $t\in T,$ an action $a_{t} \in \mathcal{A}$ is taken after observing $X_{1:t}$.
>
>- The index set $T$ can be *continuous* or *discrete*
>	- If $T \subset \mathbb{Z}_{+}$ is **discrete**, the corresponding index $t\in T$ is called a **decision epoch.**
>	- If $T = \{ 1 \,{,}\ldots{,}\, N \}$ with finite $N$, the decision problem is called a **finite horizon problem**.
>	- If $T = \{ 1 \,{,}\ldots \}$ is infinite, the decision problem is called an **infinite horizon problem**.
>- Denote $\mathcal{A}_{t}$ as the *set of* **allowable actions** *at time* $t$. Let $\mathscr{F}_{\mathcal{A}}^{t}$ be a **$\sigma$-field** on $\mathcal{A}_{t}$. 
>	- Define $\mathcal{A} = \bigcup_{t\in T}\mathcal{A}_{t}$ be the **set of allowable actions.** Let $\mathscr{F}_{\mathcal{A}}$ be a **$\sigma$-field** on $\mathcal{A}$. 
>	- Then the *measurable space* $(\mathcal{A}, \mathscr{F}_{\mathcal{A}})$ is called the **action space**. 
>- Denote $\mathcal{X}^{t} = \prod_{s=1}^{t}\mathcal{X}_{s}$ be the state space for $X_{1:t} := (X_{1} \,{,}\ldots{,}\,X_{t})$ and $\mathscr{F}_{\mathcal{X}}^{t}$ be a *$\sigma$-field* on $\mathcal{X}^{t}$. 
>	- Let $\mathcal{X} = \prod_{t\in T}\mathcal{X}_{t}$ be the *state space* of $(X_{t}, t\in T)$ and $\mathscr{F}_{\mathcal{X}}$ be a *$\sigma$-field* on $\mathcal{X}$. 


^827f09

- [[Stochastic Process]]
- [[Statistical Decision Problem]]
- [[Parametric Models]]
- [[Statistical Decision Theory by Berger]] pp 282


### Decision Rules

>[!important] Definition
>For each $s\in T$, a **deterministic** *decision rule* is said to be **Markovian** if it is a *measurable function* (a *statistic*) $$\delta_{s}: (\mathcal{X}^{s}, \mathscr{F}_{\mathcal{X}}^{s}) \to (\mathcal{A}_{s}, \mathscr{F}_{\mathcal{A}}^{s})$$  
>
>This decision rule is said to be **Markovian (memoryless)** because it depends on *previous system states* and *actions* only through the *current state* of the system, and **deterministic** because it chooses an action with certainty.

>[!important] Definition
>For each $s\in T$, a *deterministic decision rule* is said to be **history dependent** if it is a *measurable function* (a *statistic*) $$\delta_{s}: (\mathcal{H}^{s}, \mathscr{F}_{\mathcal{H}}^{s}) \to (\mathcal{A}_{s}, \mathscr{F}_{\mathcal{A}}^{s})$$  
>where 
>$$
>\mathcal{H}^s = \prod_{i=1}^{s}\mathcal{X}_{i}\;\times \prod_{i=1}^{s-1}\mathcal{A}_{i},\quad h_{s} := \left(x_{1}, a_{1} \,{,}\ldots{,}\,x_{s-1}, a_{s-1}, x_{s}\right) \in \mathcal{H}^s.
>$$

- [[Markov Decision Processes by Puterman]] pp 21

### Loss for Sequential Decision

![[Statistical Decision Problem#^e4b559]]

>[!important] Definition
>Similar to the statistical decision theory, the **loss function** $L$ is defined as 
>$$
>L: \Theta \times \mathcal{A} \times T \to [0, \infty)
>$$
>and 
>- is *Borel* on $(\mathcal{A}_{s}, \mathscr{F}_{\mathcal{A}}^s)$ for each $\theta\in \Theta$ and $s \in T$.
>  
>A special case is for i.i.d samples $X_{1:t}$, where 
>$$
>L(\theta, a, t) = \sum_{s=1}^{t}L(\theta, a)
>$$  






## Explanation





-----------
##  Recommended Notes and References


- [[Markov Decision Process]]

- [[Statistical Decision Problem]]
- [[Sequential Importance Sampling]]

- [[Product Measure]]
- [[Empirical Process and Empirical Measure]]


- [[Reinforcement Learning An Introduction by Sutton]]
- [[Markov Decision Processes by Puterman]] pp 36
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Statistical Decision Theory by Berger]] pp 282



- [[Probability and Measure by Billingsley]]
