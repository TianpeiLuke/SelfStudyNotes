---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - schur_triangularization
  - schur_form
topics:
  - matrix_analysis
  - linear_algebra
name: Schur Triangularization and Schur Form
date of note: 2024-09-16
---

## Concept Definition

>[!important]
>**Name**: Schur Triangularization and Schur Form

>[!important] Theorem
>Let $A\in M_{n}$ have *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ in any prescribed order and let $x\in \mathbb{C}^{n}$ be a *unit vector* such that $$Ax = \lambda_{1}x$$ i.e. $x$ is the *eigenvector* associated with $\lambda_{1}$.
>
>- There exists a **unitary matrix** $$U = [x\; u_{2} \,{\;}\ldots{\;}\,u_{n}]\in M_{n}$$ such that $$U^{*}\,A\,U = T = [t_{i,j}]$$ is **upper triangular** with *diagonal entries* $t_{i,i}= \lambda_{i}$, $i=1\,{,}\ldots{,}\,n.$
>- If $A \in \mathbb{R}^{n\times n}$ has **only real eigenvalues**, then $x$ may be chosen to be **real** and there is a **real orthogonal** $$Q = [x\; q_{2}\,{\;}\ldots{\;}\,q_{n}]\in O(n) \subset \mathbb{R}^{n\times n}$$ such that $$Q^{T}\,A\,Q = T = [t_{i,j}]$$ is **upper triangular** with *diagonal entries* $t_{i,i}= \lambda_{i}$, $i=1\,{,}\ldots{,}\,n.$

^b40ca5

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Unitary Similarity and Unitary Diagonalizable]]

>[!important] Definition
>Let $A\in M_{n}(\mathbb{C})$ have *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>The **Schur form** or **Schur triangularization (decomposition)** of $A$ is represented as
>$$
>A = U\,T\,U^{*}
>$$ 
>where 
>$$
>T = \left[ 
>\begin{array}{cccc}
> \lambda_{1} & t_{1,2} & \cdots & t_{1,n} \\[5pt] 
>  & \lambda_{2} & \cdots & t_{2,n} \\[5pt] 
>  &  & \ddots & \vdots \\[5pt] 
>&  &  & \lambda_{n} \\[5pt] 
>\end{array}
\right] \in M_{n}
>$$
>is an **upper triangular matrix** and $U = [x\; u_{2} \,{\;}\ldots{\;}\,u_{n}]\in \mathcal{U}(n)$ is **unitary**.
>- The columns $u_{i}$ are called the **Schur vectors.**

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]


>[!info]
>The Schur form can be represented as 
>$$
>T = D + N
>$$
>where $D$ is the **diagonal matrix** with *eigenvalue entries* and $N$ is strictly upper triangular, which is a **nilpotent matrix.**

- [[Nilpotent Linear Transformation and Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Matrix Computations by Golub]] pp 351,

### Linear Algebra Interpretation

>[!important] Theorem (Canonical Form Theorem)
>Let $A\in \mathcal{L}(V)$ be any linear transformation on an $n$-dimensional vector space $V$.
>
>Then there exists $n+1$ **subspaces** $\mathcal{S}_{0} \,{,}\ldots{,}\,\mathcal{S}_{n}$ with the following properties:
>- each $\mathcal{S}_{j}$, $j=0\,{,}\ldots{,}\,n$, is **invariant under $A$**,
>- the **dimension** of subspace $\mathcal{S}_{j}$ is $j$,
>- these subspaces are *simply ordered* $$\emptyset = \mathcal{S}_{0} \subseteq \mathcal{S}_{1} \,{\subseteq}\ldots{\subseteq}\,\mathcal{S}_{n} = V$$

- [[Invariance under Linear Transformation]]
- [[Reducibility of Linear Transformation]]
- [[Simple Order Relation]]
- [[Finite Dimensional Vector Spaces by Halmos]] pp 106 - 107

>[!info]
>A direct implication of this theorem is that we can find a set of basis recursively for $V$ 
>- For $\text{span}\{x_{1}\} = \mathcal{S}_{1}$, choose $x_{1}$ as any vector in $\mathcal{S}_{1}$
>- For $j=2\,{,}\ldots{,}\,n$:
>	- choose a basis vector $x_{j} \in \mathcal{S}_{j} \setminus\, \mathcal{S}_{j-1}$
>
 Thus for each $j$, $$Ax_{j} = \sum_{i \le j}a_{i,j}\,x_{i} \in \mathcal{S}_{j}$$ as $$a_{i,j} =0 \text{ if }i > j.$$ In other word, the **matrix representation of $A$** is an **upper triangular form.**

- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Theorem
>Let $A\in \mathcal{L}(V)$ be any linear transformation on an $n$-dimensional vector space $V$.
>
>Then there exists a set of basis $\mathcal{B}:=\left\{ x_{1}\,{,}\ldots{,}\, x_{n}\right\}$ of $V$ such that the **representation** $A$ under $\mathcal{B}$ is an **upper triangular matrix** $T$. 
>- That is, there exists a non-singular matrix $U= [x_{1}\,{,}\ldots{,}\, x_{n}]$, such that $$A = U\,T\,U^{*}$$ 


### Real Schur Form

