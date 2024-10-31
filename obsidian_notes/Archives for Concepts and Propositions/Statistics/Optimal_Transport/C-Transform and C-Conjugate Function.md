---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - c_conjugate
  - c_transform
topics:
  - information_theory
  - information_geometry
  - optimization
name: C-Transform and C-Conjugate Function
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: C-Transform and C-Conjugate Function


>[!important] Definition
>Given $\mathcal{X}$ and $\mathcal{Y}$ and a cost function $c: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}_{+}$.
>
>Define a **$c$-transform (c-conjugate)**  function of $f: \mathcal{X}\to \mathbb{R}$ as $g: \mathcal{Y} \to \mathbb{R}$ such that 
>$$
>g(y) = f^c(y) := \inf_{x \in \mathcal{X}}\{ c(x, y) - f(x) \}, \;\forall y\in \mathcal{Y}.
>$$
>Denote the **$c$-conjugate** of $f$ as $f^c$.

- [[Convex Conjugate Function]]

>[!important] Definition
>A function $f: \mathcal{X}\to \mathbb{R}$ is **$c$-concave** if there exists a function $g: \mathcal{Y} \to \mathbb{R}$ such that 
>$$
>f = \inf_{y \in \mathcal{Y}}\{ c(x, y) - g(y) \}
>$$
>
>Define $c$-conc$(\mathcal{X})$ as the space of **c-concave functions**. 

>[!important] Definition
>A function $g: \mathcal{Y}\to \mathbb{R}$ is **$\bar{c}$-concave** if there exists a function $f: \mathcal{X} \to \mathbb{R}$ such that 
>$$
>g = \inf_{x \in \mathcal{X}}\{ c(x, y) - f(x) \}
>$$
>
>Define $\bar{c}$-conc$(\mathcal{Y})$ as the space of **$\bar{c}$-concave functions**. 

## Explanation













-----------
##  Recommended Notes and References


- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]]