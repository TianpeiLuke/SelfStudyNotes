---
tags:
  - concept
  - math/graph_theory
keywords:
  - separation_of_graph
topics:
  - math/graph_theory
name: Separation of Graph
date of note: 2024-07-15
---

## Concept Definition

>[!important]
>**Name**: Separation of Graph

>[!important] Definition
>Let $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ be a graph.
>
>If 
>- $A, B \subseteq \mathcal{V}$, and
>- $X  \subseteq \mathcal{V} \cup \mathcal{E}$ are such that 
>	- *every $A$-$B$ path* in $\mathcal{G}$ contains a *vertex* or an *edge* from $X$, 
>  
>we say that $X$ **separates** $A$ and $B$ in $\mathcal{G}$.

- [[Paths in Graph and Length of Path]]

>[!info]
>This implies that $$A \cap B \subseteq X.$$

>[!important] Definition
>We say that $X$ **separates** *two vertices* $a$ and $b$ if it separates $\{ a \}$ and $\{ b \}$, but $a, b\not\in X.$
>
>We say that $X$ **separates** $\mathcal{G}$ if $X$ separates *some two vertices* in $\mathcal{G}$.
>
>A *separating* set of *vertices* is called a **separator**.

>[!important] Definition
>The unordered pair $\{ A, B \}$ is a **separation** of $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ if $A \cup B = \mathcal{V}$ and $\mathcal{G}$ has *no edge between* $A \setminus B$ and $B \setminus A$. 
>
>The latter is equivalent to say that *$A \cap B$ separates $A$ from $B$*.
>
>If both $A \setminus B$ and $B \setminus A$ are *non-empty*, the *separation* is **proper**.


>[!important] Definition
>Let  $\{ A, B \}$  be  a *separation* of $\mathcal{G}$. 
>
>- The number $|A \cap B|$ is called the **order of separation**.
>- The sets $A$ and $B$ are its **sides**.




## Explanation





-----------
##  Recommended Notes and References


- [[Connectivity of Graph]]
- [[D-Separation in Bayesian Network]]
- [[Separation and Connectedness]]


- [[Connected Graph and Connected Component of Graph]]
- [[Graph]]
- [[Graph Theory by Diestel]] pp 11