---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - householder_transformation
  - householder_reflection
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Householder Transformation and Householder Reflection
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Householder Transformation and Householder Reflection

![[Elementary Row and Column Operations#^92e828]]

>[!important] Definition
>Let $v\in \mathbb{R}^{n}$ be nonzero. 
>
>Then the **Householder reflection** or **Householder transformation** or **Householder matrix**  $P_{v}\in \mathbb{R}^{m\times m}$ is of the form $$P_{v} = I_{n} - \beta\,v\,v^{T}$$ where $$\beta = 2\,\left( v^{T}v \right)^{-1}.$$
>- The vector $v$ is called the **Householder vector.**
>- $P_{v}x$ is a **reflection** of $x$ in $\text{R}(v)^{\perp}.$ 

- [[Elementary Row and Column Operations]]
- [[Fundamental Orthogonal Projections]]
- [[Orthogonal Complement of Hilbert Spaces]]

>[!important] Proposition
>Let $v\in \mathbb{R}^{n}$ be nonzero. The **Householder reflection** is $$P_{v} = I_{n} - 2\left( v^T v\right)^{-1}\,v\,v^{T}.$$
>
>Then
>- $P_{v}$ is **symmetric** $$P_{v} = P_{v}^{T}.$$
>- $P_{v}$ is **orthogonal** $$P_{v}^{T}\,P_{v} = P_{v}\,P_{v}^{T} = I.$$


- [[Unitary and Orthogonal Transformation]]
- [[Hermitian or Symmetric Matrix]]


>[!info]
>Let $v\in \mathbb{R}^{n}$ be nonzero. The **Householder reflection** is $$P_{v} = I_{n} - 2v\,v^{+}$$ where the **Moore-Penrose Pseudoinverse** of $v$ is $$v^{+} = \left( v^{T}\,v \right)^{-1}\, v^{T}$$

- [[Moore–Penrose Pseudo Inverse of Matrix]]

### Computing Householder Vector 

>[!info]
>If we set $$v = x  - \lVert x \rVert_{2}\,e_{1} \implies v_{1} = x_{1} - \lVert x \rVert_{2},$$ the **Householder transformation** on $v$ gives 
>$$
>P_{v}\,x =  \lVert x \rVert_{2}\,e_{1}. 
>$$


>[!important] Definition
>Consider the task to compute $v = [v_{1}\,{,}\ldots{,}\,v_{n}]\in \mathbb{R}^{n}$ with $v_{1} = 1$, and $\beta\in \mathbb{R}$ such that
>-  the *Householder transformation* is *orthogonal* $$P_{v} := I - 2 \beta\, v\,v^{T} \in \mathcal{O}(n).$$ 
>- And $$P_{v}\,x = \lVert x \rVert_{2}\, e_{1}.$$ 
>  
>The procedure **$\text{Householder}(x)$** computes $(v,\beta)$ as follow:
>- *Require*: $0 \neq x\in \mathbb{R}^{n}$
>- $$\sigma = \left\langle x_{2:n} , x_{2:n} \right\rangle$$
>- Initialize $$v = \left[ \begin{array}{c}1 \\ x_{2:n}\end{array} \right] $$
>- If $\sigma = 0$ and $x_{1} \ge 0$:
>	-  $\beta = 0$
>- Elif  $\sigma = 0$ and $x_{1} < 0$:
>	-  $\beta = -2$
>- Else:
>	- Compute $\lVert x \rVert_{2}$ as $$\mu = \sqrt{ x_{1}^2 + \sigma }$$
>	- If $x_{1} \leq 0$:
>		- $$v_{1} = x_{1} - \mu$$
>	- Else:
>		- $$v_{1} = - \frac{\sigma}{x_{1} + \mu}$$
>	- The **scalar multiplier** $$\beta = 2 \frac{v_{1}^2}{v_{1}^2 + \sigma}$$
>	- Adjust **Householder vector** so that $v_{1} =1$. $$v \leftarrow \frac{v}{v_{1}}$$
>- *Return* $(\beta, v)$

^082feb

- [[Unitary and Orthogonal Transformation]]
- [[Orthogonal Group]]
- [[Matrix Computations by Golub]] pp 236

>[!info]
>The branch conditions reflect the concerns if $$x\approx \lambda e_{1}$$ then $$v = x_{1} - \lVert x \rVert e_{1}$$ would cause severe **cancellation effect**. 
>
>Note that $$v_1 = x_{1} - \lVert x \rVert  = \frac{-\left( \lVert x \rVert^2 - x_{1}^2  \right) }{x_{1} + \lVert x \rVert }$$

>[!important]
>The algorithm $\text{Householder}(x)$ involves about $$3n$$ flops.


## Explanation


>[!info]
>The **Moore-Penrose Pseudoinverse** of $v$ is $$v^{+} = \left( v^{T}\,v \right)^{-1}\, v^{T}$$
>
>Then the **projection matrix** on $\text{R}(v)^{\perp}$ is $$P_{\text{R}(v)^{\perp}} = I - v\,v^{+} = I - \left( v^{T}\,v \right)^{-1}\,v\,v^{T}$$
>
>The **Householder transformation** is a **reflection** on $\text{R}(v)^{\perp}$ $$P_{householder} = I - 2v\,v^{+}$$

- [[Fundamental Orthogonal Projections]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Projection Map onto Linear Subspace]]

>[!info]
>Similar to the **Gaussian transformation** in Gaussian elimination $$M_{k} = I_{n} - \tau\,e_{k},$$ the **Householder transformation** $$P_{v} = I - 2\,v\,v^{+}$$ is a **rank-1 update** of $I$.

- [[Gaussian Elimination for Solving Linear System]]

>[!info]
>For nonzero $x\neq 0$, applying Householder reflection $$P_{v}x = x - 2 \frac{\left\langle v , x \right\rangle}{\left\langle v , v \right\rangle}\,v$$
>We can choose $v \in \text{span}\left\{ e_{1}, x \right\}$ so that $$P_{v}x = \alpha\,e_{1}$$ for any nonzero $x$ and some $\alpha\in  \mathbb{R}$.
>
>
>In particular, let $$v = x + \lambda\, e_{1}$$ 
>
>Then 
>$$\begin{align*} 
>\left\langle v , x \right\rangle &= \left\langle x , x \right\rangle + \lambda \left\langle e_{1} , x \right\rangle \\[5pt] 
>&= \left\langle x , x \right\rangle + \lambda x_{1}  \\[5pt]  
>&= \lVert x \rVert_{2}^2  + \lambda x_{1}  \\[5pt]  
>\left\langle v , v \right\rangle &= \left\langle x , x \right\rangle + 2\lambda \left\langle e_{1} , x \right\rangle +  \lambda^2 \left\langle e_{1} , e_{1} \right\rangle\\[5pt] 
>&=  \lVert x \rVert_{2}^2 + 2\lambda x_{1} + \lambda^2
>\end{align*}
>$$
>So
>$$
>\begin{align*} 
>Px &= \left( 1 - 2 \frac{ \lVert x \rVert_{2}^2  + \lambda x_{1} }{\lVert x \rVert_{2}^2 + 2\lambda x_{1} + \lambda^2} \right)x\,- 2 \frac{\left\langle v , x \right\rangle}{\left\langle v , v \right\rangle}\,\lambda\,e_{1} \\[5pt]
>&= \left( \frac{ \lambda^2  - \lVert x \rVert_{2}^2  }{\lVert x \rVert_{2}^2 + 2\lambda x_{1} + \lambda^2} \right)x\,- 2\lambda \left(  \frac{ \lVert x \rVert_{2}^2  + \lambda x_{1} }{\lVert x \rVert_{2}^2 + 2\lambda x_{1} + \lambda^2} \right)\,e_{1}\\[5pt]
>&= \alpha\,e_{1}
>\end{align*}
>$$
>This means that
>$$
>\lambda^2  = \lVert x \rVert_{2}^2, \quad \alpha = -\lambda
>$$

>[!important]
>Thus when we set $$v = x  \pm \lVert x \rVert_{2}\,e_{1},$$ the **Householder transformation** on $v$ gives 
>$$
>P_{v}\,x = \mp \lVert x \rVert_{2}\,e_{1}. 
>$$
>
>It is this simple determination of $v$ that makes the Householder reflections so **useful**.

>[!quote]
>The **Householder transformation** are exceedingly useful for **introducing zeros** on a grand scale, e.g., the annihilation of **all but the first component** of a vector.
>
>-- [[Matrix Computations by Golub]] pp 239


>[!info]
>Then $$\beta = 2(v^Tv)^{-1} = 2\,\left( \lVert x \rVert_{2}^2 + 2\lambda x_{1} + \lambda^2 \right)^{-1} = 2(2\lVert x \rVert_{2}^2 - 2\lVert x \rVert_{2} x_{1}  )^{-1}$$
>See that $$\left(   \lVert x \rVert_{2} - x_{1} \right)^2 + \lVert x \rVert_{2}^2  - x_{1}^2 = 2\lVert x \rVert_{2}^2 - 2 \lVert x \rVert_{2} x_{1}$$
>Let $v_{1} = 1 = x_{1} - \lVert x \rVert_{2}$
>$$
>\beta = 2 \frac{1}{2\left(\lVert x \rVert_{2}^2 - \lVert x \rVert_{2} x_{1}  \right)} = 2 \frac{1}{v_{1}^2 + \left( \lVert x \rVert^2  - x_{1}^2 \right)}
>$$

## Householder Transformation on Matrix

>[!important]
>Note that $$P_{v}A = (I -\beta v\,v^{T})A = A - (\beta\,v)(v^T\,A)$$ involves a **matrix-vector product** $$w^{T} = v^{T}\,A$$ and a **rank-1 update** $$P_{v}A = A - (\beta\,v)\,w^{T}.$$ This process requires **$4mn$ flops**. 
>
>Similarly, $$AP_{v} = A(I -\beta v\,v^{T}) = A - (\beta\,Av)v^T$$ which also requires **$4mn$ flops**. 
>
>- We never need to compute the *matrix-matrix product* $P_{v}A$ directly.
>- Householder updates *never entail the explicit formation* of the Householder matrix.

## QR Factorization

- [[QR Factorization of Matrix]]





-----------
##  Recommended Notes and References

- [[Givens Transformation and Givens Rotation]]

- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[Householder QR Factorization]]
- [[QR Factorization of Matrix]]
- [[Singular Value Decomposition of Linear Map]]

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]


- [[Elementary Row and Column Operations]]
- [[Matrix]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 234 - 239