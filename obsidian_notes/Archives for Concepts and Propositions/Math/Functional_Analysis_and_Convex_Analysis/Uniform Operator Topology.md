---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - uniform_operator_topology
  - norm_topology
topics:
  - functional_analysis
  - topology
name: Uniform Operator Topology
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Uniform Operator Topology

>[!important] Definition
>Let $X$ and $Y$ be **Banach space** and $\mathcal{L}(X, Y)$ be the *space of bounded linear operators* from $X$ to $Y$.  
>
>$\mathcal{L}(X, Y)$ is a **Banach space** with **norm**
>$$
> \begin{align*}
> \lVert T \rVert  &= \sup_{x \neq 0}\frac{\lVert Tx \rVert_{Y} }{\lVert x \rVert_{X} }
> \end{align*}
>$$  
>
>The *induced norm topology* on $\mathcal{L}(X, Y)$ is called the **uniform operator topology** (or **norm topology**). 

- [[Banach Space]]
- [[Norm Topology]]
- [[Space of Bounded Linear Operators]]

## Explanation

>[!important]
>The **basis** for **uniform operator topology** consists of $\epsilon$-balls
>$$
>B_{\lVert \cdot \rVert }(T, \epsilon):= \left\{ S \in \mathcal{L}(X, Y): \lVert S - T \rVert < \epsilon   \right\},
>$$
>for all $T \in \mathcal{L}(X, Y)$, $\epsilon > 0$.

- [[Metric Topology and epsilon-ball]]
- [[Basis of Topology]]


>[!important]
>Uniform operator topology need the *both* **domain $X$ and codomain $Y$ of operator** to be **topological** and *each* has a **norm topology**.

>[!important]
>$\mathcal{L}(X, Y)$ is a **metric space** under **norm (uniform operator) topology**.

- [[Metric Space]]

>[!important]
>Denote the convergence of $T_{n}$ to $T$ under *uniform operator topology* as $$T_{n} \stackrel{\lVert \cdot \rVert }{\to} T,$$ which is defined as
>$$
>\lVert T_{n} - T \rVert \to 0.
>$$
>In other word, the **uniform convergence**
>$$
>\sup_{\lVert x \rVert_{X} \le 1}\lVert T_{n}x - Tx \rVert_{Y} = \sup_{\lVert x \rVert_{X} \le 1}\sup_{\lVert f \rVert_{Y^{*}} \le 1}\lvert f(T_{n}x) - f(Tx) \rvert \to 0
>$$

- [[Uniform Convergence]]


## Comparison

>[!important]
>$$
>\begin{align*}
> \text{norm (uniform operator) topology } \subseteq\\
> \text{strong operator topology } \subseteq \\
> \text{weak operator topology }
\end{align*}
>$$

- [[Uniform Operator Topology]]
- [[Strong Operator Topology]]
- [[Weak Operator Topology]]



-----------
##  Recommended Notes and References

- [[Norm Topology]]
- [[Banach Space]]
- [[Norm Topology]]
- [[Space of Bounded Linear Operators]]

- [[Topology of Set]]

- [[Strong Operator Topology]]

- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]