---
tags:
  - entry_point
  - concept
  - math/measure_theory
  - math/topology
keywords:
  - sigma_field
  - topology
  - continuous_function
  - borel_sigma_field
  - measurable
  - measurable_function
  - Lebesgue_measurable_function
topics:
  - measure_theory
  - topology
name: comparison_sigma_field_topology
date of note: 2024-04-18
---

## Comparison between $\sigma$-algebra and topology

|                             | ***Boolean Algebra***                                                                                                                      | ***$\sigma$-Algebra***                                                                                                                  | ***Borel $\sigma$-Algebra***                                                                                                            | ***Topology***                                                 |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **compatibility**           |                                                                                                                                            | $\Leftarrow \checkmark \Rightarrow$                                                                                                     | $\sigma$-algebra *generated open subsets*                                                                                               | **no relation**                                                |
| **collection of subsets**   | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| include emptyset            | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| include fullset             | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| finite union                | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| **countable union**         |                                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| **arbitrary union**         |                                                                                                                                            |                                                                                                                                         |                                                                                                                                         | $\checkmark$                                                   |
| finite intersection         | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                   |
| **countable intersection**  |                                                                                                                                            | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            |                                                                |
| **complements**             | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            |                                                                |
| structure                   | *analytical*                                                                                                                               | *analytical*                                                                                                                            | *analytical*                                                                                                                            | **topological**                                                |
| related **measure**         | $\checkmark$                                                                                                                               | $\checkmark$                                                                                                                            | $\checkmark$                                                                                                                            |                                                                |
| *set* **in** collection     | - elementary sets; <br>- Jordan measurable sets; <br>- atomic algebra;<br>- dyadic algebra;<br>- **finite union** of measurable sets; etc. | - Boolean measurable set;  <br>- Lebesgue measurable sets,<br>- Lebesgue null sets; <br>- the **countable union and complements**  etc. | - *open sets*,<br>- **closed sets**,<br>- **compact sets**,<br>- **elementary sets**,<br>- **$G_{\delta}$ and $F_{\sigma}$ sets**  etc. | - **open sets**                                                |
| *set* **not in** collection | *some* Lebesgue measurable sets                                                                                                            | some **non-measurable** sets                                                                                                            | some Jordan measurable set but *not Borel measurable*                                                                                   | - **closed set**, <br>- **$G_{\delta}$ and $F_{\sigma}$ sets** |
| related **function**        | - Boolean measurable function; <br>- *Rieman integrable* function,                                                                         | - **Lebesgue measurable function**, <br>- **$\sigma$-finite function**, <br>- **continuous function**                                   | - **Borel measurable** function,<br>- **continuous function**                                                                           | - **Continuous function**                                      |


- Topology concerns the structure that defines "*open set*"
- $\sigma$-Algebra concerns the algebraic structure associated with set operations such as *complements* and *countable union*
- A set with $\sigma$-Algebra do not need to have a topology.
- A set with Borel $\sigma$-Algebra have both a topology and a $\sigma$-Algebra equipped. Thus it is the more restricted concept of the above. But it is usually sufficient for discussion.




-----------
##  Recommended Notes and References

- [[sigma Algebra]]
- [[Borel sigma Field]]
- [[Boolean Algebra]]
- [[Topology of Set]]
- [[Gdelta set and Fsigma set]]



- [Latex to Markdown](https://tableconvert.com/latex-to-markdown)