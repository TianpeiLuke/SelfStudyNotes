---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - d_separation_graphical_model
  - conditional_independence
topics:
  - probabilistic_graphical_model
name: Soundness and Faithfulness of D-Separation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Soundness and Faithfulness of D-Separation

![[D-Separation in Graphical Model#^ede428]]

- [[D-Separation in Graphical Model]]
- [[Walk and Trail in Graph]]

### Soundness 

>[!important] Definition
>The **soundness of d-separation** implies that  $$ \left(\exists X, Y, Z\right) \quad \text{d-sep}_{\mathcal{G}}(X ; Y \,|\,Z) \implies  (X \perp Y \,|\,Z).$$

- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]

>[!important] Theorem
>If a distribution $\mathcal{P}$ **factorizes** according to $\mathcal{G}$, then 
>$$
>\mathcal{I}(\mathcal{G}) := \left\{ (\mathcal{X} \perp \mathcal{Y} \,|\, \mathcal{Z}):\; \text{d-sep}_{\mathcal{G}}(\mathcal{X}; \mathcal{Y} \,|\, \mathcal{Z}) \right\} \subseteq \mathcal{I}(\mathcal{P}).
>$$
>In other words, **any independence** reported by **d-separation** is *satisfied* by the underlying **distribution**.

### Faithfulness 


>[!important] Definition
>A distribution $\mathcal{P}$ is **faithful** to $\mathcal{G}$ if $$\left(\forall X, Y, Z\right) \quad  (X \perp Y \,|\,Z) \implies \text{d-sep}_{\mathcal{G}}(X ; Y \,|\,Z).$$
>
>In other word, *any independence in* $\mathcal{P}$ is reflected in the *d-separation properties* of the graph.

- [[D-Separation in Graphical Model]]
- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]


>[!important] Theorem
>Let $\mathcal{G}$ be a **Bayesian network structure**. 
>
>If $X$ and $Y$ are **not d-separated** given $Z$ in $\mathcal{G}$, then $X$ and $Y$ are **dependent** given $Z$ in **some distribution** $\mathcal{P}$ that *factorizes* over $\mathcal{G}$.
>$$
> \mathcal{G} \nvDash \text{d-sep}_{\mathcal{G}}(X ; Y \,|\,Z) \implies (\exists \mathcal{P} \; \mathcal{P} \text{ factorizes over }\mathcal{G})\;\; X \not\perp Y\,|\,Z.
>$$



>[!important] Theorem
>For *almost all* distributions $\mathcal{P}$ that **factorize** over $\mathcal{G}$, that is, for all distributions except for a set of *measure zero* in the space of CPD *parameterizations*, we have that $$\mathcal{I}(\mathcal{P}) = \mathcal{I}(\mathcal{G}).$$



## Explanation




-----------
##  Recommended Notes and References


- [[D-Separation in Graphical Model]]
- [[Separation of Graph]]
- [[I-Map and Independence Assertion]]
- [[Conditional Independence]]
- [[Bayesian Network on Directed Acyclic Graph]]


- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 69
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 562 - 564