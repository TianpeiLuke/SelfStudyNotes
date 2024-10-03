---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_qr
  - shift_strategy_qr
topics:
  - numerical_linear_algebra
name: Shift Strategy for Faster Symmetric QR Iterations
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Shift Strategy for Faster Symmetric QR Iterations


>[!info]
>We can improve the *rate of convergence* for *symmetric QR iteration* with **shifts.** 

>[!important] Definition
>The **shifted symmetric QR iteration** algorithm *approximates* the **eigenvalues** $D$ of $A$ by producing a sequence of *unitarily similar Tridiagonal matrices* $\{T_{k}\}_{k\ge 1}$ as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: **shift parameter** $\mu\in \mathbb{R}$
>- Initialize with **tridiagonal reduction** $$T_{0} = U_{0}^{*}\,A\,U_{0}$$
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Compute the **QR factorization** of *tridiagonal matrix* $T_{k-1}$ **shifted by** $\mu$  $$U_{k}\,R_{k} = T_{k-1} -\mu I$$
>	- Apply $U_{k}$ to **column** of $R_{k}$ with **additional shifting** to obtain new *unitary similar* **tridiagonal matrix** $T_{k}$ $$T_{k} = R_{k}\,U_{k} + \mu I$$

^4796e1

- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

### Wilkinson Shift

>[!info]
>Consider the **symmetric and tridiagonal matrix**
>$$T = \left[ \begin{array}{ccccc}a_{1} & b_{1} &  &  0 \\[5pt] b_{1} & a_{2} & \ddots &   \\[5pt]   & \ddots & \ddots &  b_{n-1} \\[5pt] 0 &    & b_{n-1} & a_{n}\end{array} \right].$$
>
>One effective way is to choose the **shift** $\mu$ as the **eigenvalue** of *trailing principal submatrix* $$T_{\left\{ n-1,n \right\}, \left\{ n-1,n \right\}} = \left[ \begin{array}{cc}a_{n-1} & b_{n-1} \\ b_{n-1} & a_{n}\end{array} \right] $$ 

>[!important] Definition
>The **Wilkinson shift** is estimated as the *eigenvalue* of the *trailing $2\times 2$ principal submatrix* of symmetric tridiagonal matrix $$T_{\left\{ n-1,n \right\}, \left\{ n-1,n \right\}} = \left[ \begin{array}{cc}a_{n-1} & b_{n-1} \\ b_{n-1} & a_{n}\end{array} \right]$$ that is *closer* to $a_{n}$
>
>That is, the **Wilkinson shift** is equal to $$\mu = a_{n} + d - \text{sgn}(d)\sqrt{ d^2 + b_{n-1}^2 }$$ where $$d= \frac{a_{n-1} - a_{n}}{2}$$

### Implicit Wilkinson Shift

>[!info]
>It is possible to combine two steps from $T$ to $T_{+} = RU+\mu I$ where $$T_{+} = U^{T}TU$$ *without explicitly forming the matrix* $$T - \mu I.$$

^2ee320

>[!info]
>The idea is to use **Given rotation** $G_{i} := G(i,i+1, \theta_{i})$ so that $$G_{1}\,e_{1} = Ue_{1}$$ and we chose the *unwanted nonzero elements* in second off-diagonal terms out.
>
>By **Implicit Q theorem** in [[Tridiagonal Decomposition of Symmetric Matrix]], as long as we make sure the **first column matches** $$Ze_{1} = G_{1}e_{1} = Ue_{1}$$ for $$Z = G_{1}G_{2}\,{}\ldots{}\,G_{n-1},$$ and $$Z^{T}TZ$$ is **tridiagonal**, the resulting $Z^{T}TZ$ is the same as the result of **explicit shift**

![[Givens Rotations and Jacobi Rotations#^05b457]]


>[!important] Definition
>The **implicit symmetric QR step for Wilkinson shift** is described as follow:
>- *Require*: $T\in \mathbb{R}^{n\times n}$ symmetric and tridiagonal
>- Compute the **Wikinson shift** based on the *trailing $2\times 2$ principal submatrix* of $T$
>	- $$d = \frac{T_{n-1, n-1} - T_{n,n}}{2}$$
>	- $$\mu = T_{n,n} - \frac{T_{n,n-1}^2}{d + \text{sgn}(d)\sqrt{ d^2 + T_{n,n-1}^2 }}$$
>- Choose initial *shifted vector* from *first column* of *leading $2\times 2$ principal submatrix* $$\left[\begin{array}{c}x \\ z \end{array} \right]  := \left[\begin{array}{c}T_{1,1} - \mu \\ T_{2,1} \end{array} \right] $$
>- For $k=1\,{,}\ldots{,}\,n-1$:
>	- Compute **Givens parameters**:  $$(\cos(\theta^{(k)}), \sin(\theta^{(k)})) := (c^{(k)}, s^{(k)}) = \text{Givens}(x, z)$$
>	- **Apply Givens transformation** on both *rows and columns* of *tridiagonal matrix* $$T^{(k)} = G_{k}^{T}\,T^{(k-1)}\,G_{k}$$ where $G_{k} = G(k, k+1, \theta^{(k)})$
>	- If $k < n-1$:
>		- Choose new columns from off-diagonal term of $k$-th column $$\left[\begin{array}{c}x \\ z \end{array} \right]  := \left[\begin{array}{c}T_{k+1,k}^{(k)}  \\ T_{k+2,k}^{(k)} \end{array} \right] $$
>- *Return*: $$T^{(n-1)} = Z^{T}TZ$$ where 
>	- $Z = G_{1}\,{}\ldots{}\,G_{n-1}$ is the orthogonal matrix formed by *product of Givens rotations*.
>	- $R = Z^{T}(T-\mu I)$ is an *upper triangular matrix*
>	- $\mu$ is the *eigenvalue* of the *trailing $2\times 2$ principal submatrix* of $T$ that is closer to $T_{n,n}$

^ab31a0

- [[Givens Rotations and Jacobi Rotations]]
- [[Shift Strategy for Faster QR Iterations]]

>[!important]
>This algorithm requires about $$30n$$ flops and $$n$$ square roots.
>- Note that the *Given rotation* on **tridiagonal matrix** only requires $O(n)$ flops



## Explanation

>[!important] Proposition
>Let $T$ be **tridiagonal**. For any $s\in \mathbb{R}$, let $$T- sI = QR$$ be the *QR factorization* of $T$. 
>
>Then $$T_{+} := RQ + sI$$ is also **tridiagonal**

- [[Shift Strategy for Faster QR Iterations]]

>[!important] Proposition
>If $T$ is **unreduced**, then the first $n-1$ columns of $$T - sI$$ are **independent** regardless of $s$. 
>
>Thus, if $s\in\lambda(T)$ is an **eigenvalue**, and $$T-sI = QR$$ is the *QR factorization* then 
>- $$R_{n,n} = 0$$
>- and the *last column* of $$T_{+} = RQ + sI$$ is equal to $s e_{n} = [0\,{,}\ldots{,}\,0,s]^{T}$

- [[Linear Independence]]





-----------
##  Recommended Notes and References




- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Schur Triangularization and Schur Form]]
- [[Jordan Canonical Form]]
- [[QR Factorization of Matrix]]

- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[QR Iteration Practical for General Eigenvalue Problem]]
- [[Symmetric QR Iteration for Symmetric Eigenvalue Problem]]

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Matrix]]


- [[Matrix Computations by Golub]] pp 385 - 391
- [[Numerical Linear Algebra by Trefethen]] pp 212, 219 - 224