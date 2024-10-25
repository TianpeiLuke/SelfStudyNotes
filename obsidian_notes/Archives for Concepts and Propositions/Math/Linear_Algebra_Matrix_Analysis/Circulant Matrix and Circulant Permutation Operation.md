---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - circulant_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Circulant Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Circulant Matrix and Circulant Permutation Operation

>[!important] Definition
>Let $$a := (a_{0} \,{,}\ldots{,}\,a_{n-1})$$ be a sequence of length $n$. 
>
>A **circulant matrix** $A\in M_{n}$ of **size** $n$ is of the form
>$$
>A = \left[ \begin{array}{cccc}a_{0} & a_{1} & \cdots & a_{n-1} \\ a_{n-1} & a_{0} & \cdots & a_{n-2} \\ \vdots & \vdots & \ddots & \vdots \\ a_{1} & a_{2} & \cdots & a_{0} \\ \end{array} \right] 
>$$
>where each row is the previous row *cycled forward one step*.
>- The entries in each row are a **cyclic permutation** of those in the first.

- [[Permutation Matrix and Reversal Matrix]]

>[!important] Definition
>A **basic circulant permutation matrix** $C_{n}\in M_{n}$ is of the form
>$$
>C_{n} = \left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] = \left[ \begin{array}{cc}0 & I_{n-1} \\[5pt] 1 & 0 \end{array} \right] 
>$$

- [[Permutation Matrix and Reversal Matrix]]

## Explanation

>[!important] Proposition
>A matrix $A\in M_{n}$ can be written in the form of *matrix polynomial*
>$$
>A = \sum_{k=0}^{n-1}a_{k}\,C_{n}^{k}
>$$
>where  $C_{n}\in M_{n}$ is **basic circulant permutation matrix** *if and only if* $A$ is a **circulant matrix**.

- [[Matrix Polynomial]]

>[!info]
>This representation reveals that the circulant matrices of size $n$ are a **commutative algebra**: 
>- *linear combinations* and *products* of circulants are circulants; 
>- the *inverse* of a nonsingular circulant is a circulant; 
>- any two circulants of the same size *commute*.

- [[Commutative Ring Algebra]]

>[!info]
>We use $0$ index as the starting one, instead of $1$.

### Toeplitz Matrix

>[!info]
>A **circulant matrix** is a **Toeplitz matrix** associated with a *periodic sequence* $$a = (a_{0}\,{,}\ldots{,}\,a_{n-1},\,a_{0}\,{,}\ldots{,}\,)$$

- [[Toeplitz Matrix and Backward Forward Shift Operation]]



## Cyclic Convolution

>[!important] 
>Let $$a := (a_{0} \,{,}\ldots{,}\,a_{n-1})$$ be a sequence of length $n$ and $A\in M_{n}$ be the **circulant matrix**  of **size** $n$ 
>$$
>A = \left[ \begin{array}{cccc}a_{0} & a_{1} & \cdots & a_{n-1} \\ a_{n-1} & a_{0} & \cdots & a_{n-2} \\ \vdots & \vdots & \ddots & \vdots \\ a_{1} & a_{2} & \cdots & a_{0} \\ \end{array} \right] 
>$$ 
>
>Then for $x= (x_{0}\,{,}\ldots{,}\,x_{n-1})$, and $y=(y_{0}\,{,}\ldots{,}\,y_{n-1})$, the **circulant linear system** 
>$$
>Ax = y
>$$
>corresponds to the **cyclic convolution** or **periodic convolution**
>$$
>y = a * x \; \implies \;  y_{i} = \sum_{k=0}^{n-1}a_{i - k}\,x_{k}, \quad i=0\,{,}\ldots{,}\,n-1
>$$

- [[Convolution Operation]]
- [[Discrete Time Signal Processing by Oppenheim]] PP 631

## Spectrum, Eigenvectors and Discrete Fourier Transform

