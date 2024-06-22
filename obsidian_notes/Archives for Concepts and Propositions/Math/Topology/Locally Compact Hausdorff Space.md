---
tags:
  - concept
  - math/topology
keywords:
  - locally_compact_Hausdorff_space
topics:
  - topology
name: locally compact Hausdorff Space
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Locally Compact Hausdorff (**LCH**) Space


>[!important] Definition
>A *topological space* $X$ is called **locally compact Hausdorff**:
>1. $X$ is *Hausdorff*, i.e. for any distinct  $x, y\in X$,  there exists two disjoint open subsets $U, V$ such that $U\cap V = \emptyset$ and $x \in U$ and $y \in V$
>2. $X$ is *locally compact*, i.e. for any $x \in X$, for any neighborhood $U$ of $x$, there exists some *compact* subset $C$ such that $U \subset C$.


## Example

>[!example] Real Line
>The **real line** $\mathbb{R}$ is *locally compact Hausdorff*. 
>
>$\mathbb{R}$ is Hausdorff. And every point $x \in \mathbb{R}$ lies in some interval $(a, b)$, which in turn is *contained* in *the compact subspace* $[a, b]$. 


>[!example] Finite Dimensional Euclidean Space
>The **n-dimensional Euclidean space** $\mathbb{R}^n$ is *locally compact Hausdorff*. 
>
>Each point $\mathbf{x}$ lies in some basis element
$(a_1, b_1) \times \ldots \times (a_n, b_n)$, which in turn lies in *the compact subspace* $[a_1, b_1] \times \ldots \times [a_n, b_n]$.


>[!example] Topological Manifold
>Every **topological manifold** is *locally compact Hausdorff*.




## Basic Properties

>[!important] Proposition
>Let $X$ be a *Hausdorff* space. Then $X$ is **locally compact** *if and only if* given $x$ in $X$, and given a neighborhood $U$ of $x$, there is a neighborhood $V$ of $x$ such that $\bar{V}$ is **compact** and $\bar{V} \subseteq U$.

- This proposition shows that every *locally compact Hausdorff space* has **pre-compact basis**
- [[Pre-Compactness]]


>[!important] Corollary
>Let $X$ be *locally compact Hausdorff*; let $A$ be a subspace of $X$. If $A$ is **closed** in $X$ or **open** in $X$, then $A$ is **locally compact.**

- The *open or closed subspace* of locally compact Hausdorff is also locally compact Hausdorff.
- That is, locally compact Hausdorff property is *closed* under *open/closed subspace operation.*

- [[Subspace Topology]]


>[!important] Corollary
>A space $X$ is **homeomorphic** to an *open subspace* of a **compact Hausdorff space** *if and only if* $X$ is **locally compact Hausdorff.**

- [[Homeomorphism]]
- The *locally compact Hausdorff* space is *topologically equivalent* to an **open subspace** of **compact Hausdorff space.**

## Equivalent Definitions

>[!important] Definition
For a *Hausdorff space* $X$,  the following are **equivalent**:
> 
> 1. $X$ is **locally compact.**
> 2. Each point of $X$ has a **precompact neighborhood.** 
> 3. $X$ has a **basis** of **precompact open** subsets.

- [[Locally Compactness]]
- [[Pre-Compactness]]

## Important Properties

>[!important]
>Useful facts for (locally) compact Hausdorff space: 
> - **subspace** of compact Hausdorff space is *compact Hausdorff* if and only if it is *closed*. 
> - **closed subspace** of **compact** space is *compact*; 
> - **compact subspace** of *Hausdorff* space is *closed*;
> - *compact Hausdorff space* $X$ is **normal** ($T_4$), thus it is *completely regular*;
> - **arbitrary product** of *compact (Hausdorff)*  space is *compact (Hausdorff)*;
> - *compactness* $\Rightarrow$ *sequential compactness*;
> - *compactness* $=$ *net compactness*, i.e. every \emph{net} has a *convergence* subnet;
> - **image** of *compact* space under **continuous map** $f$ is *compact*;
> - **continuous bijection** between two *compact Hausdorff* spaces is a **homemorphism** (and is a **closed map**);
> - **closed graph theorem**: $f$ is *continuous* if and only if its *graph* is *closed*;
> - **uncountability**: for *compact Hausdorff space*, if the space has **no isolated points**, then it is *uncountable*;
> - **metrization**: if compact Hausdorff space is **second-countable**, then it is **metrizable**.

>[!info]
>*Locally compact Hausdorff space* is the second most used topological space, (the first is the metric space). 

>[!info]
>*Locally compact Hausdorff space* is similar to a metric space in many senses. Its property is *very close to a metric space*. 
>
>For instance, both LCH and metric space are **completely regular space**.


>[!info]
>**Compact Hausdorff space** is almost a metric space in many senses. 
>- A compact Hausdorff space will become a metric space as long as it is *second-countable*. 
>- The CH property is **invariant** to *closed subspace* operation, *arbitrary product*, *function image operation*. 
>- both compact Hausdorff space and metric space are **normal space**.



-----------
##  Recommended Notes and References


- [[Hausdorff Space]]
- [[Locally Compactness]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)

- [[Topology Book by Munkres]]
- [[Real Analysis by Royden]]