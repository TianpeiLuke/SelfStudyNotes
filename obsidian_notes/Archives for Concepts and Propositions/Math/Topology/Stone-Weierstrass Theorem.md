---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - stone_weierstrass_theorem
topics:
  - functional_analysis
  - topology
name: Stone-Weierstrass Theorem
date of note: 2024-05-27
---

## Theorem

>[!important]
>**Name**: Stone-Weierstrass Theorem

>[!important] Thereom (Classical Weierstrass Theorem)
>The *polynomials* are **dense** in the $\mathcal{C}([a,b], \mathbb{R})$, the space of all *real-valued continuous functions* on **closed internal** $[a,b]$ for any finite number $a < b$.
>
>In other word, let  $f: [a, b] \to \mathbb{R}$ be a *continuous function*. For any $\epsilon >0$,  there exists a **polynomial** $P(x)$ such that  for any $x \in  [a, b]$, 
>$$
>\lvert f(x) - P(x) \rvert < \epsilon.
>$$ 

- [[Limit Point]]
- [[Uniform Convergence]]
- [[Space of all Continuous Functions]]
- [[Compactness]]

>[!info]
>Equivalently, for any $f\in \mathcal{C}([a,b], \mathbb{R})$, there exists polynomial $p$
>$$
>\lVert f - p \rVert_{\infty} < \epsilon 
>$$


>[!important] Thereom (Stone-Weierstrass Theorem)
>Let  $X$ be **compact Hausdorff** space and $B$ be a **sub-algebra** of $\mathcal{C}(X, \mathbb{R})$ which is closed under
>$$
>\lVert f \rVert_{\infty} := \sup_{x\in X}|f(x)|. 
>$$
>
>We say that $B$ **separate points** if, given any $x, y \in X$, we can find $f\in B$ such that 
>$$
>f(x) \neq f(y).
>$$
>
>If $B$ *separate points*, then
>- either $$B = \mathcal{C}(X, \mathbb{R});$$
>- or there *exists some* $x_{0} \in X$, such that $$B = \{ f \in \mathcal{C}(X, \mathbb{R}): f(x_{0}) = 0 \}.$$ That is, $B$ is the set of *all continuous functions* whose **roots** contains $x_{0}$.
>
>Furthermore, if $1 \in B$, and $B$ separate points, then $B = \mathcal{C}(X, \mathbb{R}).$  
 
- [[Compact Hausdorff Space]]
- [[Uniform Topology on Metric Spaces]]
- [[Urysohn Lemma]]


>[!important] Alternative Theorem
>For compact Hausdorff space $X$, a **sub-algebra** $B$ of $\mathcal{C}(X, \mathbb{R})$ is **dense** in $\mathcal{C}(X, \mathbb{R})$ *if and only if* $B$ **separate points**. 


>[!important] Thereom (Stone-Weierstrass Theorem)
>Let  $X$ be **compact Hausdorff** space and $B$ be a **sub-algebra** of $\mathcal{C}(X, \mathbb{C})$ which is closed under
>$$
>\lVert f \rVert_{\infty} := \sup_{x\in X}|f(x)|. 
>$$
>and $$f \in B \implies  \bar{f} \in B. $$
>
>If $B$ is **closed** and **separate points**, then 
>- either $$B = \mathcal{C}(X, \mathbb{C})$$
>- or there exists some $x_{0}$ such that $$B = \{ f \in \mathcal{C}(X, \mathbb{C}): f(x_{0})  = 0\}$$


## Explanation





-----------
##  Recommended Notes and References


- [[Urysohn Lemma]]
- [[Tietze Extension Theorem]]
- [[Compact Hausdorff Space]]
- [[Uniform Topology on Metric Spaces]]
- [[Space of all Continuous Functions]]


- [[Limit Point]]
- [[Compactness]]



- [[Functional Analysis by Reed]]