>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$.
>
>There exists a real **nonsingular** $S\in \mathbb{R}^{n\times n}$ such that $$S^{-1}\,A\,S$$ is a **real quasi-upper-triangular matrix**  $$T = \left[ \begin{array}{cccc}A_{1} & \star  & \cdots & \star \\[5pt]  & A_{2} &  &  \\[5pt] &  & \ddots &  \vdots\\[5pt] &  &  & A_{n} \\[5pt] \end{array}\right] \in M_{n}$$ where each $A_{i}$ is either $1\times 1$ or $2 \times 2$.
>- If $A_{i}\in \mathbb{R}$ then $A_{i} = \lambda_{i}$ is the **real eigenvalue** of $A$;
>- If $A_{i}\in \mathbb{R}^{2\times 2}$, then it has a special form that displays the **a conjugate pair** of **non-real eigenvalues** of $A$: $$\left[ \begin{array}{cc}a & b \\-b & a\end{array} \right],\quad a,b\in \mathbb{R}, b>0 $$ when the *complex eigenvalues* are of form $\lambda_{i} = a \pm ib.$
>- The **diagonal blocks** are completely determined by the **eigenvalues** of $A$; they may appear in any prescribed order.

- [[Quasi-triangular Matrix and Quasi-diagonal Matrix]]
- [[General Linear Group]]
- [[Similarity Relation between Linear Maps and Matrices]]

>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$.
>
>There exists a real **orthogonal** $Q\in O(n) \subset  \mathbb{R}^{n\times n}$ such that $$Q^{T}\,A\,Q$$ is a **real quasi-upper-triangular matrix**  $$T = \left[ \begin{array}{cccc}A_{1} & \star  & \cdots & \star \\[5pt]  & A_{2} &  &  \\[5pt] &  & \ddots &  \vdots\\[5pt] &  &  & A_{n} \\[5pt] \end{array}\right] \in M_{n}$$ where each $A_{i}$ is either $1\times 1$ or $2 \times 2$.
>- If $A_{i}\in \mathbb{R}$ then $A_{i} = \lambda_{i}$ is the **real eigenvalue** of $A$;
>- If $A_{i}\in \mathbb{R}^{2\times 2}$, then it has **a conjugate pair** of **non-real eigenvalues** of $A$ (but **no special form**)
>- The **ordering** of its *diagonal blocks* may be prescribed in the following sense:
>	- If the *real eigenvalues* and *conjugate pairs* of *non-real eigenvalues* of $A$ are listed in a prescribed order, then the *real eigenvalues* and *conjugate pairs* of *non-real eigenvalues* of the respective diagonal blocks $A_{1} \,{,}\ldots{,}\,A_{m}$ of $Q^{T} A Q$ are in the *same order*.


>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ have *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>The **real Schur form (RSF)** of $A$ is represented as
>$$
>A = Q\,T\,Q^{T}
>$$ 
>where 
>$$
>T = \left[ \begin{array}{cccc}A_{1} & \star  & \cdots & \star \\[5pt]  & A_{2} &  &  \\[5pt] &  & \ddots &  \vdots\\[5pt] &  &  & A_{n} \\[5pt] \end{array}\right] \in \mathbb{R}^{n\times n}
>$$
>is an **quasi-upper-triangular matrix** with each $A_{i}$ being either $1\times 1$ or $2 \times 2$, and $Q\in \mathcal{O}(n)$ is **orthogonal**.
>- The columns $u_{i}$ are called the **real Schur vectors.**


## Explanation

>[!important]
>The importance of **Schur decomposition** is that it applies to **all matrices / maps** regardless its property, 
>- while the **eigen-decomposition** only applies to **normal matrices / maps** including the **Hermitian matrices** / **self-adjoint maps**. 

- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


>[!important]
>**Schur form** of a matrix is a canonical form  that displays **eigenvalues** but **not eigenvectors**. 
>- It can be computed efficiently using **iterative methods** based on **QR factorization**

- [[QR Factorization of Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Classical Iterations to approximate Solution of Sparse Linear System]]

>[!info]
>Compared with the **spectral theorem** or **eigen-decomposition**, **Schur decomposition** do not requires $A$ to be *normal* or *self-adjoint* (*Hermitian* or *Symmetric*). 
>
>Thus the *canonical form* is *not a diagonal matrix* $$D = \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})$$ with eigenvalues $\lambda_{i}$ but an **upper triangular matrix** $$T = D + N$$ with eigenvalue diagonal entries

>[!important] 
>Every matrix $A\in M_{n}$ is **unitarily similar** to an **upper triangular matrix** $$A \sim T=D+N$$
>
>Among them, $A$ is **unitarily similar** to a **diagonal matrix** $$A \sim D$$ *if and only if* $A$ is **normal matrix**. $$A^{*}A = AA^{*}.$$

>[!info]
>The **Jordan decomposition** is an *nonunitary analog* to the **Schur decomposition** for unsymmetric matrix.

- [[Jordan Canonical Form]]

## Commuting Family

>[!important] Theorem
>Let $\mathcal{F} \subseteq M_{n}$ be a nonempty **commuting family.**
>
>Then there exists a **unitary matrix** $U\in M_{n}$ such that $$U^{*}\,A\,U$$ is **upper triangular** for **every** $A\in \mathcal{F}$.

- [[Commuting Family of Matrices]]

## Jordan Form

- [[Jordan Canonical Form]]





-----------
##  Recommended Notes and References


- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Triangular Matrix and Block Triangular Matrix]]


- [[Linear Map]]
- [[Linear Subspace]]
- [[Matrix]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]] pp 106 - 107
- [[Matrix Analysis by Horn]] pp 101 - 106
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 98
- [[Matrix Computations by Golub]] pp 351, 440
- [[Numerical Linear Algebra by Trefethen]] pp 193 - 195
- [[Matrix CookBook by Petersen]] pp 32