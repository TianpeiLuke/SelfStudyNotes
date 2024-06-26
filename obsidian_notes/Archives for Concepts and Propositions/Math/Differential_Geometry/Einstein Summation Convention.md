---
tags:
  - concept
  - math/differential_geometry
keywords:
  - Einstein_summation_convention
topics:
  - differential_geometry
name: The Einstein Summation Convention
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: The Einstein Summation Convention

>[!info]
>Because of the proliferation of summations such as $$\sum_{i=1}^{n}x^{i}\,E_{i}$$ in this subject, we often **abbreviate** such a sum by **omitting the summation sign**, as in
>$$
> \begin{align*}
> E(x) = \sum_{i=1}^{n}x^{i}\,E_{i}\;\; \Rightarrow \;\; E(x) = x^{i}\,E_{i}.
> \end{align*}
>$$ 

>[!important] Definition
>We interpret any such expression according to the **following rule**, called the **Einstein summation convention**:
>
>- if the **same index name** (such as $i$ in the expression above) appears **exactly twice** in any **monomial term**, 
>	- once as **an upper index** and 
>	- once as **a lower index**, 
>	- that term is understood to *be summed over* **all possible values of that index**, generally from $1$ to the dimension of the space in question. 
>
>
>- Another important aspect of the summation convention is the **positions** of *the indices* 
>	- We always write **basis vectors** (such as $E_i$) with **lower indices**, and
>	- **components** of a vector *with respect to a basis* (such as $x^i$) with **upper indices.** 
>	- These index conventions help to ensure that, in summations that make mathematical sense, *each index to be summed over typically appears twice* in any given term, once as a lower index and once as an upper index. 
>	- Any index that is **implicitly summed** over is a "*dummy index,"* meaning that the *value* of such an expression is **unchanged** if *a different name* is **substituted** for each dummy index. For example, $x^i E_i$ and $x^j E_j$ mean exactly the same thing. 
>
>
>- Since the coordinates of a point $(x^1,\ldots, x^n)$ are also its *component* with respect to the standard basis, in order to be consistent with our convention of writing *components* of vectors *with upper indices*, we need to use upper indices for these coordinates.





## Explanation





-----------
##  Recommended Notes and References

