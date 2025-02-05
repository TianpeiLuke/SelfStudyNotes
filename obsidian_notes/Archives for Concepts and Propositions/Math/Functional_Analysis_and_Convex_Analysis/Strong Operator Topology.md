---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - strong_operator_topology
topics:
  - functional_analysis
  - topology
name: Strong Operator Topology
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Strong Operator Topology


>[!important] Definition
>Let $X$ be vector space and $Y$ be a **topological vector space**. 
>
>The **strong operator topology** is the *weakest topology* on $\mathcal{L}(X, Y)$ such that *the evaluation functional* $\delta_{x}: \mathcal{L}(X, Y) \to Y$
>$$ 
> \begin{align*}
> \delta_x: T \mapsto Tx
> \end{align*}
>$$  
>are **continuous** for *all* $x \in X$. 

- [[Evaluation Functional]]
- [[Banach Space]]
- [[Weak Topology Generated by Functions]]
- [[Continuous Function]]


## Explanation

>[!important]
>The **strong operator topology** is generated by **sub-basis**
>$$
>\mathcal{S} := \left\{ \delta_{x}^{-1}(U): \;  \forall \, x\in X,\, \forall U \in \mathscr{T}_{Y}  \right\} 
>$$

- [[Weak Topology Generated by Functions]]
- [[Sub-Basis of Topology]]

>[!important]
>Strong operator topology just need the **codomain of operator** $Y$ to be **topological**. The **domain** $X$ **need not** to be *topological*.

- [[Topological Vector Space]]

>[!info]
>$\mathcal{L}(X,Y)$ is not necessarily a *metric space* under *strong operator topology*.

- [[Metric Space]]

>[!info]
>In general, both the **weak** and **strong operator topologies** on $\mathcal{L}(X, Y)$ will **not be first-countable**. 

- [[First Countablity]]


>[!important]
>Denote the convergence of $T_{n}$ to $T$ under *weak operator topology* as $$T_{n} \stackrel{s}{\to} T,$$ which is defined as **the pointwise convergence** of $T_{n}x$ to $Tx$ in $Y$
>$$
>T_{n}x \to Tx
>$$
>for every $x\in X$.
>
>If $Y$ is normed space, it is the **uniform convergence** in $Y^{*}$
>$$
>\begin{align*}
>\lVert T_{n}x - Tx \rVert_{Y} = \sup_{\lVert f \rVert_{Y^{*}} \le 1 }\lvert f(T_{n}x) - f(Tx) \rvert \to 0  
>\end{align*}
>$$

- [[Pointwise Convergence]]
- [[Topology of Pointwise Convergence]]

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

>[!important] 
> Consider the **multiplication map** $\mathcal{L}(X, Y) \times \mathcal{L}(Y, Z) \rightarrow \mathcal{L}(X, Z)$
> $$
> \begin{align*}
> (A, B) \mapsto BA
> \end{align*}
>$$ 
>
>- Under **uniform operator topology**,  the map is **jointly continuous**.
>- Under **strong operator topology**, the map is **separately continuous** *but* **not** *jointly continuous* if $X$, $Y$, and $Z$ are *infinite-dimensional*.





-----------
##  Recommended Notes and References


- [[Banach Space]]
- [[Space of Bounded Linear Operators]]
- [[Uniform Operator Topology]]
- [[Weak Operator Topology]]

- [[Topological Vector Space]]
- [[Vector Space over a Field]]

- [[Functional Analysis by Reed]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]