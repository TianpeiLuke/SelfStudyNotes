---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
  - statistics/concentration_inequality
keywords: 
topics:
  - machine_learning_theory
  - stochastic_process
  - concentration_inequality
name: Gaussian Complexity
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gaussian Complexity Gaussian Width

>[!important] Definition  (Gaussian Random Vector)
>Let $X := (X_{1} \,{,}\ldots{,}\,X_{n})$ be a sequence of *independent, identically distributed standard Gaussian random variables* $X_{i} \sim \mathcal{N}(0,1).$
>
>For a collection of vectors $\mathcal{A} \subset \mathbb{R}^n$,  the **Gaussian complexity** (or **Gaussian width**) of $\mathcal{A}$ is defined as 
>$$
>w(\mathcal{A}) := \mathbb{E}\left[ \sup_{a\in \mathcal{A}}\left\{ \sum_{i=1}^{n}a_{i}X_{i} \right\}    \right] := \mathbb{E}\left[ \sup_{a\in \mathcal{A}}\left\langle  a\,,\,X    \right\rangle  \right] 
>$$

- [[Gaussian Random Vector]]

>[!important] Definition (Gaussian Process)
>Let $(T,d)$ be a metric space, and $(X_{t}, t\in T)$ be a *standard Gaussian process* indexed by $T$.
>
>The **Gaussian complexity** (or **Gaussian width**) of $T$ is defined as 
>$$
>w(T) := \mathcal{G}(T) := \mathbb{E}\left[ \sup_{t\in T}X_{t}   \right]
>$$

- [[Gaussian Process]]

## Explanation

>[!important]
>It is important to realize that
>$$
>Z = f_{\mathcal{A}}(X) :=\sup_{a\in \mathcal{A}}\left\langle  a\,,\,X    \right\rangle  
>$$
>is a **sub-Gaussian random variable**.
>
>Moreover, $f_{\mathcal{A}}: x \to \sup_{a\in \mathcal{A}}\left\langle  a\,,\,x    \right\rangle$ is a **Lipschitz function** with **Lipschtiz constant** $\sup_{a \in \mathcal{A}}\lVert a \rVert_{2}$
>$$
>\lvert f_{\mathcal{A}}(x) - f_{\mathcal{A}}(y)\rvert \le \left\langle  a^{*}\,,\, x -y   \right\rangle \le \sup_{a\in \mathcal{A}}\lVert a \rVert\, \lVert x - y \rVert  
>$$


- [[Lipschitz Continuous Function]]

![[Representation of Gaussian Random Function in Hilbert Space#^3e7bb2]]

- [[Representation of Gaussian Random Function in Hilbert Space]]

>[!important]
>By **Karhunen-Loeve expansion** of Gaussian process on separable Hilbert space, we can represent the Gaussian complexity  as
>$$
>\mathcal{G}(T) :=  \mathbb{E}\left[ \sup_{t\in T}X_{t}   \right] = \mathbb{E}\left[ \sup_{t\in T}\left\langle \varphi_{t} \,,\, \xi   \right\rangle   \right]
>$$
>where 
>$$
>X_{t} = \left\langle  \varphi_{t} \,,\,  \xi  \right\rangle := \sum_{i=1}^{\infty} \xi_{i} \varphi_{t}^{i}
>$$
>and $\xi \in \ell^2$ is an infinite sequence of i.i.d. standard Gaussian random variables and $\varphi_{t}^{i}:= \varphi^{i}(t)$ is **the i-th basis function** in Hilbert space.




-----------
##  Recommended Notes and References




- [[Gaussian Process]]
- [[Empirical Process and Empirical Measure]]

- [[Rademacher Complexity]]

- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]