>[!important] Theorem
>Let $C_{n}$ be a **basic circulant permuation matrix** i.e.
>$$
>C_{n} = \left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] = \left[ \begin{array}{cc}0 & I_{n-1} \\[5pt] 1 & 0 \end{array} \right] 
>$$
>
>Then 
>- $C_{n}$ is **unitary** (or **real orthogonal**)
>- Let $$D = \text{diag}\left(1,\, \omega_{n} \,{,}\ldots{,}\,\omega_{n}^{n-1}\right)$$ where $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$ and let $F_{n}$ be the **DFT matrix**.  $$\begin{align*} F_{n} &= \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]  &=  \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n} \\[5pt] \end{array} \right]\end{align*}$$ Then $$C_{n}F_{n} = F_{n}D$$ That is, the **spectral decomposition** of $C_{n}$ is given by $$C_{n} = F_{n}\,D\,F_{n}^{*}$$ where
>	- the **eigenvalues** of $C_{n}$ consists of all **$n$-th root of unit** (i.e. $\omega_{n}^n=1$) $$1,\, \omega_{n} \,{,}\ldots{,}\,\omega_{n}^{n-1}$$ and $$\sum_{k=0}^{n-1}\omega_{n}^{k} = 0$$
>	- and the **eigenvector** of $C_{n}$ corresponds to **eigenvalue** $\omega_{n}^{k}$ is **the $k$-th Fourier modes** $$v_{k} := \frac{1}{\sqrt{ n}}\left[ 1,\,\omega_{n}^{k}\,{,}\ldots{,}\,\omega_{n}^{k(n-1)} \right]^{T}$$


^174342

- [[Unitary and Orthogonal Transformation]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Fourier Series and Fourier Transform]]
- [[Discrete Fourier Transform]]
- [[Polynomial Ring]]

>[!info] Proof
>See that
>$$
>\begin{align*}
>\left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] \left[ \begin{array}{c}x_{1} \\ x_{2} \\ \vdots \\ x_{n-1} \\ x_{n}\end{array} \right] &= \left[ \begin{array}{c}x_{2} \\ x_{3} \\ \vdots \\ x_{n} \\ x_{1}\end{array} \right]
>\end{align*}
>$$
>Thus
>$$
>\begin{align*}
>\left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] \left[ \begin{array}{c}1 \\ \omega_{n}^{k} \\ \vdots \\ \omega_{n}^{k(n-2)} \\ \omega_{n}^{k(n-1)} \end{array} \right] &= \left[ \begin{array}{c}\omega_{n}^{k}  \\ \omega_{n}^{2k}  \\ \vdots \\ \omega_{n}^{k(n-1)} \\ 1\end{array} \right] = \omega_{n}^{k}\left[ \begin{array}{c}1 \\ \omega_{n}^{k} \\ \vdots \\ \omega_{n}^{k(n-2)} \\ \omega_{n}^{k(n-1)} \end{array} \right]
>\end{align*}
>$$
>Therefore $v_{k} := \frac{1}{\sqrt{ n}}\left[ 1,\,\omega_{n}^{k}\,{,}\ldots{,}\,\omega_{n}^{k(n-1)} \right]^{T}$ is the eigenvector of $C_{n}$ associated with $\omega_{n}^{k}$, i.e. $$C_{n}v_{k} = \omega_{n}^{k}\,v_{k}.$$

>[!important]
>Use the projection formula for spectral theorem
>$$
>C_{n} = \sum_{k=0}^{n-1}\,\omega_{n}^{k}\,v_{k}\,v_{k}^{*}
>$$


>[!important] Corollary
>Let $$a := (a_{0} \,{,}\ldots{,}\,a_{n-1})$$ be a sequence of length $n$ and a **circulant matrix** $A\in M_{n}$ of **size** $n$ is of the form
>$$
>A = \left[ \begin{array}{cccc}a_{0} & a_{1} & \cdots & a_{n-1} \\ a_{n-1} & a_{0} & \cdots & a_{n-2} \\ \vdots & \vdots & \ddots & \vdots \\ a_{1} & a_{2} & \cdots & a_{0} \\ \end{array} \right] = \sum_{k=0}^{n-1}a_{k}C_{n}^{k}. 
>$$
>
>Then the **spectral decomposition** of $A$ is given by $$A = F_{n}\,\Lambda\,F_{n}^{*}$$ where 
>- $F_{n}$ be the **DFT matrix**.  $$\begin{align*} F_{n} &= \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]  &=  \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n} \\[5pt] \end{array} \right]\end{align*}$$ 
>- And the **spectrum** of $A$, $\Lambda = \text{diag}(\lambda_{0}\,{,}\ldots{,}\,\lambda_{n-1})$, is given by the **Fourier transform** of $a$, $$\lambda_{j} = \sum_{k=0}^{n-1}\,a_{k}\,\omega_{n}^{kj}:= (\mathcal{F}a)_{j},\quad j=0\,{,}\ldots{,}\,n-1$$ with $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$
>- Or equivalently $$(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})^{T} = \sqrt{n} \,F_{n}^{*}a$$
>- Moreover, **all circulant matrices** shared the **same eigenvectors**, and they are **simultaneously unitary diagonalizable.**

