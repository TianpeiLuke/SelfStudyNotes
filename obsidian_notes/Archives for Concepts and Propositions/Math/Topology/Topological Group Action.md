---
tags:
  - concept
  - math/topology
  - math/algebra
  - math/algebraic_topology
keywords:
  - topological_group_action
topics:
  - topology
  - algebra
  - algebraic_topology
name: Topological Group Action
date of note: 2024-05-17
---

## Concept Definition

^7bb29e

>[!important]
>**Name**: Topological Group Action

>[!important] Definition
>An **action** of a **topological group** $G$ **on** a *topological space* $X$ is a **continuous map** $\phi: G \times X \rightarrow X$ and define $$g(x):= \phi(g, x),$$
>  such that for
> $$
> \begin{align*}
> (g_1 \cdot g_2)(x)  &= g_1(g_2(x)), && \quad \forall g_1, g_2 \in G, x\in X\\
> 1_{G}(x) &= \text{Id}_{X}(x) = x, &&\quad \forall x\in X
> \end{align*} 
>$$ 
> where $1_{G}$ is the unit element of group $G$. 
> 
> Together with the **group action**, $X$ is called a **$G$-space**.

^097003


- [[Topological Group]]
- [[Topology of Set]]
- [[Group Action]]



>[!important]
>The map $$x \mapsto g(x)$$ is a **continuous map** on $X$ for each $g\in G$. 
>
>This map has **inverse map** $$x \mapsto g^{-1}(x)$$ which is **continuous** as well. 
>
>Thus the map $x \mapsto g(x)$ is a **homemorphism**.

- [[Homeomorphism]]

## Explanation


## Example


>[!example]
>A **global flow on $M$** (also called a **one-parameter group action**) is defined as a *continuous left $\mathbb{R}$-action* on $M$; 
>
>That is, a *continuous map* $$\theta: \mathbb{R} \times M \rightarrow M$$ satisfying the following *properties* for all $s, t \in \mathbb{R}$ and $p \in M$:
>$$
> \begin{align}
> &\theta(t, \theta(s, p)) = \theta(t+s, p)\\ \\
> &\theta(0, p) = p 
> \end{align}
>$$ 
>
>
>- For each $p \in M$, define a curve $$\theta^{(p)}: \mathbb{R} \rightarrow M$$ by
>$$ 
> \begin{align*}
> \theta^{(p)}(t) &= \theta(t, p).
> \end{align*}
>$$  
>The image of this curve is **the orbit** of $p$ **under the group action**.

- [[Global Flow on Smooth Manifold]]
- [[Orbit under Topological Group Actions]]





-----------
##  Recommended Notes and References

- [[Orbit under Topological Group Actions]]

- [[Group Action]]
- [[Topology of Set]]
- [[Topology Book by Munkres]]