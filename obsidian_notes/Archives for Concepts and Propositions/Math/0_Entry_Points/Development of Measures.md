---
tags:
  - entry_point
  - concept
  - math/measure_theory
keywords: 
topics:
  - measure_theory
name: 
date of note: 2024-05-07
---


## Development of Lebesgue Measure from Elementary Measures on $\mathbb{R}^n$

- [[Intuitive Axioms of Measures]]
- [[Elementary Measure]]
- [[Jordan Measure]]
- [[Lebesgue Outer Measure]]
- [[Lebesgue Measure]]
- [[Complete Measure Space]]


### Comparison and Development of Measures on Euclidean Space

|                             | **Elementary measure**                  | **Jordan measure**                                                                                                                                                                                    | **Lebesgue outer measure**                                                                                     | **Lebesgue measure**                                                                                                 |
| --------------------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **compatibility**           |                                         | $\Leftarrow \checkmark$                                                                                                                                                                               | $\Leftarrow \checkmark$                                                                                        | $\Leftarrow \checkmark$                                                                                              |
| **non-negative**            | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| $m(\emptyset) = 0$          | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| $m([0,1]^d) = 1$            | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **translation-invariant**   | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **finitely additive**       | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **monotonicity**            | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **finitely subadditive**    | $\checkmark$                            | $\checkmark$                                                                                                                                                                                          | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **outer regularity**        |                                         |                                                                                                                                                                                                       | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **inner regularity**        |                                         |                                                                                                                                                                                                       | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **countably subadditivity** |                                         |                                                                                                                                                                                                       | $\checkmark$                                                                                                   | $\checkmark$                                                                                                         |
| **countably additivity**    |                                         |                                                                                                                                                                                                       |                                                                                                                | $\checkmark$                                                                                                         |
| **measurable set**          | box $I_1 \,{\times}\ldots{\times}\,I_d$ | All *elementary sets*;<br><br>any *compact convex* polytope; <br><br>any *open sets* and *closed sets*;<br><br>*finite union* of measurable sets; <br><br>**graph/epigraph** of *continous function*; | All *Jordan measurable* sets; <br><br>*countable union* of measurable sets, e.g. $G_{\delta}$ and $F_{\sigma}$ | forms a $\sigma$-algebra that includes all *Borel sets*;<br><br>sets with *Lebesgue outer measure zero* (null sets). |
| **non-measurable set**      | any subsets *other than box*            | *countable union* of Jordan measurable sets;<br><br>*bullet-riddled square* and *sets of bullets*;<br><br>subsets with a lot of *"holes"* or *"fractal"*                                              | same as right                                                                                                  | $E = \mathbb{R}/\mathbb{Q} \cap [0,1]$                                                                               |
| **algebra**                 | *boolean algebra* $\mathscr{A}_0$       | *boolean algebra* $\mathscr{A}_1 \supsetneq \mathscr{A}_0$                                                                                                                                            |                                                                                                                | *$\sigma$-algebra* $\mathscr{A}_{2} \supsetneq \mathscr{A}_1$                                                        |
| **integration**             |                                         | **Riemann integration**                                                                                                                                                                               |                                                                                                                | **Lebesgue integration**                                                                                             |


## Development of Abstract Measure

### From Algebra to $\sigma$-Algebra

- [[Boolean Algebra]]
- [[Finite and sigma-Finite Measure]]
- [[sigma Algebra]]
- [[Borel sigma Field]]
- [[pi-system and lambda-system and Dynkin Theorem]]
- [[Compare Sigma Field with Topology]]

### Important Algebra

- [[Discrete Algebra]]
- [[Atomic Algebra]]
- [[Dyadic Algebra]]
- [[Lebesgue and Jordan and Null Algebra]]

### Algebra Operations

- [[Restriction of Algebra on Subset]]
- [[Recursive Description of Generated sigma Algebra]]
- [[sigma Algebra Generated by Sets]]
- [[sigma Algebra Generated by Measurable Functions]]

### Definition of Measure on Collection of Subsets

- [[Finitely Additive Measure]] on [[Boolean Algebra]]
- [[Measure Space and Countably Additive Measure]] on [[sigma Algebra]]
- [[Borel Measure]] on [[Borel sigma Field]]
- [[Criteria for Measurability]]
- [[Complete Measure Space]]
- [[Support of Measure]]
- [[Inner Regularity]]
- [[Outer Regularity]]
- [[Tightness of Measures]]


### Other Important Measures

- [[Dirac Measure]]
- [[Discrete Measure]]
- [[Counting Measure]]
- [[Restriction of Measure on Subset]]
- [[Radon Measure]]
- [[Haar Measure on Locally Compact Topological Group]]

### Construction of Abstract Measures

#### Path 1 via Carathéodory Measurability

- [[Outer Measure]]
- [[Carathéodory Measurability]]
- [[Carathéodory Extension Theorem]]

#### Path 2 via Hahn-Kolmogorov Extension

- [[Pre-Measure]]
- [[Hahn-Kolmogorov Extension of Pre-measure]]
- [[Hahn-Kolmogorov Theorem]]

- [[Monotone Class]]


## Development of Other Measures

### Lebesgue-Stieltjes Measure

- [[Lebesgue-Stieltjes Measure]]
- [[Lebesgue-Stieltjes Integration]]

### Product Measure

- [[sigma Algebra Generated by Sets]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]
- [[Product Measure]]
- [[Tensor Product]]

### Measure in Infinite Product Space

- [[Kolmogorov Extension Theorem in Infinite Product Space]]
- [[Product Measure on Infinite Product Space]]





-----------
##  Recommended Notes and References


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Principles of Mathematical Analysis by Rudin]] pp 321