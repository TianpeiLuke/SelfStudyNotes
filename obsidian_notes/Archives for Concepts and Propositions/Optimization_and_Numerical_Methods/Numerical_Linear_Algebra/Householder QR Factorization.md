---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - qr_factorization
  - householder_transformation
  - householder_qr
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Householder QR Factorization
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Householder QR Factorization

![[QR Factorization of Matrix#^b07f79]]

![[Householder Transformation and Householder Reflection#^082feb]]

>[!important] Definition
>Consider the **QR factorization** of matrix $A\in M_{m,n}$ where $m \ge n$, $$A = Q\,R.$$
>
>The following **Householder QR algorithm** finds a sequence of *Hourseholder transformations* $H_{1} \,{,}\ldots{,}\,H_{n}$ such that if $$Q = H_{1}\,{}\ldots{}\,H_{n},$$ then $$Q^{T}A = R$$ is **upper triangular**.
>- *Require*: $A\in \mathbb{R}^{m\times n}$ with $m\ge n$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- Call the **subroutine $\text{Householder}(x)$** that return $\beta, v$ where $v$ is the Householder vector
>		- $[\beta^{(j)}, v^{(j)}] = \text{Householder}(A_{\{ j:m \}, j})$
>	- Apply the **Householder transformation** on $A_{\{ j:m , j\}}$ $$A_{\{ j:m \}, \{ j:n \}} = \left(I - \beta^{(j)}\,v^{(j)}\,(v^{(j)})^{T}\right)\,A_{\{ j:m \}, \{ j:n \}}$$
>		- We apply the **rank-1 update** for the lower triangular part $$A_{\{ j:m \}, \{ j:n \}} = A_{\{ j:m \}, \{ j:n \}} - (\beta^{(j)}\,v^{(j)})\,\left((v^{(j)})^{T}\,A_{\{ j:m \}, \{ j:n \}}\right)$$
>		- The result $A_{j,j} = \lVert A_{\{ j:m , j\}} \rVert$
>	- If $j < m$:
>		- $$A_{\{ j+1:m \}, j} = v_{\{ 2:m-j+1 \}}^{(j)}$$
>- *Return*: the **upper triangular matrix** $R$ $$R := [A_{j, \{ j:n \}}]_{j=1}^{n}$$ and the **lower triangular part** $$v^{(j)} = [\underbrace{ 0 \,{,}\ldots{,}\,0 }_{ j-1 }\,,1\,, A_{j+1,j}\,{,}\ldots{,}\,A_{m,j} ],\quad j=1\,{,}\ldots{,}\,n.$$ 
>- *Return*: the $Q$ matrix $$Q= H_{1}\,{}\ldots{}\,H_{n},$$ which is obtained by the **backward accumulation algorithm.**

^7f3184

- [[Householder Transformation and Householder Reflection]]
- [[QR Factorization of Matrix]]
- [[Unitary and Orthogonal Transformation]]

>[!important]
>The **Householder QR** requires $$2n^2\left(m - \frac{n}{3}\right)$$ flops.

### Computing $Q$ by Back Accumulation of Householder Transformations

>[!important] Definition
>Given a list of Householder transformations $H_{k}$, $$H_{k} = I - \beta^{(k)}\,v^{(k)}(v^{(k)})^{T},$$ we compute $$Q = H_{1}\,{}\ldots{}\,H_{n}$$ via the **Backward Accumulation**:
>- $$Q = I_{m}$$ 
>- For $j=n\,{,}\ldots{,}\,1$
>	- $$Q \leftarrow Q_{j}\,Q$$
>	  
>Specifically, the **Backward Accumulation** is described as follow
>- *Require*: the matrix $A$ whose lower triangular parts are non-one part of Householder vectors
>- Initialize $$Q = I_{:, \{ 1:n \}}$$
>- For $j=n\,{,}\ldots{,}\,1$:
>	- Recover **Householder vector** $v$ $$v_{j:m} = \left[ \begin{array}{c} 1 \\ A_{j+1:m, j} \end{array} \right] $$
>	- Recover scalar $\beta$ as $$\beta_{j} = \frac{2}{1+ \lVert A_{\{ j+1 :m\}, j} \rVert_{2}^2 }$$
>	- **Accumulate backwards** $$Q_{\{ j:m \}, \{ j:n \}} \leftarrow Q_{\{ j:m \}, \{ j:n \}} - \left(\beta_{j}\,v_{j:m}\right)\,\left(v_{j:m}^{T}\,Q_{\{ j:m \}, \{ j:n \}}\right)$$

- [[Matrix Computations by Golub]] pp 238

>[!important]
>The **backward accumulations** involves about $$4\left(m^2n - mn^2 + \frac{n^3}{3}\right)$$ flops.


## Explanation

>[!info]
>The **Householder QR** is close to the **Gaussian Elimination (LU)** as both algorithms dig holes (i.e. remove entry to zero) in the lower triangular part of the matrix via elementary transformation.
>- In **Gaussian elimination** i.e. **LU decomposition**, we used the **Gaussian transformation** $$M_{k} = I_{n} - \tau\,e_{k}^{T}$$ by substracting  all lower rows with pivot row using scale via pivots.
>	- $$M_{k}\,v = \left[ \begin{array}{cccccc}1 & \cdots & 0 & 0 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots &  & \vdots \\ 0 & \cdots & 1 & 0 & \cdots & 0 \\ 0 & \cdots & -\tau_{k+1}^{(k)} & 1 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ 0 & \cdots & -\tau_{n}^{(k)} & 0 & \cdots & 1 \end{array} \right]\;\left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ v_{k+1} \\ \vdots \\ v_{n}\end{array} \right] =  \left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ 0 \\ \vdots \\ 0\end{array} \right]$$ 
>- In **Householder QR**, we used the **Householder transformation** $$H_{k}  = I- \beta_{k}\,v_{k}\,v_{k}^{T}$$ by reflecting along the $\text{span}(v)$
>	- If we set $$v = x  - \lVert x \rVert_{2}\,e_{1} \implies v_{1} = x_{1} - \lVert x \rVert_{2},$$ the **Householder transformation** on $v$ gives $$H_{k}\,x =  \lVert x \rVert_{2}\,e_{1} = \left[ \begin{array}{c} \lVert x \rVert_{2} \\ 0 \\ \vdots \\  0 \\ \vdots \\ 0\end{array} \right].$$
>	- Let $x = A_{\{ j:m \}, j}$ $$H_{k}A_{\{ j:m \}, j} = \lVert A_{\{ j:m \}, j} \rVert\, e_{1} $$ which set all entries $A_{\{ j+1:m \},j} = 0$ and $A_{j,j} = \lVert A_{\{ j:m \}, j} \rVert.$

- [[Householder Transformation and Householder Reflection]]
- [[Gaussian Elimination for General Linear System]]
- [[Elementary Row and Column Operations]]



-----------
##  Recommended Notes and References

- [[Householder Transformation and Householder Reflection]]

- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]


- [[Elementary Row and Column Operations]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 238, 248 - 250