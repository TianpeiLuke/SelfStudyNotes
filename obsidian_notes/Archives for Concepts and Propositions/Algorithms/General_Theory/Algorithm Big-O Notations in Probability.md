---
tags:
  - concept
  - algorithm/analysis
keywords:
  - big_o_notation_algorithm
  - big_gamma_notation_algorithm
  - big_theta_notation_algorithm
topics:
  - algorithm/analysis
name: Algorithm Big-O Notations in Probability
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Algorithm Big-O Notations in Probability

>[!important] Definition
>The **Big-Oh notation** is a member of a family of notations, collectively called the **Bachmann–Landau notation** or **Landau notation** or **asymptotic notation**.

### $O$-Notation

![[Algorithm Big-O Notations and Dominance Relation#^ebad98]]

- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Upper Bound and Supremum of Set]]
- [[Algorithm Worst-Case Running Time Analysis]]

### $o$-Notation

![[Algorithm Big-O Notations and Dominance Relation#^cf55fa]]

- [[Algorithm Big-O Notations and Dominance Relation]]


###  $O$-Notation in Probability

>[!important] Definition
>We can define **Big-Oh probability notation** as $$X_{n} = O_{p}(g_{n}) \iff \forall \delta >0, \; \exists \epsilon,\,n_{0}, \; \forall n\ge n_{0},\;\; \mathcal{P}\left\{ \left\lvert  \frac{X_{n}}{g_{n}}  \right\rvert > \epsilon \right\} < \delta $$
>- This means that $X_{n}/g(n)$ is **asymptotically bounded**.
>- Or, *with probability* $1- \delta$, $$\left\lvert  \frac{X_{n}}{g_{n}}  \right\rvert \le \epsilon$$

^0b1f8e

- Wikipedia [Big_O_in_probability_notation](https://en.wikipedia.org/wiki/Big_O_in_probability_notation)

###  $o$-Notation in Probability

>[!important] Definition
>We can define **Little-Oh probability notation** as $$X_{n} = o_{p}(g_{n}) \iff \forall \delta >0, \forall \epsilon >0, \; \exists n_{0}, \; \forall n\ge n_{0},\;\; \mathcal{P}\left\{ \left\lvert  \frac{X_{n}}{g_{n}}  \right\rvert \ge \epsilon \right\} < \delta $$
>- This means that $X_{n}/g(n)$ is **converge** to zero **in probability**. $$\lim_{ n \to \infty } \mathcal{P}\left\{ \left\lvert  \frac{X_{n}}{g_{n}}  \right\rvert \ge \epsilon \right\} = 0,\; \forall \epsilon >0$$

- [[Convergence in Measure]]



## Explanation



## Examples of Complexity 







-----------
##  Recommended Notes and References

- [[Loop Invariant Format]]
- [[Algorithm General Definition]]

- [[Introduction to Algorithms by Cormen]] pp  25 - 31, 49 - 76
- [[Algorithm Design Manual by Skiena]] pp 34 - 41
- [[Numerical Linear Algebra by Trefethen]] pp 103-106
- [[Matrix Computations by Golub]] pp 12
- [[Numerical Optimization by Nocedal]] pp 631 - 633
- 


- Wikipedia [Big_O_notation](https://en.wikipedia.org/wiki/Big_O_notation)
- Blog 
	- [Big-O, Little-O, Theta, Omega](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/analysis/notations.html)
