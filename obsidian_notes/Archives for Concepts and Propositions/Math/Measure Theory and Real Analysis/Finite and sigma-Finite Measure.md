---
tags:
  - concept
  - math/measure_theory
keywords:
  - finite_measure
  - sigma_finite_measure
topics:
  - measure_theory
name: finite and sigma-finite measure
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Finite and $\sigma$-Finite Measure $\mu$


>[!important] Defintion
>Let $(X, \mathscr{B}, \mu)$ be a *measure space*. 
>
>If $$\mu(X)< \infty$$ (which implies that $\mu(E) < \infty$ for all $E \in \mathscr{B}$), then $\mu$ is called **finite**. 

- [[Finite Set and Cardinality]]

>[!important] Definition
> Let $(X, \mathscr{B}, \mu)$ be a *measure space*.  
> 
> If $$X = \bigcup_{j=1}^{\infty}E_j,\text{  where } E_j \in \mathscr{B}\text{ and } \mu(E_j) < \infty,$$then $\mu$ is called **$\sigma$-finite**.  
> 
> More generally, if $$E = \bigcup_{j=1}^{\infty}E_j$$ where $E_j \in \mathscr{B}$ and $\mu(E_j) < \infty$, then $E$ is said to be **$\sigma$-finite** *for* $\mu$.

- [[Countable Set and Uncountable Set]]
- [[Covering of Set and Open Covering of Topological Set]]


>[!important] Definition
>Let $(X, \mathscr{B}, \mu)$ be a *measure space*.  
>
>If for each $E \in \mathscr{B}$ with $$\mu(E) = \infty$$ there *exists* $F\in \mathscr{B}$ with $F \subseteq E$ and $$0 < \mu(F) < \infty,$$ then $\mu$ is called **semi-finite**.



## Explanation


## Examples

>[!example]
>Given measurable space $(\Omega, \mathscr{F})$,  a *probability measure* $\mathcal{P}$  is a **finite measure** since $$\mathcal{P}(\Omega) = 1.$$

- [[Probability Space]] 




-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Probability Space]]

- [[Countable Set and Uncountable Set]]
- [[Covering of Set and Open Covering of Topological Set]]