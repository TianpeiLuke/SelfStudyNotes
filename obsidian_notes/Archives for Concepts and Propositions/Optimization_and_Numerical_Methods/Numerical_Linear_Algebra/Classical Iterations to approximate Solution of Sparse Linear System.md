---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - linear_system
  - classical_iteration_linear_system
topics:
  - numerical_linear_algebra
name: Classical Iterations to approximate Linear System Solution
date of note: 2024-09-29
---

## Concept Definition

>[!important]
>**Name**: Classical Iterations to approximate Linear System Solution

>[!important] Definition
>The **classical iteration** methods for $$Ax = b$$ problem generate a *sequence of approximate solutoins* $\{ x^{(k)} \}$ that converges to $A^{-1}b$ $$x^{(k)} \to x = A^{-1}b.$$
>- Typically, the matrix $A$ is involved only in the context of **matrix-vector multiplication** and that is what makes this framework  attractive when $A$ is **large** and **sparse**.

^39280e


## Explanation

>[!quote]
>The importance of **iterative algorithms** in *linear algebra* stems from a simple fact: **noniterative or "direct" algorithms require $O(m^3)$ work**. This is too much! It is too much both in the absolute sense that $m^3$ is huge when $m$ is large, and in the relative sense that since the input to most matrix problems involves only $0(m^2)$ numbers, it seems unreasonable that $0(m^3)$ work must be expended in solving them.
>
>...
>
>To put it another way, if matrix problems could be solved in $O(m^2)$ instead of $O(m^3)$ operations, some of the matrices being treated today might be $10$ to $100$ times larger. This is the **aim**, achieved for *some matrices but not others*, of **matrix iterative methods**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 243

### Structure, Sparsity and Black Boxes

>[!quote]
>Of course, it is not at all obvious that the $O(m^3)$ bottleneck can be beaten, and indeed, for *"random" matrix problems*, very likely it cannot. However, the **large matrix problems** that arise in practice are far from random, and there is a simple reason for this. *Small matrices*, say with dimension 3 or 30, may *arise directly* with more or less arbitrary entries in scientific problems—as representations of the relations between three forces in a structure, perhaps, or between thirty species in a chemical reaction. **Large matrices, by contrast, usually arise indirectly in the discretization of differential or integral equations**. One might say that if $m$ is very large, it is probably *an approximation to* $\infty$. It follows that most large matrices of computational interest are **simpler** than their *vast numbers of individual entries* might suggest. They have some kind of structure, and as the years have gone by, ways have been found to exploit this structure in more and more contexts.
>
>The most obvious structure that a large matrix may have is **sparsity**, i.e., preponderance of zero entries. (The opposite of sparse is dense.) For example, a *finite difference discretization* of a *partial differential equation* ... This kind of structure is readily exploited by the **iterative methods** we shall discuss
>...
>
>The *iterative algorithm* requires nothing more than the **ability to determine $Ax$ for any $x$**, which in a computer program will be effected by a procedure whose internal workings need be of no concern to the designer of the iterative algorithm. For the example of a *sparse matrix* $A$, it is easy to design a procedure to compute $Ax$ in only $O(\nu m)$ rather than $O(m^2)$ operations. This is in marked contrast to the algorithms of direct linear algebra, such as *Gaussian or Householder triangularization*, which explicitly manipulate matrix entries so as to *introduce zeros*, but in the process generally **destroy sparsity**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 244


### Projection into Krylov Space

>[!quote]
>The iterative methods that occupy the remainder of this book are based on the idea of **projecting** an $m$-dimensional problem into a **lower-dimensional Krylov subspace**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 245

- [[Krylov Subspace and Krylov Matrix]]



### Number of Steps, Work per Step

>[!quote]
>**Gaussian elimination**, **QR factorization**, and most other algorithms of dense linear algebra fit the following pattern: **there are $O(m)$ steps**, **each requiring $O(m^2)$ work**, for a total work estimate of $O(m^3)$. (Of course these figures, especially the second, may change on a parallel computer.) For iterative methods, the same figures still apply, but now they represent a typical worst-case behavior. When these methods succeed, they may do so by reducing one or both of these factors.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 246

>[!quote]
>We shall see that the number of steps required for **convergence** to a satisfactory precision typically depends on **spectral properties** of the matrix $A$, if the word "spectral" is interpreted broadly.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 246

>[!quote]
>The *ideal iterative method* in linear algebra reduces the number of steps from $m$ to $O(1)$ and the work per step from $O(m^2)$ to $O(m)$, reducing the total work from $O(m^3)$ to $O(m)$. Such extraordinary speedups do occur in practical problems, but a more **typical improvement** is perhaps from $O(m^3)$ to $O(m^2)$.

### Exact vs. Approximate Solutions

>[!quote]
>Matrix iterative methods are **approximate** in the sense that in principle they do not deliver exact answers, even in the absence of *rounding errors*, at least when carried to the number of iterative steps that is of practical interest. ... After all, *even **direct methods** are inexact* when carried out on a computer: one hopes for answers accurate to machine precision, no better. Since **iterative methods** too may be used to achieve the full accuracy of machine precision, the fact that they are in principle approximate need have little significance.


![[iterative_method_linear_algebra.png]]




## Summary of Iterative Algorithms

- [[Krylov Subspace and Krylov Matrix]]

|                   | $Ax = b$ **linear system problem**  |    $Ax = \lambda x$ **eigenvalue problem**    |
| ---------------   | ------------------------------------ | --------------------------------------------- |
| $A = A^{*}$ **Hermitian** |  **Conjugate Gradient (CG)**  |  **Lanczos Iteration** |
| $A \neq A^{*}$ **Non-Hermitian** | **GMRES**, **CGN**, **BCG** | **Arnoldi Iteration** |

- [[Conjugate Gradient Algorithm Linear]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[Conjugate Gradient Normal Equation Residual and CGNR]]


## Iterative Algorithms to Solve Linear Equations

- [[Gauss-Seidel Iteration for Sparse Linear System]]
- [[Jacobi Iteration for Sparse Linear System]]

### Symmetric

- [[Conjugate Gradient Algorithm Linear]]


### Non Symmetric

- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Conjugate Gradient Normal Equation Residual and CGNR]]



## Iterative Algorithms to Solve Eigenvalue Problem

- [[Lanczos Iteration Practical with Reorthogonalization]]
- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]



-----------
##  Recommended Notes and References


- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Matrix Analysis by Horn]]
- [[Numerical Linear Algebra by Trefethen]]
- [[Matrix Computations by Golub]] pp 611