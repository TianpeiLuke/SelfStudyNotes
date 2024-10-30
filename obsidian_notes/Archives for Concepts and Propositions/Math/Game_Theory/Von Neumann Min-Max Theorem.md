---
tags:
  - concept
  - math/game_theory
  - deep_learning/generative_models
  - math/functional_analysis
  - machine_learning/boosting
keywords:
  - min_max_theorem_game
topics:
  - game_theory
  - functional_analysis
  - optimization
  - deep_learning/generative_models
  - boosting
name: Von Neumann Min-Max Theorem
date of note: 2024-08-04
---

## Concept Definition

>[!important]
>**Name**: Von Neumann Min-Max Theorem

### Min-Max Theorem in Two-Person Zero-Sum Bilinear Game

>[!important] Von Neumann's Min-Max Theorem (Zero-Sum Game)
>Let $X$ and $Y$ be two **probability simplexes**
>- $$X = \left\{ (x_{1}\,{,}\ldots{,}\,x_{n}): \; x_{i} \ge 0,\; \sum_{i=1}^{n}x_{i} = 1 \right\} $$
>- $$Y = \left\{ (y_{1}\,{,}\ldots{,}\,y_{m}): \; y_{i} \ge 0,\; \sum_{i=1}^{m}y_{i} = 1 \right\} $$
>  
>


- [[Mixed Strategy and Finite Strategy Sets]]
- [[Generalized Simplex]]
- [[Normal-Form Games]]


### Min-Max Theorem in Reflective Normed Space

>[!important] Min-Max Theorem (Reflective Normed Space)
>Let $X$ be a **reflective normed space** and let $A$ and $B$ be **compact convex subsets** of $X$ and $X^{*}$, respectively.
>
>Then 
>$$
>\min_{x \in A}\max_{x^{*} \in B} \left\langle  x^{*}\,,\,x    \right\rangle = \max_{x^{*} \in B}\min_{x \in A} \left\langle  x^{*}\,,\,x    \right\rangle
>$$
>where $\left\langle  \cdot\,,\,\cdot    \right\rangle: X^{*} \times X \to \mathbb{R}$ is the *canonical dual pairing.*

^3ea541

- [[Reflexive Normed Space and Bidual of Normed Space]]
- [[Compactness]]
- [[Convex Set]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Canonical Dual Pairing]]

### Min-Max Theorem for Convex-Concave Function

>[!important] Min-Max Theorem (Concave-Convex Function)
>Let $X \subseteq \mathbb{R}^{n}$, $Y \subseteq \mathbb{R}^{m}$ be **compact convex sets** and let $$f: X \times Y \to \mathbb{R}$$ be a **continuous** function that is **convex-concave**, i.e.
>- for every $y\in Y$,  $$f(\cdot, y): X \to \mathbb{R}$$ is **convex**;
>- for every $x\in X$,  $$f(x, \cdot): Y \to \mathbb{R}$$ is **concave**;
>
>Then 
>$$
>\min_{x \in X}\max_{y \in Y} f(x, y) = \max_{y \in Y}\min_{x \in X} f(x, y)
>$$
>

- [[Convex Function]]
- [[Methods of Lagrangian Multipliers]]
- [[Saddle Point of Lagrangian Function]]
- [[Fenchel Duality Theorem]]
- [[Kullback-Leibler Divergence]]




## Explanation





-----------
##  Recommended Notes and References



- [[Nash Equilibrium in Mixed Strategies]]
- [[Mixed Strategy and Finite Strategy Sets]]
- [[Two-Player Finite Game and Matrix Representation]]



- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Norm and Normed Space]]



- [[Game Theory An Introduction by Tadelis]] pp 107
- [[Foundations of Machine Learning by Mohri]] pp 174 - 175
- [[Optimization by Vector Space Methods by Luenberger]] pp 206 - 209
- [[Convex Analysis by Rockafellar]]
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 182, 184, 185, 187, 188, 190, 197, 225, 226
- Wikipedia [Minimax_theorem](https://en.wikipedia.org/wiki/Minimax_theorem)