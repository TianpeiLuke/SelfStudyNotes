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

### Min-Max Theorem in Two-Person Zero-Sum Game

>[!important] Von Neumann's Min-Max Theorem (Zero-Sum Game)
>Consider a **two player zero-sum game** where the *payoff functions* are defined by the matrix $$A = [\ell(i,j)]_{i,j} \in \mathbb{R}^{n\times m}$$
>where 
>- $\ell(i,j)$ is the **loss** when the row player chooses action $i\in [n]$, and column player chooses action $j\in [m]$
>- The **row player**'s objective is to **minimize the loss function**
>- The **column player**'s objective is to **maximize the loss function**
>
>Assume that 
>- the *row player* chooses a **mixed strategy**  $$p \in  \mathcal{P} :=  \left\{ (p_{1}\,{,}\ldots{,}\,p_{n}): \; p_{i} \ge 0,\; \sum_{i=1}^{n}p_{i} = 1 \right\} $$
>- and *column player* chooses a **mixed strategy** $$q \in \mathcal{Q} := \left\{ (q_{1}\,{,}\ldots{,}\,q_{m}): \; q_{i} \ge 0,\; \sum_{i=1}^{m}q_{i} = 1 \right\} $$
>
>Define the **expected payoff**  as $$\bar{\ell}(p, q) := \sum_{i=1}^{n}\sum_{j=1}^{m}p_{i}\,q_{j}\,\ell(i,j) := \left\langle  p\,,\,Aq    \right\rangle$$
>
>Then the following **min-max equlity** holds
>$$
>\min_{p \in \mathcal{P}}\max_{q\in \mathcal{Q}}\left\langle  p\,,\,Aq    \right\rangle = \max_{q\in \mathcal{Q}}\min_{p \in \mathcal{P}}\left\langle  p\,,\,Aq    \right\rangle
>$$
>where
>- The common value of the *left-hand* and *right-hand* sides is called the **value of the game**, which is denoted as $V$.
>- The mixed strategy profile $$\pi = p^{*} \times q^{*}$$ that attains the *value of the game* is called a **Nash equilibrium.**
>- The above equality is equivalent to $$\max_{q' \in \mathcal{Q}}\bar{\ell}(p^{*}, q') = \min_{p' \in \mathcal{P}}\bar{\ell}(p', q^{*}) = \bar{\ell}(p^{*}, q^{*}) := V$$

^d1aa27


- [[Mixed Strategy and Finite Strategy Sets]]
- [[Generalized Simplex]]
- [[Normal-Form Games]]
- [[Two-Player Finite Game and Matrix Representation]]
- [[Expected Payoff of Pure Strategy Against Mixed Strategy]]
- [[Nash Equilibrium in Mixed Strategies]]
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 181 - 184


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
- [[Optimization by Vector Space Methods by Luenberger]] pp 206 - 209

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

^8777e4

- [[Convex Function]]
- [[Methods of Lagrangian Multipliers]]
- [[Saddle Point of Lagrangian Function]]
- [[Fenchel Duality Theorem]]
- [[Kullback-Leibler Divergence]]
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 185 - 186



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
- [[Boosting Foundations and Algorithms by Schapire]] pp 157 - 159
- Wikipedia [Minimax_theorem](https://en.wikipedia.org/wiki/Minimax_theorem)