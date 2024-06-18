---
tags:
  - concept
  - math/differential_geometry
  - math/topology
  - math/algebra
keywords:
  - global_flow_smooth_manifold
  - topological_group_action
topics:
  - differential_geometry
  - topology
  - algebra
name: Global Flow on Smooth Manifold
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Global Flow on Smooth Manifold

>[!important] Definition
>A **global flow on $M$** (also called a **one-parameter group action**) is defined as a *continuous left $\mathbb{R}$-action* on $M$; 
>
>That is, a *continuous map* $$\theta: \mathbb{R} \times M \rightarrow M$$ satisfying the following *properties* for all $s, t \in \mathbb{R}$ and $p \in M$:
>$$
> \begin{align}
> &\theta(t, \theta(s, p)) = \theta(t+s, p)\\ \\
> &\theta(0, p) = p 
> \end{align}
>$$ 

^532ef7

- [[Topological Group Action]]

>[!info]
>For a global flow $\theta$ on $M$, we define two collections of maps as follows:


>[!important] Definition
> For each $t\in \mathbb{R}$, define a **continuous map** $$\theta_t: M \rightarrow M$$ by
>$$  
> \begin{align*}
> \theta_t(p) &= \theta(t, p). 
> \end{align*}
>$$  
>
>The defining properties for global flow are equivalent to **the group laws**:
>$$
> \begin{align}
> &\theta_t \circ \theta_s = \theta_{t+s}, \\
> &\theta_0 = \text{Id}_{M} 
> \end{align}
>$$ 
>

- [[Topological Group Action]]
- [[Group]]


>[!important] Definition
> For each $p \in M$, define a curve $$\theta^{(p)}: \mathbb{R} \rightarrow M$$ by
>$$ 
> \begin{align*}
> \theta^{(p)}(t) &= \theta(t, p).
> \end{align*}
>$$  
>
>The image of this curve is **the orbit** of $p$ **under the group action**.

- [[Orbit under Topological Group Actions]]
- [[Orbit Space of Topological Group Action]]

## Explanation

>[!info]
>Note that this definition did not mention the vector fields. 
>
>A global flow is just a one-parameter group action on manifold. $\theta(t, p)$ **can be any vectors**, but necessarily attached to a vector field.
>
>On the other hand, for each global flow, it is always possible to identify a tangent vector field for that flow. 

- [[Vector Field as Infinitesimal Generator of Global Flow]]

>[!info]
>Let the orbit 
>$$
>\theta^{(p)}(\mathbb{R}):= \{ \theta^{(p)}(t): t\in \mathbb{R}  \}
>$$
>
>The orbit space of global flow is 
>$$
>M / \mathbb{R} := \{ \theta^{(p)}(\mathbb{R}) : p \in M \}
>$$ 

- [[Orbit Space of Topological Group Action]]



-----------
##  Recommended Notes and References

- [[Vector Field on Manifold]]
- [[Topological Group]]
- [[Topological Group Action]]