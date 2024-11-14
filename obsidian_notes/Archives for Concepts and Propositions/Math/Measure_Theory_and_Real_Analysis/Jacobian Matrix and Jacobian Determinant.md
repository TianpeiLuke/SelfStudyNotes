---
tags:
  - concept
  - math/calculus
  - math/real_analysis
  - math/differential_geometry
keywords:
  - jacobian_matrix
  - jacobian_determinant
topics:
  - calculus
  - real_analysis
  - differential_geometry
name: Jacobian Matrix and Jacobian Determinant
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: Jacobian Matrix and Jacobian Determinant

>[!important] Definition
>Let $f: \mathbb{R}^{n} \to \mathbb{R}^{m}$ be a smooth function where $$f(x) := (f^{1}(x) \,{,}\ldots{,}\,f^{m}(x))$$ and  each component function $f^{i}: \mathbb{R}^{n} \to \mathbb{R}$ is smooth $f^{i}\in \mathcal{C}^{1}(\mathbb{R}^{n})$
>
>The **Jacobian matrix** at $x\in \mathbb{R}^{n}$  is defined as 
>$$
>\begin{align}
>  \left[\begin{array}{ccc}
> \dfrac{\partial\,f^{1}}{\partial\,x^{1}}(x)& \ldots& \dfrac{\partial\,f^{1}}{\partial\,x^{n}}(x)\\
> \vdots & \ddots & \vdots\\
> \dfrac{\partial\,f^{m}}{\partial\,x^{1}}(x)& \ldots& \dfrac{\partial\,f^{m}}{\partial\,x^{n}}(x)
> \end{array}\right]_{m \times n}
> \end{align}
>$$ 
>- Each *row* is the *gradient* of component function $$\nabla f^{i} := \frac{ \partial f^{i} }{ \partial x} := \left(  \frac{\partial\,f^{i}}{\partial\,x^{1}}(x) \,,\,\ldots \,,\,\frac{\partial\,f^{i}}{\partial\,x^{n}}(x)\right)$$
>- Each *column* is denoted as $$\frac{ \partial f }{ \partial x^{j}} := \left(  \frac{\partial\,f^{1}}{\partial\,x^{j}}(x) \,,\,\ldots \,,\,\frac{\partial\,f^{m}}{\partial\,x^{j}}(x)\right)$$
>- The **Jacobian matrix** is denoted as $$Df := \frac{ \partial f }{ \partial x } :=  \frac{ \partial (f^1 \,{,}\ldots{,}\,f^{m}) }{ \partial (x^{1} \,{,}\ldots{,}\,x^{n}) } $$

- [[Differentiability in Higher Dimensions Euclidean Space]]

>[!important] Definition
>Let $f: \mathbb{R}^{n} \to \mathbb{R}^{n}$ be a smooth function.
>
>The *determinant* of *Jacobian matrix* is the **Jacobian determinant**
>$$\det(Df) := \det \left( \frac{ \partial (f^1 \,{,}\ldots{,}\,f^{n}) }{ \partial (x^{1} \,{,}\ldots{,}\,x^{n}) }  \right) $$

### Differentials in High Dimensional Space

![[Differentiability in Higher Dimensions Euclidean Space#^d50646]]

- [[Differentiability in Higher Dimensions Euclidean Space]]
- [[Fréchet Derivative and Strong Derivative in Banach Space]]

### Geometric Interpretation

![[Coordinate Representation of Differential at Point#^9a537d]]

- [[Smooth Map between Euclidean Spaces]]
- [[Derivation of Smooth Map at point and Tangent Vector]]
- [[Differential of a Smooth Map at Point]]
- [[Coordinate Representation of Differential at Point]]
- [[Coordinate Representation of Differential]]

### Rank of Smooth Map 

>[!important]
>The **rank** of Jacobian matrix compared to the row or column dimension defines the *submersion*, *immersion* map.

- [[Rank of Smooth Map]]
- [[Rank Theorem]]
- [[Smooth Submersion]]
- [[Smooth Immersion]]


## Explanation



## Inverse Function Theorem

![[Inverse Function Theorem#^13f7b2]]

- [[Inverse Function Theorem]]



## Change of Variables in Pullback Operation

![[Coordinate Representation of Pullback of k-Forms#^164bfd]]

- [[Coordinate Representation of Pullback of k-Forms]]
- [[Coordinate Representation of Pullback of Covector]]
- [[Pullback of k-Form]]

## Change of Coordinates

![[Vector Bundle#^446434]]

- [[Vector Bundle]]

## Newton's Method and Quadratic Programming


- [[Newton Method]]
- [[Quadratic Programming]]



-----------
##  Recommended Notes and References



- [[Cotangent Space and Differential of Map]]

- [[Matrix]]
- [[Determinant of Linear Transformation]]


- [[Principles of Mathematical Analysis by Rudin]]
- [[Introduction to Smooth Manifolds by Lee]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 44, 820
- Wikipedia [Jacobian_matrix_and_determinant](https://en.wikipedia.org/wiki/Jacobian_matrix_and_determinant)