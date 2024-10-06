---
tags:
  - concept
  - math/functional_analysis
  - optimization/linear_optimization
  - optimization/convex_optimization
keywords:
  - krein_milman_lemma
  - krein_milman_theorem
  - extreme_points
  - convex_set
  - locally_convex_space
topics:
  - functional_analysis
name: Krein-Milman Lemma and Krein-Milman Theorem
date of note: 2024-06-21
---

## Concept Definition

>[!important]
>**Name**: *Krein-Milman Lemma* and *Krein-Milman Theorem*

>[!important] Lemma
>Let $K$ be a *nonempty*, **compact**, **convex** subset of a **locally convex** *topological vector space* $\mathcal{X}$ and $$\psi: \mathcal{X} \to \mathbb{R}$$ be **linear** and **continuous**. 
>
>Then the set of points in $K$ at which $\psi$ takes its **maximum value** on $K$ is an **extreme subset** of $K$.

^5c9b4d

- [[Extreme Points of Convex Set of Locally Convex Space]]
- [[Bounded Linear Functional]]
- [[Basic Solution for Linear Optimization]]
- [[Compactness]]
- [[Convex Set]]
- [[Locally Convex Space]]

>[!important] Krein-Milman Lemma
>Let $K$ be a *nonempty*, **compact**, **convex** subset of a **locally convex** *topological vector space* $\mathcal{X}$.
>
>Then $K$ has an **extreme point**.

^5eae27

- [[Zorn Lemma]]
- [[Separation Theorem]]
- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]
- [[Existence of Extreme Point in Polyhedron]]

>[!important] Krein-Milman Theorem
>Let $K$ be a *nonempty*, **compact**, **convex** subset of a **locally convex** *topological vector space* $\mathcal{X}$.
>
>Then $K$ is the **closed convex hull** of its **extreme points**.

^8e5fc2

- [[Convex Hull]]
- [[Banach-Alaoglu Theorem]]
- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]

![[Polyhedron and Polytope#^9235c5]]

- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Introduction to Linear Optimization by Bertsimas]] pp 68

## Explanation

>[!info]
>To apply the **Krein-Milman Theorem** it is necessary to establish *criteria for identifying which subsets* of a *locally convex topological space* are **compact**. 
>
>In particular, to identify which *convex subsets* of a *normed linear space* $\mathcal{X}$ are **weakly compact** and which *convex subsets* of its **dual space** $\mathcal{X}^{*}$ are **weak$^*$ compact**. 
>
>[[Banach-Alaoglu Theorem]] tells us that the **closed unit ball** of the **dual** *of a normed linear space* $\mathcal{X}$ is **weak$^*$ compact**. 
>- Therefore every **bounded** *convex subset* of $\mathcal{X}^{*}$ that is **weak$^*$ closed** is **weak$^*$ compact**. 
>- From [[Banach-Alaoglu Theorem]] and [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]] we then infer that any **strongly closed bounded** *convex* subset of a **reflexive** *Banach space* is **weakly compact.** 

- [[Reflexive Normed Space and Bidual of Normed Space]]



-----------
##  Recommended Notes and References



- [[Extreme Points of Convex Set of Locally Convex Space]]
- [[Bounded Linear Functional]]
- [[Compactness]]
- [[Convex Hull]]
- [[Closed Set]]
- [[Convex Set]]
- [[Locally Convex Space]]

- [[Topological Vector Space]]
- [[Vector Space over a Field]]

- [[Real Analysis by Royden]] pp 295 - pp 296
- [[Partial Differential Equations by Evans]]