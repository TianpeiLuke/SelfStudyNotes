---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - givens_transformation
  - givens_rotation
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Givens Transformation and Givens Rotation
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Givens Transformation and Givens Rotation

![[Elementary Row and Column Operations#^92e828]]


>[!important] Definition
>The **Givens rotations** or **Givens transformations** are of the form
>$$
>G(i, k, \theta) = \left[ \begin{array}{ccccccc}1 & \cdots & 0 & \cdots  & 0 & \cdots & 0 \\ \vdots & \ddots & \vdots &   & \vdots &  & \vdots \\ 0 & \cdots & \cos(\theta) & \cdots  & -\sin(\theta) & \cdots & 0 \\ \vdots &  & \vdots & \ddots  & \vdots &  & \vdots \\ 0 & \cdots & \sin(\theta) & \cdots  & \cos(\theta) & \cdots & 0 \\ \vdots &  & \vdots &   & \vdots & \ddots & \vdots \\0 & \cdots & 0 & \cdots  & 0 & \cdots & 1 \end{array} \right] 
>$$ 
>where $\theta$ is the *rotation angle*.
>- Givens rotations are **orthogonal**.
>- Givens rotations are a **rank-2 correction** $$\begin{align*} G(i, k, \theta) &= I_{n} + (\cos(\theta)-1)\,(e_{i}\,e_{i}^T + e_{k}\,e_{k}^T)  +\sin(\theta)\,e_{k}\,e_{i}^{T} - \sin(\theta)\,e_{i}\,e_{k}^{T} \\[5pt] &= E_{3}(i,k, \sin(\theta)) + E_{3}(k,i, -\sin(\theta)) + E_{2}(i, \cos(\theta)) + E_{2}(k, \cos(\theta)) \end{align*}$$ 
>- Left multiplication by $G(i,k,\theta)$ amounts to a **counterclockwise rotation** of $\theta$ radians in the $(i,k)$ *coordinate plane*. $$G(i,k, \theta)\,x = y$$ 
>	- That is, $$y_{j} = \left\{\begin{array}{cl}\cos(\theta)\,x_{i} - \sin(\theta)\,x_{k}, & \text{ if }j=i\\[5pt] \sin(\theta)\,x_{i} + \cos(\theta)\,x_{k}, & \text{ if }j=k\\[5pt] x_{j} & \text{ if }j\neq i,k \end{array}\right.$$
>	- if $$\cos(\theta) = \frac{x_{i}}{\sqrt{ x_{i}^2  + x_{k}^2}}, \quad \sin(\theta) = \frac{-x_{k}}{\sqrt{ x_{i}^2  + x_{k}^2}},$$ then **Givens rotations** transform one entry into *zero* $$y_{k} =0, \quad y_{i} = \sqrt{ x_{i}^2  + x_{k}^2 }.$$

^956c04

- [[Elementary Row and Column Operations]]
- [[Unitary and Orthogonal Transformation]]

### Algorithm

>[!important] Definition
>The **Givens rotation function** $\text{Givens}(a, b)$ is described as follows:
>- *Require*: scalar $a, b\in \mathbb{R}$
>- If $b =0$:
>	- $$\cos(\theta) = 1; \quad \sin(\theta) = 0.$$
>- Else:
>	- If $|b| > |a|$:
>		- $$\tau = - \frac{a}{b}, \quad \sin(\theta) = \frac{1}{\sqrt{ 1+ \tau^2 }}, \quad \cos(\theta) = \sin(\theta)\,\tau$$
>	- Else:
>		- $$\tau = - \frac{b}{a}, \quad \cos(\theta) = \frac{1}{\sqrt{ 1+ \tau^2 }}, \quad \sin(\theta) = \cos(\theta)\,\tau$$
>- *Return*: $(\cos(\theta), \sin(\theta))$.

>[!info]
>There is no need to compute the angle $\theta$, as we just need $c:= \cos(\theta), \; s=\sin(\theta).$


>[!important]
>The **Givens rotations** requires $5$ flops, and a *single square root*.

### Applying Givens Rotation

>[!important] Definition
>Let $A\in \mathbb{R}^{m\times n}$, $c= \cos (\theta)$, $s = \sin(\theta)$.
>
>$$G(i,k, \theta)\,A = A$$ Applying the **Givens rotations** on $A$ only affects two rows, 
>- For $j=1\,{,}\ldots{,}\,n$:
>	- $$\tau_{1} = A_{i,j}$$
>	- $$\tau_{2} = A_{k,j}$$
>	- $$A_{i,j} = c\,\tau_{1} - s\,\tau_{2}$$
>	- $$A_{k,j} = s\,\tau_{1} + c\,\tau_{2}$$

>[!important] Definition
>Let $A\in \mathbb{R}^{m\times n}$, $c= \cos (\theta)$, $s = \sin(\theta)$.
>
>$$A\,G(i,k, \theta)^{T} = A$$ Applying the **Givens rotations** on $A$ only affects two rows, 
>- For $j=1\,{,}\ldots{,}\,n$:
>	- $$\tau_{1} = A_{j,i}$$
>	- $$\tau_{2} = A_{j,k}$$
>	- $$A_{j,i} = c\,\tau_{1} - s\,\tau_{2}$$
>	- $$A_{j,k} = s\,\tau_{1} + c\,\tau_{2}$$



## Explanation

>[!quote]
>**Householder reflections** are exceedingly useful for introducing zeros on a grand scale, e.g., the annihilation of *all but the first component* of a vector. However, in calculations where it is necessary to zero elements more *selectively*, **Givens rotations** are the transformation of choice. 
>
>-- [[Matrix Computations by Golub]] pp 239

- [[Householder Transformation and Householder Reflection]]


## Givens QR Factorization

- [[Givens QR Factorization]]



-----------
##  Recommended Notes and References


- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]

- [[Householder Transformation and Householder Reflection]]
- [[QR Factorization of Matrix]]
- [[Singular Value Decomposition of Linear Map]]

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

- [[Elementary Row and Column Operations]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 239 - 243