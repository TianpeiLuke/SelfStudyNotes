---
tags:
  - concept
  - optimization/theory
  - math/convex_analysis
keywords:
  - theorem_alternatives
topics:
  - optimization
  - convex_analysis
name: Theorems of Alternatives
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Theorems of Alternatives

>[!important] Theorem
>Let $C$ be a *convex* set, and let $f_{1} \,{,}\ldots{,}\, f_{m}$ be proper *convex functions* such that **$\text{dom}(f_{i}) \supset \text{relint}(C).$**
>
>Then **one and only one** of the following **alternatives** holds
>- There *exists* some $x \in C$, such that 
>  $$
>  f_{i}(x) < 0, \quad i=1 \,{,}\ldots{,}\,m
> $$
>- There exists **non-negative** real numbers $\lambda_{1} \,{,}\ldots{,}\, \lambda_{m}$, **not all zero**, such that 
>  $$
>  \sum_{i=1}^m \lambda_{i} f_{i}(x) \ge 0, \quad \forall x\in C.
> $$

- [[Relative Interior of Convex Set]]
- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]
- [[Separation Theorem]]
- [[Convex Function]]
- [[Convex Set]]
- [[Lagrange Dual Problem]]

>[!info]
>The condition that $\text{dom}(f_{i}) \supset \text{relint}(C)$ is **necessary**.


>[!important] Theorem (with affine constraints)
>Let $C$ be a *convex* set, and let $f_{1} \,{,}\ldots{,}\, f_{k}$ be proper *convex functions* such that $\text{dom}(f_{i}) \supset \text{relative-int}(C).$ Let $f_{k+1} \,{,}\ldots{,}\, f_{m}$ be *affine functions* such that 
>$$
>f_{j}(x) \leq 0, \quad  j= (k+1) \,{,}\ldots{,}\,m.
>$$
>has **at least one solution** $x\in  \text{relative-int}(C).$
>
>Then **one and only one** of the following **alternatives** holds
>- There *exists* some $x \in C$, such that 
>  $$
> \begin{align*}
> f_{i}(x) < 0, &\quad i=1 \,{,}\ldots{,}\,k \\
> f_{j}(x) \leq 0, &\quad i=(k+1) \,{,}\ldots{,}\,m
\end{align*}
> $$
>- There exists **non-negative** real numbers $\lambda_{1} \,{,}\ldots{,}\, \lambda_{m}$ such that **at least one of the numbers $\left\{ \lambda_{i}: 1 \leq i \leq k \right\}$ is non-zero**, and
>  $$
>  \sum_{i=1}^m \lambda_{i} f_{i}(x) \ge 0, \quad \forall x\in C.
> $$


>[!important] Theorem (Possible infinite number of weak constraints)
>Let $C$ be a non-empty, **closed** *convex* set in $\mathbb{R}^n$, and let $\left\{  f_{i}, i\in I\right\}$ be a collection of *proper*, **closed**, *convex functions*. 
>
>Assume that $f_{i}$ have *no common* **direction of recessions** which is also a *direction of recession* of $C.$
>
>Then **one and only one** of the following **alternatives** holds
>- There *exists* some $x \in C$, such that 
>  $$
>  f_{i}(x) < 0, \quad \forall i \in I
> $$
>- There exists **non-negative** real numbers $\lambda_{i}$, **only finitely many non-zero**, such that, for some $\epsilon >0$, one has
>  $$
>  \sum_{i=1}^m \lambda_{i} f_{i}(x) \ge \epsilon, \quad \forall x\in C.
> $$
> 
>If the second alternative holds, then the multipliers $\lambda_{i}$, can actually be chosen so that **at most $n+1$ of them are non-zero**. 

- [[Carathéodory Theorem for Convex Hull]]

>[!info]
>The above theorem applies both to **infinite systems** and *finite systems*. 
>
>One of its main consequences, as far as infinite systems are concerned, is that **existence** questions for *such systems* can be **reduced** in the following sense to **existence questions for finite systems.**

>[!important] Corollary (Existence of Feasible Solution in System of Infinite Inequalities)
>Let $C$ be a non-empty, **closed** *convex* set in $\mathbb{R}^n$, and let $\left\{  f_{i}, i\in I\right\}$ be a collection of *proper*, **closed**, *convex functions*. 
>
>Assume that $f_{i}$ have *no common* **direction of recessions** which is also a *direction of recession* of $C.$
>
>Assume also that for every $\epsilon >0$, and **every finite subset** $\{i_{1} \,{,}\ldots{,}\, i_{m}\}$ in $I$, with $m \leq n+1$, the **system**
>$$
>  f_{j}(x) < \epsilon, \quad j \in \{i_{1} \,{,}\ldots{,}\, i_{m}\},
> $$
>is satisfied by **at least one $x\in C$**.
> 
>Then there *exists* some $x \in C$, such that 
>  $$
>  f_{i}(x) < 0, \quad \forall i \in I.
> $$


>[!important] Helly's Theorem
>Let $\mathscr{C}:= \{C_{i}, i\in I\}$ be a collection of non-empty, **closed** *convex* sets in $\mathbb{R}^n$.
>
>Assume that the sets $C_{i}$ have *no common direction of recession*. 
>
>If **every subcollection** consists of $n+1$ or *fewer* sets has a **non-empty intersection**, then the entire collection has a **non-empty intersection**.
>
> $$
> \begin{align*}
> \bigcap_{i \in \{i_{1} \,{,}\ldots{,}\, i_{m}\}}C_{i} \neq \emptyset, \quad \forall\, m \leq n+1 \implies \bigcap_{i\in I}C_{i} \neq \emptyset
> \end{align*}
> $$

>[!info]
>Let $f_{i}:= \mathbb{1}\left\{ x\in  C_{i} \right\}$ and apply the Corollary above.


>[!info]
>The statement of Helly's Theorem is close to the criterion of **compactness** via the *finite-intersection property*.
> $$
> \begin{align*}
> \bigcap_{\{i = 1 \,{,}\ldots{,}\,n, C_i \in \mathscr{C}\}}C_{i} \neq \emptyset, \quad \forall\, n\text{ is finite} \implies \bigcap_{C \in \mathscr{C}}C \neq \emptyset
> \end{align*}
> $$
>- See [[Compactness]] and [[Finite Intersection Property]]
>  
>Note that this theorem works in finite dimensional space.  


## Explanation










-----------
##  Recommended Notes and References

- [[Lagrangian Function]]
- [[Lagrange Dual Problem]]

- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]
