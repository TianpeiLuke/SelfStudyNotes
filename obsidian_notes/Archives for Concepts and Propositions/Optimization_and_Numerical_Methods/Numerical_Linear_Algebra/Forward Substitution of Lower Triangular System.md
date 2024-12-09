---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - forward_substitution_lower_triangular_system
  - linear_system
topics:
  - numerical_linear_algebra
name: Forward Substitution of Lower Triangular System
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Forward Substitution of Lower Triangular System

>[!important] Definition
>Consider the following **lower triangular system**
>$$
>\begin{align*}
> \left[ \begin{array}{ccccc}a_{11} & &  &  \\[5pt] a_{21} & a_{22} &  &  \\[5pt] \cdots & \cdots & \ddots \\[5pt] a_{n1} & a_{n2} & \cdots & a_{nn}\end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2}\\[5pt] \vdots \\[5pt] x_{n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2}\\[5pt] \vdots \\[5pt] b_{n}\end{array} \right] 
>\end{align*}
>$$
>
>The **row-oriented forward substitution** algorithm that solves the above problem is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- Initialize $$x_{1} = \frac{b_{1}}{a_{11}}$$
>- For $i=2\,{,}\ldots{,}\,n$:
>	- $$x_{i} = \frac{b_{i} - \sum_{j=1}^{i-1}a_{i j}\,x_{j}}{a_{i i}}$$

^7dde49

- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Definition
>**Column-oriented versions** of the above procedures can be obtained by *reversing loop orders*. Note that 
>$$
>\begin{align*}
> \left[ \begin{array}{cc}a_{11} & 0  \\[5pt] A_{2:n,1} & A_{2:n, 2:n} \end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2:n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2:n}\end{array} \right] 
>\end{align*}
>$$
>Thus
>$$
>A_{2:n, 2:n}\,x_{2:n} = b_{2:n} - x_{1}\,A_{2:n,1}
>$$
>
>Specifically, the **column-oriented forward substitution** algorithm that solves the *lower triangular system*  is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- For $j=1\,{,}\ldots{,}\,n-1$:
>	- $$x_{j} = \frac{b_{j}}{a_{jj}}$$
>	- For $k=j+1 \,{,}\ldots{,}\,n$ *in parallel*:
>		- $$b_{k} \leftarrow b_{k} - a_{k,j}\,x_{j}$$
>- Finallly $$x_{n} = \frac{b_{n}}{a_{nn}}$$

^7ef70f

### Parallel Formulation

>[!important] Definition
>the **column-oriented forward substitution** algorithm that solves the *lower triangular system*  is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- For $j=1\,{,}\ldots{,}\,n-1$:
>	- $$x_{j} = \frac{b_{j}^{(j)}}{a_{jj}}$$
>	- $$b_{j+1:n}^{(j+1)} = b_{j+1:n}^{(j)} - a_{j+1:n,j}\;x_{j}$$
>- Finallly $$x_{n} = \frac{b_{n}^{(n)}}{a_{nn}}$$


## Explanation

>[!info]
>In the algorithm, 
>- the **outer loop** of iteration of rows must be **sequential**, i.e. the $x_{k}$ cannot be computed without knowing $x_{j}$ for all $j <k.$
>- the **inner loop** to compute residual can be done in **parallel**
>	- i.e. *row-oriented residual* $$r_{k}:= b_{k} - \sum_{j=1}^{k-1}a_{kj}x_{j}$$
>	- or *column-oriented residual* $$b^{(k+1)}_{k+1:n}:= b_{k+1:n} - x_{k}\,A_{k+1:n,k}$$


>[!info]
>The **row-oriented forward substitution** solves each *equation* **recursively** $$\begin{align*} \sum_{j=1}^{k-1}a_{kj}x_{j}  + a_{kk}\,x_{k} &= b_{k}, \quad k=1\,{,}\ldots{,}\,n \\[5pt] \implies a_{kk}\,x_{k}&= b_{k} - \sum_{j=1}^{k-1}a_{kj}x_{j}  \end{align*}$$ 

>[!info]
>An alternative **recursive structure** for **lower triangular system** involves the following partition
>$$
>\begin{align*}
> \left[ \begin{array}{cc}a_{11} & 0  \\[5pt] A_{2:n,1} & A_{2:n, 2:n} \end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2:n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2:n}\end{array} \right] 
>\end{align*}
>$$
>where 
>- the **trailing principal  submatrix** $A_{2:n, 2:n}$ is also a **lower-triangular matrix**.
>- Specifically, it solve the equation $$\begin{align*}a_{11}\,x_{1} &= b_{1}\\[5pt]A_{2:n, 2:n}\,x_{2:n} &= b_{2:n} - x_{1}\,A_{2:n,1} := b^{(2)}_{2:n}\end{align*}$$
>- In *column-oriented forward substitution*, we remove the *leftmost column* and *top row* of coefficient matrix at each iteration $$A \to A_{2:n, 2:n} \,{\to}\ldots{\to}\,A_{n-1:n, n-1:n} \to A_{n,n} = a_{nn}$$
>- At each iteration $k$,  the system of equations becomes $$\begin{align*}a_{kk}\,x_{k} &= b_{k}^{(k)}\\[5pt]A_{k+1:n, k+1:n}\,x_{k+1:n} &= b_{k+1:n}^{(k)} - x_{k}\,A_{k+1:n,k} := b^{(k+1)}_{k+1:n}\end{align*}$$

- [[Principal Submatrix]]
- [[Partition of Matrix and Block Matrix]]

>[!info]
>The **column-oriented forward substitution** can be considered as solving the linear system based on this recursive structure.
>
>- At step $k=1\,{,}\ldots{,}\,n$, 
>	-  solves the *lower triangular system* $$A_{k+1:n, k+1:n}\,x_{k+1:n} = b^{(k+1)}_{k+1:n}$$ where $$b^{(k+1)}_{k+1:n} := b^{(k)}_{k+1:n} - x_{k}\,A_{k+1:n,k}$$  
>	- and the upper corner is $$x_{k} = \frac{b_{k}^{(k)}}{a_{kk}}$$

>[!info]
>We can overwrite the vector $b$ as solution $x$
>$$
>b_{i} \leftarrow \frac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,b_{j}}{a_{i,i}}
>$$
>Similarly for column-oriented,
>$$
>b_{j+1:n} \leftarrow b_{j+1:n} - a_{j+1:n,j}\;b_{j}
>$$
>Thus the **space complexity** of **forward substitution algorithm** is $O(1)$.

## Algorithm Complexity Analysis

>[!important]
>Since the algorithm need to access each entry $a_{i,j}$ by row, the **time complexity** of the algorithm is $$O\left( n^2 \right)$$

- [[Algorithm Big-O Notations and Rate of Growth]]
- [[Algorithm RAM Model and Complexity Analysis]]




-----------
##  Recommended Notes and References


- [[Triangular System of Equations]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Back Substitution of Upper Triangular System]]
- [[Triangular Matrix and Block Triangular Matrix]]


- [[Matrix Computations by Golub]] pp 106 - 109
- [[Matrix Analysis by Horn]] pp 216
- [[Convex Optimization by Boyd]] pp 664 - 665