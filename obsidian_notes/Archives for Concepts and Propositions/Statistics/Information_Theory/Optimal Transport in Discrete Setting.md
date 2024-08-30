---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - optimization/theory
  - math/optimal_transport
keywords:
  - optimal_transport_linear_program
topics:
  - information_theory
  - information_geometry
  - optimization
  - optimal_transport
name: Optimal Transport
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Optimal Transport as Linear Programming via Kantorovich relaxation 

![[Optimal Assignment Problem and Monge Problem#^6219c2]]

>[!important] Optimal Transport (Discrete) 
>Suppose 
>- There are $n$ piles of mass $\boldsymbol{a}=[a_1, \ldots, a_n]$ at *one location* $\boldsymbol{X} = [\boldsymbol{x}_1, \ldots, \boldsymbol{x}_{n}]$  and $m$ piles $\boldsymbol{b}=[b_1, \ldots, b_m]$ *at another location*  $\boldsymbol{Y} = [\boldsymbol{y}_1, \ldots, \boldsymbol{y}_{m}]$.
>
>- The **cost** of moving object from position $\boldsymbol{x}_{i}$ to position $\boldsymbol{y}_{j}$ is defined as $$c(\boldsymbol{x}_{i}, \boldsymbol{y}_{j}) \ge 0.$$ 
>   Let $\boldsymbol{C} = [C_{i,j}]_{n, m}$ be a **cost matrix.**  
>
>The **optimal transport** under *Kantorovich relaxation* is defined as finding an **optimal coupling** 
>$$
>\boldsymbol{P} := [P_{i,j}] \in \mathbb{R}_{+}^{n \times m}
>$$
>that **minimizes the overall cost** of moving $n$ piles of mass $\boldsymbol{a}$ from positions $\boldsymbol{X}$ to $m$ piles of mass  $\boldsymbol{b}$ at position $\boldsymbol{Y}.$ The total cost is computed as 
>$$
>\sum_{i,j}C_{i,j} P_{i,j}.
>$$

- [[Optimal Assignment Problem and Monge Problem]]
- [[Algorithms to Live By Chapter 08 Relaxation]]

>[!info]
>$\boldsymbol{P}$ is called a **probabilistic transport**. Here the coupling matrix $\boldsymbol{P}$  describes *the amount of mass* flowing from bin $i$ toward bin $j$, or from the mass found at $\boldsymbol{x}_i$ toward $\boldsymbol{y}_j$ in the formalism of discrete measures.

>[!important] Optimal Transport (Linear Programming) 
>The above formulation is defined as a **linear programming** problem:
>$$
>\begin{align*}
>\min_{P_{i,j} \in \mathbb{R}_{+}^{n \times m}} & \sum_{i,j}C_{i,j} P_{i,j} \\
\text{s.t. }&  \sum_{j=1}^{m}P_{i,j} = a_{i}, \quad 1 \le i \le n \\
&\sum_{i=1}^n P_{i,j}  = b_{j}, \quad 1 \le j \le m   \\
&P_{i,j} \ge 0 \nonumber
\end{align*}
>$$
>or, in matrix form
>$$
>\begin{align*}
>\min_{\boldsymbol{P} \in \mathbb{R}_{+}^{n \times m}} & \left\langle \boldsymbol{P} \,,\, \boldsymbol{C}    \right\rangle := \sum_{i,j}C_{i,j} P_{i,j} \\
\text{s.t. }&  \boldsymbol{P}\mathbf{1}_{m} = \mathbf{a} \\
&\boldsymbol{P}^T\mathbf{1}_{n}  = \boldsymbol{b}   \\
&P_{i,j} \ge 0 \nonumber
\end{align*}
>$$

- [[Linear Optimization Problem]]
- [[Theory and Algorithms for Linear Optimization]]

>[!info]
>The two sets of equality constraints corresponds to **the conservation of total mass** at both locations. 
>
>That is, it requires that 
>- the total mass **moving out** at one point $x_{i}$ ($a_i$) is equal to the total mass allocated to positions $\boldsymbol{Y}$
>- the total mass **moving in** at one point $y_{j}$ ($b_{j}$) is equal to the total mass allocated from positions $\boldsymbol{X}$
>

## Explanation


>[!info] Setting
>Consider the space of probability simplex $\Delta_{n}:= \{p_1, \ldots, p_n: \sum_{i=1}^{n}p_i = 1, \;\; p_i \ge 0\}$. We can define a *discrete measure* (i.e. distribution of discrete random variables)
>$$
> \begin{align*}
> \alpha &:= \sum_{i=1}^{n}a_i \delta_{\boldsymbol{x}_{i}}
> \end{align*}
>$$  
>where $\delta_{\boldsymbol{x}_{i}}$ is the *point mass (Dirac funcation)* at $\boldsymbol{x}_i$ and $\boldsymbol{a} \in \Delta_{n}$. The discrete measure $\alpha$ can be used to describe the distribution of the mass in one location. 







-----------
##  Recommended Notes and References

- [[Optimal Assignment Problem and Monge Problem]]
- [[Optimal Transport in Space of Measures]]

- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Computational Optimal Transport by Peyre]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 307