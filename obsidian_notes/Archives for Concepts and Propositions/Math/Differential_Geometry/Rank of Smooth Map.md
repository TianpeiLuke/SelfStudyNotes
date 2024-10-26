---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords:
  - rank_smooth_map
topics:
  - differential_geometry
  - linear_algebra
name: Rank of Smooth Map
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Rank of Smooth Map

>[!important] Definition
>Suppose $M$ and $N$ are smooth manifolds with or without boundary. 
>
>Given a *smooth map* $F: M \rightarrow N$ and a point $p \in M$, we define the **rank of $F$ at $p$** to be *the rank of the linear map* $$dF_p: T_{p}M \rightarrow T_{F(p)}N;$$

- [[Rank and Nullity of Linear Map]]

>[!info]
>it is **the rank of the Jacobian matrix** of $F$ in any smooth chart, or the **dimension** of $$\text{Im }dF_p \subseteq T_{F(p)}N.$$ 


>[!important] Definition
>If $F$ has the **same rank** $r$ **at every point**, we say that it has **constant rank**, and write $$\text{rank}\,F = r.$$

>[!info]
>Note that $\text{rank }dF_{p} \le \min\set{\text{dim }M, \; \text{dim }N}$. 

- [[Rank and Nullity of Linear Map]]
- [[Rank–Nullity Theorem]]

>[!important] Definition
>- If the rank of $dF_p$ is equal to this *upper bound*, we say that **$F$ has full rank at $p$**, and 
>- if $F$ has *full rank everywhere*, we say **$F$ has full rank**.

>[!info]
>A smooth map with full rank may *not be of constant rank.*

## Explanation

>[!important]
>The rank of a smooth map is a **local property**. It is evaluated at each neighborhood of a point. 



## Submersion, Immersion and Embedding

>[!important] 
>The most important *constant-rank maps* are those of **full rank**. 

- [[Smooth Submersion]]
- [[Smooth Immersion]]
	- [[Smooth Embedding]]

>[!important] 
>The concept
>- **submersion/immersion**: about the **local differential property** of $F$ 
>- **surjective/injective**:  about the **global property** of $F$.  
>  
>Local property can *be determined by* the global property but not vice versa. 
>
>Thus a map 
>- can be **submersion** but *may not be surjective*.  
>- can be **immerison** but may *not be injective*. 

## Rank Theorem

- [[Rank Theorem]]





-----------
##  Recommended Notes and References


- [[Smooth Map between Euclidean Spaces]]

- [[Rank and Nullity of Linear Map]]

- [[Introduction to Smooth Manifolds by Lee]]