^a24c39

- [[Discrete Fourier Transform]]
- [[DFT Matrix]]
- [[Unitary Similarity and Unitary Diagonalizable]]

>[!important] 
>The **(operator) spectrum** of **circulant matrix** $C(a)$ for a *periodic sequence* $a$ is also the **(Fourier) spectrum** of the **periodic sequence.**
>$$\lambda(C(a)) = \mathcal{F}(a)$$

>[!info]
>These two above theorems work for both $$\omega_{n} := \exp \left(-i \frac{2\pi}{n}\right)$$ and $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$
>
>In fact, it works for all $\omega_{n}$ so that $$\omega_{n}^{n} = 1$$

>[!info]
>This can be understood by realizing that **multiplication** with a *circulant matrix* implements a **cyclic convolution**. 
>- In **Fourier space**, **convolutions become multiplication**. 
>- Hence the *product of a circulant matrix with a Fourier mode* yields a *multiple of that Fourier mode*, i.e. it is an **eigenvector**. 
>  
>See this via eigen-decomposition  
>$$
>\begin{align*}
>  a*x&= y \\[5pt]
> \iff Ax &= y\\[5pt]
> \implies F_{n}\,\text{diag}(\sqrt{n}\,F_{n}^{*}a)\,F_{n}^{*}x &= y \\[5pt] 
> \implies \text{diag}(\sqrt{n}\,F_{n}^{*}a)\,\sqrt{n}\,F_{n}^{*}x &= \sqrt{n}\,F_{n}^{*}\,y\\[5pt] 
> \implies \mathcal{F}(a)\,\mathcal{F}(x) &= \mathcal{F}\left(a*x\right)
\end{align*}
>$$

- [[Convolution Operation]]

>[!info]
>Due to **fast Fourier transform**, solving the **eigenvalue problem** of **circulant matrix**
> $$
> A\,F_{n} = F_{n}\,\Lambda
> $$
>requires only $$O(n\log(n)) \quad \text{ v.s. traditional } O(n^3)$$

- [[Fast Fourier Transform]]
- [[QR Iteration for General Eigenvalue Problem]]


## Determinant

>[!important]
>The **determinant** of **circulant matrix**
>$$
>A = \left[ \begin{array}{cccc}a_{0} & a_{1} & \cdots & a_{n-1} \\ a_{n-1} & a_{0} & \cdots & a_{n-2} \\ \vdots & \vdots & \ddots & \vdots \\ a_{1} & a_{2} & \cdots & a_{0} \\ \end{array} \right]. 
>$$
>is given by
>$$
>\det(A) = \prod_{j=0}^{n-1}\lambda_{j}  = \prod_{j=0}^{n-1}(\mathcal{F} a)_{j-1} = \prod_{j=0}^{n-1}\left(\sum_{k=0}^{n-1}\,a_{k}\,\omega_{n}^{kj}\right)
>$$
>with $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$


- [[Determinant of Linear Transformation]]

## Matrix Polynomial

- [[Matrix Polynomial]]
- [[Continuous Functional Calculus]]
- [[Matrix Exponential]]


## Circulant Graph

- [[Cycles in Graph]]


-----------
##  Recommended Notes and References


- [[Toeplitz Matrix and Backward Forward Shift Operation]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Discrete Fourier Transform]]
- [[Matrix]]
- [[Symmetric Group]]



- [[Numerical Linear Algebra by Trefethen]] pp 187, 305, 318, 342
- [[Matrix Computations by Golub]] pp 220
- [[Matrix Analysis by Horn]] pp 33 - 34, 100, 36
- Wikipedia [Circulant_matrix](https://en.wikipedia.org/wiki/Circulant_matrix)
- Youtube OpenCourse [31. Eigenvectors of Circulant Matrices: Fourier Matrix](https://www.youtube.com/watch?v=1pFv7e9xtHo)