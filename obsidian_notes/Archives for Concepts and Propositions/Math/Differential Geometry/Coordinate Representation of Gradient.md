---
tags:
  - concept
  - math/differential_geometry
keywords:
  - gradient_smooth_map
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Gradient
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Gradient

>[!important]
>Let $(M, g)$ be an *oriented Riemannian $n$-manifold* (with or without boundary) and $(x^i)$ be smooth coordinates on an open subset $U \subseteq M$. 
>
>Suppose $f: M \to \mathbb{R}$ is a smooth map. The **gradient** of $f$ can be written in terms of coordinate basis frame:
>$$
>\text{grad }f = g^{i,j}\frac{ \partial f}{ \partial x^{i} }\frac{\partial }{ \partial x^{j} }.  
>$$ 
>where $(g^{i,j})$ is the *matrix of the inverse map* $\hat{g}^{-1}: T^{*}M \to TM$.


>[!info]
>Recall $\hat{g}^{-1}: T^{*}M \to TM$ has coordinate formula
>$$
>\widehat{g}^{-1}(\omega)  := g^{i,j}\omega_{i} \, \frac{ \partial }{ \partial x^{j} } 
>$$

- [[Einstein Summation Convention]]


## Explanation





-----------
##  Recommended Notes and References

- [[Gradient of Smooth Map]]
- [[Riemannian Metric and Riemannian Manifold]]


