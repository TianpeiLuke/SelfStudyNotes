---
tags:
  - concept
  - math/measure_theory
keywords:
  - positive_set
  - negative_set
  - null_set
topics:
  - measure_theory
name: positive set; negative set; null set
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: $\nu$-Positive Set, $\nu$-Negative Set and $\nu$-Null Set


>[!important] Defintion
>If $\nu$ is a *signed measure* on $(X,\mathscr{B})$,  a *set* $E\in \mathscr{B}$ is called 
>- **positive**,  if $\nu(F)\ge 0$;
>- **negative**, if $\nu(F)\le 0$;
>- **null**, if $\nu(F)= 0$, 
>
>respectively, for *all $\mathscr{B}$-measurable subsets* of $E$ (i.e. $F\in \mathscr{B}$ and $F\subseteq E$).  

- [[Signed Measure]]

>[!important]
>$E$ is **$\nu$-positive**, **$\nu$-negative**, **$\nu$-null**  if and only if $\nu(E\cap M)>0$, $\nu(E\cap M)<0$, $\nu(E\cap M)=0$ *for any $M$.* 



>[!important]
>Note that $$\nu(E) = \int_{X}\mathbb{1}(E)\,f\, d\mu,$$ then $E$ being **$\nu$-positive**, **$\nu$-negative**, **$\nu$-null**  corresponds to $f\ge 0$, $f\le 0$ and $f=0$ for *$\mu$-almost everywhere* $x\in E$.



## Explanation






-----------
##  Recommended Notes and References


- [[Real Analysis Modern Techniques and Their Applications by Folland]]