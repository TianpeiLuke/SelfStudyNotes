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


- [[Unitary and Orthogonal Transformation]]
- [[Unitary Group]]
- [[Unitary Similarity and Unitary Diagonalizable]]

>[!important] Definition
>Let $A\in M_{n}$ have *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>The **Schur form** or **Schur triangularization** of $A$ is represented as
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

- [[Eigenvalue and Eigenvector for Linear Map]]


### Real Schur Form

>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$.
>
>There exists a real **nonsingular** $S\in \mathbb{R}^{n\times n}$ such that $$S^{-1}\,A\,S$$ is a **real upper triangular matrix**  $$T = \left[ \begin{array}{cccc}A_{1} & \star  & \cdots & \star \\[5pt]  & A_{2} &  &  \\[5pt] &  & \ddots &  \vdots\\[5pt] &  &  & A_{n} \\[5pt] \end{array}\right] \in M_{n}$$ where each $A_{i}$ is either $1\times 1$ or $2 \times 2$.
>- If $A_{i}\in \mathbb{R}$ then $A_{i} = \lambda_{i}$ is the **real eigenvalue** of $A$;
>- If $A_{i}\in \mathbb{R}^{2\times 2}$, then it has a special form that displays the **a conjugate pair** of **non-real eigenvalues** of $A$: $$\left[ \begin{array}{cc}a & b \\-b & a\end{array} \right],\quad a,b\in \mathbb{R}, b>0 $$ when the *complex eigenvalues* are of form $\lambda_{i} = a \pm ib.$
>- The **diagonal blocks** are completely determined by the **eigenvalues** of $A$; they may appear in any prescribed order.


- [[General Linear Group]]
- [[Similarity Relation between Linear Maps and Matrices]]

>[!important] Theorem
>Let $A\in \mathbb{R}^{n\times n}$.
>
>There exists a real **orthogonal** $Q\in O(n) \subset  \mathbb{R}^{n\times n}$ such that $$Q^{T}\,A\,Q$$ is a **real upper triangular matrix**  $$T = \left[ \begin{array}{cccc}A_{1} & \star  & \cdots & \star \\[5pt]  & A_{2} &  &  \\[5pt] &  & \ddots &  \vdots\\[5pt] &  &  & A_{n} \\[5pt] \end{array}\right] \in M_{n}$$ where each $A_{i}$ is either $1\times 1$ or $2 \times 2$.
>- If $A_{i}\in \mathbb{R}$ then $A_{i} = \lambda_{i}$ is the **real eigenvalue** of $A$;
>- If $A_{i}\in \mathbb{R}^{2\times 2}$, then it has **a conjugate pair** of **non-real eigenvalues** of $A$ (but **no special form**)
>- The **ordering** of its *diagonal blocks* may be prescribed in the following sense:
>	- If the *real eigenvalues* and *conjugate pairs* of *non-real eigenvalues* of $A$ are listed in a prescribed order, then the *real eigenvalues* and *conjugate pairs* of *non-real eigenvalues* of the respective diagonal blocks $A_{1} \,{,}\ldots{,}\,A_{m}$ of $Q^{T} A Q$ are in the *same order*.





## Explanation


## Commuting Family

>[!important] Theorem
>Let $\mathcal{F} \subseteq M_{n}$ be a nonempty **commuting family.**
>
>Then there exists a **unitary matrix** $U\in M_{n}$ such that $$U^{*}\,A\,U$$ is **upper triangular** for **every** $A\in \mathcal{F}$.




-----------
##  Recommended Notes and References


- [[Unitary Similarity and Unitary Diagonalizable]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 101 - 106
- [[Matrix Computations by Golub]]