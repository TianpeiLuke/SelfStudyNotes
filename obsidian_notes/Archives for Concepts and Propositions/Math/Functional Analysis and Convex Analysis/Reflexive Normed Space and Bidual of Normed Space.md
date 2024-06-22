---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/measure_theory
keywords:
  - reflexive_banach_space
  - reflexive_normed_space
topics:
  - real_analysis
  - functional_analysis
  - measure_theory
name: Reflexive Normed Space
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Reflexive Normed Space

>[!important] Definition
>Let $\mathcal{X}$ be a *normed vector space*. 
>
>The *linear operator* $$J: \mathcal{X} \to \left(\mathcal{X}\right)^{* *}$$ defined by
>$$
>J(x)[f] := f(x), \quad \forall x\in \mathcal{X}, \; f\in \mathcal{X}^{*}
>$$
>is called the **natural embedding** of $\mathcal{X}$ into $\left(\left(\mathcal{X}\right)^{*}\right)^{*}$.

- [[Evaluation Functional]]
- [[Injective Function]]
- [[Canonical Inclusion]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Norm and Normed Space]]

>[!important] Definition
>Let $\mathcal{X}$ be a *normed vector space*. Let $J: \mathcal{X} \to \left(\mathcal{X}\right)^{* *}$ be the *natural embedding* of $\mathcal{X}$ into $\left(\mathcal{X}\right)^{* *}$, which is defined by $J(x)[f] := f(x), \quad \forall x\in \mathcal{X}, \; f\in \mathcal{X}^{*}.$
>
>The space $\mathcal{X}$ is said to be **reflexive** if $$J(\mathcal{X}) = \left(\left(\mathcal{X}\right)^{*}\right)^{*}.$$
>
>It is customary to denote $\left(\left(\mathcal{X}\right)^{*}\right)^{*}$ as $\left(\mathcal{X}\right)^{**}$, and call $\mathcal{X}^{* *}$ the **bidual** of $\mathcal{X}$.

## Explanation

>[!important]
>$J(x): f \mapsto f(x)$ is an [[Evaluation Functional]].
>
>Thus the mapping $J: x \to f(x)$ for any $f\in \mathcal{X}^{*}$ is an **one-to-one mapping**

- [[Injective Function]]

>[!important]
>If $\mathcal{X}$ is **reflective**, it is **isometric isomorphic** to its **bidual**
>$$
>\mathcal{X} \simeq \left(\mathcal{X}\right)^{* *}
>$$
>
>In general, it is **embedded** in its **bidual**
>$$
>\mathcal{X} \xhookrightarrow{} \left(\mathcal{X}\right)^{* *}
>$$
>
>On the other hand, the **converse is not true** since there exists **isomorphism** between $\mathcal{X}$ and its *bidual*, but it is not reflexive.
>
>Being reflexive requires **the natural embedding** being *isometry and isomorphism*.

- [[Isometry and Isometric isomorphism]]
- [[Canonical Inclusion]]



## Propositions

>[!important] Proposition
>A *normed vector space* is **reflexive** *if and only if* the **weak** and **weak$^{*}$ topologies** on $\mathcal{X}^{*}$ are the same.

- [[Weak Topology of Banach Space]]
- [[Weak-star Topology of Banach Space]]

>[!important] Proposition
>Let $\mathcal{X}$ be a *normed vector space*. 
>
>Then the **natural embedding** $J$ of $\mathcal{X}$ into $\left(\left(\mathcal{X}\right)^{*}\right)^{*}$, i.e. $$J(x)[f] := f(x), \quad \forall x\in \mathcal{X}, \; f\in \mathcal{X}^{*}$$ is an **isometry**.

- [[Isometry and Isometric isomorphism]]



-----------
##  Recommended Notes and References


- [[Norm and Normed Space]]
- [[Banach Space]]

- [[Dual Normed Space and Dual Banach Space]]

- [[Evaluation Functional]]
- [[Canonical Inclusion]]
- [[Injective Function]]


- [[Real Analysis by Royden]]  pp 276