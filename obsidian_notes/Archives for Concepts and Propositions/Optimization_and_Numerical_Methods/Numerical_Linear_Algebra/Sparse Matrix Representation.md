---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - sparse_matrix
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Sparse Matrix Representation
date of note: 2024-10-06
---

## Concept Definition

>[!important]
>**Name**: Sparse Matrix Representation

>[!important] Definition
>Typically, a real vector is used to house the nonzero entries of the matrix and one or two integer  vectors are used to specify their "location." This is called the **compressed-column representation**.
>
>Let $A$ denote a matrix.
>- The **compressed-column representation** stores the nonzero entries *column by column*  in a real vector as $$A.val = [a_{11}, a_{41} \;||\; a_{52} \;||\; a_{23}, a_{33}, a_{63} \;||\; a_{14}, a_{44} \;||\; a_{25}, a_{55}, a_{65}].$$
>- An *integer vector* $A.c$ is used to indicate **where each column begins** in $A.val$, e.g. $$A.c = [1, 3, 4, 7, 9\;||\; 12]$$
>	- By convention, the last component in $A.c$ stores the **number of nonzeros** in $A$ **plus 1**, $$A.c[-1] = \text{nnz}(A) + 1 \equiv \text{the number of nonzeros in }A + 1$$
>	- To retrieve the **$j$-th column** of $A$, (one-indexed) $A_{:,j}$, $$A_{:,j} = A.val[A.c[j]\,:\,A.c[j+1]-1]$$
>- An *integer vector* $A.r$ is used to indicate **row indices of nonzero entries** in $A.val$, e.g. $$A.r = [1, 4 \;||\; 5 \;||\; 2, 3, 6 \;||\; 1, 4 \;||\; 2, 5, 6]$$ 
>	- Assume that $A_{i,j} \neq 0$, to retrieve the $(i,j)$-entry of $A$, 
>		- we use $A.c[j]$ to *locate the entries of column* $j$ in $A.val$
>		- then use $A.r$ to  *retrieve the row indices* and to verify if $A.r[s] = i$
>		- finally, we retrieve the value $A.val[s]$ if the corresponding $A.r[s] = i$
>		- $$A.val[s] = A_{A.r[s], j} = A_{i,j}, \quad \text{ where } s\in [A.c[j]:A.c[j+1]-1]$$

- [[Adjacency List for Sparse Representation of Graph]]

### Matrix-Vector Product Operations 

>[!important] Definition
>The **Gaxpy operation** that computes $$y \leftarrow y + Ax$$ with $A\in \mathbb{R}^{m\times n}$ in **compressed-column format**, and $x\in \mathbb{R}^{n},y\in \mathbb{R}^{m}$ in **conventional dense storage format** is described as follow:
>- For $j=1\,{,}\ldots{,}\,n$:
>	- **Retrieve indices** corresponding to the column $j$ **in $A.val$**: $$\text{index}_{j} = \{A.c[j] \;{,}\ldots{,}\;  (A.c[j+1]-1)\}$$
>	- For $k\in \text{index}_{j}$:
>		- **Retrieve the row index** from $A.r[k]$  corresponding to $A.val[k]$ as $$s = A.r[k]$$
>		- Aggregate the linear operation result $$y[s] \leftarrow y[s] + A.val[k] \cdot x[j]$$
>		  
>		  
>
>This algorithms requires $2 \cdot\text{nnz}(A)$ flops.

### Outer Product and Rank-1 Update Operation

>[!important] Definition
>Consider the **outer product operation** for **rank-1 update** $$A \leftarrow A + u\,v^{T},$$ where $A\in \mathbb{R}^{m\times n}$, $u\in \mathbb{R}^{m}$ and $v\in \mathbb{R}^{n}.$ 
>- Since more nonzero entries are included, we need to expand *memory allocation* for $A.val$ by *introducing new entries* based on the index $i$ of $u_{i}$ and $j$ of $v_{i}$ such that $$(i,j) \implies u_{i}v_{j} \neq 0,$$
>	- e.g. $$A.val = [a_{11}, a_{41} \;||\; 0, a_{52} \;||\; a_{23}, a_{33}, a_{63} \;||\; a_{14}, 0, a_{44}, 0 \;||\; a_{25}, a_{55}, a_{65}].$$ with $$A.c = [1, 3, 5, 8, 12\;||\; 15]$$ and $$A.r = [1, 4 \;||\; 3, 5 \;||\; 2, 3, 6 \;||\; 1, 3, 4, 5 \;||\; 2, 5, 6]$$ 
>  
>Assuming both $A, u, v$ are in **column-compressed representation**, the **rank-1 outer product** algorithm $$A_{i,j} \leftarrow A_{i,j} + u_{i}v_{j}, \quad \forall (i,j)\text{ if }u_{i}v_{j} \neq 0$$ is describe as follow:
>- For $\beta = 1\,{,}\ldots{,}\,\text{nnz}(v)$:
>	- *Retrieve row index* of nonzero $v$ to determine the *column index* of $A$: $$j = v.r(\beta)$$
>	- *Initialize row index* for $u$: $$\alpha = 1$$
>	- For $l = A.c[j]\,{,}\ldots{,}\,(A.c[j+1] -1)$:
>		- If $\alpha < \text{nnz}(u)$ and $A.r[l] == u.r[l]$:
>			- Update **only when** *row index* in *column* $j$ of $A$ that **matches** *row index* of $u$ $$A.val[l] \leftarrow A.val[l] + u.val[\alpha] \cdot v.val[\beta]$$
>			- Index points to the next value of $u$ to multiply $v_{j}$ $$\alpha \leftarrow \alpha + 1.$$


## Explanation

>[!info]
>The **Gaxpy operation** and **outer product operations** are basic operation behind 
>- [[Elementary Row and Column Operations]]
>- [[Gaussian Elimination for General Linear System]] and [[LU Factorization of Matrix]]
>- [[Householder Transformation and Householder Reflection]] and [[Householder QR Factorization]]


## Challenges to Preserve Sparsity in Matrix Factorization

- [[Sparse Matrix Factorization and Challenges]]



-----------
##  Recommended Notes and References




- [[Adjacency Matrix of Graph]]
- [[Sparse Linear System and Graph]]
- [[Matrix]]
- [[Graph]]

- [[Matrix Computations by Golub]] pp 598 - 600
- [[Numerical Linear Algebra by Trefethen]] pp 232, 244