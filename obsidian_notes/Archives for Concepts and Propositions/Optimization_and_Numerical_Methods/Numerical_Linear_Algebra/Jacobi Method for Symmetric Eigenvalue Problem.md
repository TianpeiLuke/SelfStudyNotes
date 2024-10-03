---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - jacobi_method_symmetric_eigenvalue
  - givens_rotation
  - jacobi_rotations
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Jacobi Method for Symmetric Eigenvalue Problem
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Jacobi Method for Symmetric Eigenvalue Problem

![[Givens Rotations and Jacobi Rotations#^956c04]]

- [[Givens Rotations and Jacobi Rotations]]

### Symmetric Schur Decomposition on $2\times 2$ Matrix

>[!important] 
>Let  $A\in \mathbb{R}^{2\times 2}$ be a symmetric $2\times 2$ matrix, i.e. $$\left[ \begin{array}{cc} a_{pp} & a_{pq} \\ a_{pq} & a_{qq} \end{array} \right].$$ Consider the task of **symmetric Schur decomposition** with *Givens rotation* i.e. finding $c, s$ such that $$\left[ \begin{array}{cc} b_{pp} & 0 \\0 & b_{qq} \end{array} \right] = \left[ \begin{array}{cc} c & s \\ -s & c \end{array} \right]^{T}\;\left[ \begin{array}{cc} a_{pp} & a_{pq} \\ a_{pq} & a_{qq} \end{array} \right]\;\left[ \begin{array}{cc} c & s \\ -s & c \end{array} \right]$$
>- The *off-diagonal term* of $B$ is $0$ so the *following equation* holds $$ 0 = b_{pq} = a_{pq}(c^2 - s^2) + (a_{pp} - a_{qq})cs$$
>	- if $a_{pq} = 0$, then $cs =0$. So we set $c=1$ and $s=0$
>	- if $a_{pq} \neq 0$, then we can define $$t := \frac{s}{c} := \tan(\theta),\quad \tau := \frac{(a_{qq} - a_{pp})}{2a_{pq}}$$  The above equation becomes $$t^2 + 2\tau t - 1 = 0$$
>		- The solution is $$t_{min} = \left\{\begin{array}{cl}\dfrac{1}{\tau + \sqrt{ 1 + \tau^2 }} & \text{ if }\tau \ge 0\\[5pt] \dfrac{1}{\tau - \sqrt{ 1 + \tau^2 }} & \text{ if }\tau < 0 \end{array}\right.$$
>		- This implies $|\theta| \le \dfrac{\pi}{4}$
>		- $$c = \frac{1}{\sqrt{ 1 + t_{min}^2 }}, \quad s = t_{min}\,c.$$
>- The **Frobenius norm** is **preserved** under unitary transformation. Thus the following equation hold $$a_{pp}^2 + a_{qq}^2 + 2a_{pq}^2 = b_{pp}^2 + b_{qq}^2$$


>[!important] Definition
>The following subroutine **$\text{symSchur2}(A, p, q)$** compute the symmetric Schur decomposition 
>$$\left[ \begin{array}{cc} b_{pp} & 0 \\0 & b_{qq} \end{array} \right] = \left[ \begin{array}{cc} c & s \\ -s & c \end{array} \right]^{T}\;\left[ \begin{array}{cc} a_{pp} & a_{pq} \\ a_{pq} & a_{qq} \end{array} \right]\;\left[ \begin{array}{cc} c & s \\ -s & c \end{array} \right]$$ 
>of a $2\times 2$  principle submatrix $A_{\left\{ p,q \right\}, \left\{ p,q \right\}}\in \mathbb{R}^{2\times 2}$ 
>- *Require*: $A\in \mathbb{R}^{n\times n}$ **symmetric**
>- *Require*: $p,q\in \left\{ 1\,{,}\ldots{,}\,n \right\}$
>- If $A_{p,q} \neq 0$:
>	- Compute the ratio $\tau$ as $$\tau = \frac{(A_{q,q} - A_{p,p})}{2\,A_{p,q}}$$
>	- If $\tau \ge 0$:
>		- Compute $t:=\tan(\theta)$ as $$t = \frac{1}{\tau + \sqrt{ 1 + \tau^2 }} $$
>	- Else
>		- $$t = \frac{1}{\tau - \sqrt{ 1 + \tau^2 }} $$
>	- Compute $c:= \cos(\theta)$, and $s =\sin(\theta)$ as $$c = \frac{1}{1 + t^2}, \quad s= tc.$$
>- Else: 
>	- Set $c:= \cos(\theta)$, and $s =\sin(\theta)$ $$c = 1, \quad s = 0.$$
>- *Return*: $(c,s)$ pair where $c= \cos(\theta)$, $s = \sin(\theta)$

- [[Principal Submatrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Frobenius Norm of Matrix]]

### Classical Jacobi Algorithm

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be a **symmetric matrix**. 
>
>The **classical Jacobi algorithm** that find an *orthogonal matrix* $V$ such that $$A \leftarrow V^{T}\,A\,V$$ with *total norm* of *off-diagonal terms* $$\lVert \text{off}\left( V^{T}\,A\,V \right) \rVert_{F} \le \text{tol}\,\cdot \lVert A \rVert_{F}$$ is described as follow
>- *Require*: $A\in \mathbb{R}^{n\times n}$ *symmetric*
>- *Require*: tolerance $\text{tol} >0$ 
>- Initialize $$V = I_{n}, \quad \delta := \text{tol}\cdot \lVert A \rVert_{F}$$
>- While $\lVert \text{off}(A) \rVert_{F} > \delta$:
>	- Choose $p,q\in \left\{ 1\,{,}\ldots{,}\,n \right\}$ such that the *off-diagonal term* is maximized $$\lvert A_{p,q} \rvert = \max_{i\neq j}\lvert A_{i,j} \rvert  $$
>	- **Construct** the **Givens (Jacobi) rotation** such that the principle sub-matrix $A_{\left\{ p,q \right\}, \left\{ p,q \right\}}$ is **diagonalized** $$[c, s] = \text{symSchur2}(A, p, q)$$
>	- **Apply** *Givens (Jacobi) rotation* for both rows and columns of $A$ $$A \leftarrow G(p, q, \theta)^{T}\,A\,G(p, q, \theta)$$
>		- This process estimates the **eigenvalue**
>	- **Right multiply** the *Givens (Jacobi) rotation* to orthogonal matrix $V$ $$V \leftarrow V\,G(p, q, \theta)$$
>		- This process estimate the **eigenvector**
>- *Return*: $$V^{T}\,A\,V$$ that overwrites $A$


- [[Unitary and Orthogonal Transformation]]
- [[Hermitian or Symmetric Matrix]]


## Explanation

>[!important]
>The **main idea** of **Jacobi method** to compute the *eigenvalue and eigenvector* for symmetric matrix $A$ is to reduce the **total Frobenius norm** of **off-diagonal entries**
>$$
>\lVert \text{off}(A) \rVert_{F} :=   \lVert A - A\odot I \rVert_{F} := \sqrt{ \sum_{i\neq j}a_{i,j}^2 }
>$$

- [[Hadamard Product of Matrices]]


## Parallel Computation

>[!quote]
>Jacobi methods for the symmetric eigenvalue problem attract current attention be­ cause they are **inherently parallel**.
>
>-- [[Matrix Computations by Golub]] pp 476




-----------
##  Recommended Notes and References


- [[Givens Rotations and Jacobi Rotations]]
- [[Frobenius Norm of Matrix]]
- [[Schur Triangularization and Schur Form]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Hermitian or Symmetric Matrix]]


- [[Matrix Computations by Golub]] pp 476 - 483