---
tags:
  - concept
  - probabilistic_graphical_models/theory
keywords:
  - bayesian_network
topics:
  - probabilistic_graphical_model
name: Bayesian Network Distribution to Graph
date of note: 2024-07-19
---

## Concept Definition

>[!important]
>**Name**: Bayesian Network Distribution to Graph

### Minimal I-Map

![[Minimal I-Map#^665356]]

- [[Minimal I-Map]]
### Perfect I-Map

![[Perfect Map for Independence Assertions#^f50db0]]

- [[Perfect Map for Independence Assertions]]

### Identify Undirected Skeleton


>[!important] Lemma
>Let $\mathcal{G}^{*}$ be a **$P$-map** of a distribution $\mathcal{P}$, and let $X$ and $Y$ be two variables such that $X \to Y$ is in $\mathcal{G}^{*}.$
>
>Then for any set $U$ that **does not include** $X$ and $Y$, $$\mathcal{P} \not\vDash \left( X \perp Y \,|\,U\right).$$


>[!important] Lemma
>Let $\mathcal{G}^{*}$ be a **$I$-map** of a distribution $\mathcal{P}$, and let $X$ and $Y$ be two variables that are **not adjacent** in $\mathcal{G}^{*}.$
>
>Then either $$\mathcal{P} \vDash \left( X \perp Y \,|\,\text{Pa}_{\mathcal{G}^{*}}(X)\right)$$ or $$\mathcal{P} \vDash \left( X \perp Y \,|\,\text{Pa}_{\mathcal{G}^{*}}(Y)\right).$$


>[!important] Definition
>Thus, if $X$ and $Y$ are **not adjacent** in $\mathcal{G}^{*}$, then we can find a set $U$ so that  $$\mathcal{P} \vDash \left( X \perp Y \,|\,U\right).$$ We call this set $U$ a **witness** of *their independence*.


### Identify Immoralities



## Explanation





-----------
##  Recommended Notes and References


- [[I-Equivalence between Two Graphs]]
- [[D-Separation in Bayesian Network]]
- [[Minimal I-Map]]
- [[I-Map and Independence Assertion]]
- [[Bayesian Network on Directed Acyclic Graph]]


- [[Markov Network Distribution to Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 78 - 93