---
tags:
  - concept
  - math/topology
keywords:
  - path_connectedness
topics:
  - topology
name: path connectedness
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Path Connectedness


>[!important] Definition
>Given points $x$ and $y$ of the space $X$, a **path** in $X$ from $x$ to $y$ is a *continuous map* $f : [a, b] \rightarrow X$ of some *closed interval* in the real line into $X$, such that $f(a) = x$ and $f(b) = y$. 


>[!important] Definition
>A space $X$ is said to be **path connected** if *every pair* of points of $X$ can be *joined by a path* in $X$.




## Explanation

>[!info]
>Recall that a topological space $X$ is
> 
> - **connected** if there do not exist two *disjoint*, *nonempty*, *open* subsets of $X$ whose union is $X$;
> - **path-connected** if every pair of points in $X$ can be *joined by a path* in $X$, and
> - **locally (path-)connected** if $X$ has a *basis* of *(path-)connected* open subsets.
> 
> We have $$\text{\emph{\textbf{path-connected}}} \Rightarrow \text{\emph{\textbf{connected}}}$$ but $$\text{\emph{\textbf{connected}}} \not\Rightarrow \text{\emph{\textbf{locally-connected}}}.$$
> 

- [[Separation and Connectedness]]
- [[Locally Connected and Locally Path-Connected]]



-----------
##  Recommended Notes and References

- [[Separation and Connectedness]]
- [[Topology Book by Munkres]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)