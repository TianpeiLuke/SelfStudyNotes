---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - cramer_rule
topics:
  - matrix_analysis
  - linear_algebra
name: Cramer Rule
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Cramer's Rule

>[!important] Definition
>Let $A = [a_{1} \,{,}\ldots{,}\,a_{n}]\in M_{n}(F)$ be *partitioned* according to its columns, and $b\in F^{n}.$ 
>
>Define 
>$$
> (A \stackrel{i}{\leftarrow} b ) = \left[a_{1} \,{,}\ldots{,}\,a_{i-1},\,b, \,a_{i+1} \,{,}\ldots{,}\,a_{n}  \right] 
>$$
>as an **augmented matrix** obtained by *replacing* $i$-th column $a_{i}$ with $b$.

- [[Partition of Matrix and Block Matrix]]

>[!important] Theorem (Cramer's Rule)
>Let $A = [a_{1} \,{,}\ldots{,}\,a_{n}]\in M_{n}(F)$ be a *nonsingular matrix* where $a_{i}\in F^{n}$ is the $i$-th *column* of $A$, and $b\in F^{n}$. 
>
>Then the **solution** $x= [x_{1} \,{,}\ldots{,}\,x_{n}]$ of the **system of linear equations** $$Ax = b$$ is given by the following identity
>$$
>x_{i} = \frac{\det(A \stackrel{i}{\leftarrow} b)}{\det(A)}, \quad i=1\,{,}\ldots{,}\,n
>$$

- [[Adjugate of Matrix]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


## Explanation

>[!info]
>By [[Laplace Expansion Theorem]], the **vector** formed by *determinant of augmented matrices* is
>$$
>\left[ \det(A \stackrel{i}{\leftarrow} b ) \right]_{i=1}^{n} = \left( \text{adj}(A) \right)\,b \in F^{n}
>$$
>Similarly, for column partitioned matrix $C = [c_{1} \,{,}\ldots{,}\,c_{n}]\in M_{n}$, the **matrix** formed by *determinant of augmented matrices* is
>$$
>\left[ \det(A \stackrel{i}{\leftarrow} c_{j} ) \right]_{i,j} =  \left( \text{adj}(A) \right)\,C \in M_{n}
>$$

>[!info]
>Since
>$$
>A\left( \text{adj}(A) \right) = \det(A)\,I.
>$$
>Thus
> 
>$$
>\begin{align*}
>A\left[ \det(A \stackrel{i}{\leftarrow} b ) \right]_{i}^{n} &=  A\left( \text{adj}(A) \right)\,b =  \det(A)\,b \\[5pt]
>A \left(\det(A)^{-1}\, \det(A \stackrel{i}{\leftarrow} b )  \right)_{i=1}^{n} &= b\\[5pt]
>\iff Ax &= b 
\end{align*}
>$$
>The **Cramer's rule** follows by the fact that $Ax=b$ for non-singular $A$ *exists* and is *unique*.
>$$
>x = \left(\det(A)^{-1}\, \det(A \stackrel{i}{\leftarrow} b )  \right)_{i=1}^{n}
>$$

- [[Adjugate of Matrix]]


## Differential Geometry

### Inner Multiplication of Tensors

- [[Coordinate Representation of Interior Multiplication]]
- [[Interior Multiplication]]






-----------
##  Recommended Notes and References


- [[Reduced Row Echelon Form]]
- [[Jacobi Identity and Minors of the Inverse]]

- [[Laplace Expansion Theorem]]
- [[Partition of Matrix and Block Matrix]]
- [[Determinant of Linear Transformation]]
- [[Matrix]]

- [[Matrix Analysis by Horn]] pp 24