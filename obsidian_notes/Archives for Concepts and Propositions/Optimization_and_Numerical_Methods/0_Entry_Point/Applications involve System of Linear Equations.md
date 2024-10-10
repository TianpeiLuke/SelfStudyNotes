---
tags:
  - entry_point
  - concept
  - numerical_methods/numerical_linear_algebra
  - numerical_methods/numerical_differential_equations
  - math/matrix_analysis
  - machine_learning/algorithms
  - online_learning/algorithms
  - deep_learning/algorithms
  - optimization/algorithm
keywords: 
topics:
  - numerical_linear_algebra
name: 
date of note: 2024-09-27
---

## Topics

### System of Linear Equations

>[!info]
>The problem of solving **Linear system** or **system of linear equations** refer to the problem $$Ax = b$$ 
>
>For $A\in M_{n}$ and *nonsingular*, the linear system has **unique solution** 
>- it is equivalent to the problem of finding $$x = A^{-1}b$$
>- Note that it is common to transfer the problem of finding $A^{-1}b$ into the solution of linear system $Ax = b$. 


- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Fundamental Subspaces from Linear Map]]
- [[Fundamental Orthogonal Projections]]


>[!info]
>For $A\in M_{n,m}$ with $n < m$, the system $$Ax = b$$ is **undercomplete** or **under-determined**, i.e. it has more *variables* than *equations/constraints*, thus $$\{ 0 \} \subset \text{Ker}(A), \quad \text{dim}\left(\text{Ker}(A)\right) = m -n.$$ The solution form a $m-n$ dimensional  *linear subspace*.

- [[Rank–Nullity Theorem]]

>[!info]
>The general form of *solution* for linear system $$Ax = b$$ is 
>$$x = A^{+}\,b + \left(I - A^{+}\,A\right)\,\epsilon$$ where $\epsilon\in \mathbb{R}^{m}$ is *arbitrary*

- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]

### Linear Least Square Estimation

>[!info]
>If $n >m$, i.e. there are more equations/constraints than variables, the system $$Ax = b$$ is **overcomplete.**
>
>One way to find a solution is via the **minimum norm estimation**
>$$
>\begin{align*}
>\min_{x} &\; \lVert x \rVert_{2}^2 \\[5pt]
>\text{s.t. }& Ax = b
\end{align*}
>$$
>This is equivalent to 
>$$
>\min_{x}\; \lVert Ax - b \rVert_{2}^2 
>$$
>This optimization problem is called the **linear least square estimation** problem.
>- The LSE problem is the MLE of the **linear regression** where it is assumed that the *each response* is the *linear function* of *covariates* $$b_{i} = \left\langle  A_{i,:}\,,\,x    \right\rangle + \epsilon_{i}, \quad i=1\,{,}\ldots{,}\,n$$
>- If $A$ has **full column rank**,  e.g. $n > m$, then the LSE has **unique solution** $$x = A^{+}b= \left(A^{T}\,A\right)^{-1}\,A^{T}b$$
>	- If  $n > m$, the linear system is **overcomplete.**

- [[Least Square Estimation]]
- [[Linear Regression]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Algorithms for Least Square Estimation Problem]]

#### Normal Equation

>[!info]
>If $A$ has **full column rank**, e.g. $n > m$, then the LSE has **unique solution** $$x = A^{+}b= \left(A^{T}\,A\right)^{-1}\,A^{T}b$$ 

- [[Normal Equations and Newton System of Equations]]

#### Gaussian Elimination and Cholesky Factorization

>[!info]
>Solving $x$ is equivalent to finding the solution of **normal equation**
>$$
>A^{T}\,A\,x = A^{T}b \iff S\,x = w
>$$ 
>where $$S := A^{T}\,A \succ 0$$ is a **symmetric positive definite transformation** (since $A$ has full column rank) and $w := A^{T}b$
>- This is a **symmetric positive definite system**
>- We can use **$LDL^{T}$ factorization** $$S = L\,D\,L^{T},$$ which requires $n^3 / 3$ flops. Here $L$ is *unit lower triangular matrix* and $D$ is the *diagonal matrix*.
>	- The solution can be obtained by solving three triangular systems $$L\,z = w, \quad D\,y = z, \quad L^{T}x = y$$
>- Or we can use **Cholesky factorization**  $$S = G\,G^{T},$$ which requires $n^3 / 3$ flops. Here $G$ is a *lower triangular matrix*. 
>	- The solution can be obtained by solving two triangular systems $$G\,y = w, \quad G^{T}\,x = y$$

- [[Normal Equations and Newton System of Equations]]
- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Triangular System of Equations]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]

#### Modified Gram-Schmidt Orthogonalization and QR Factorization

>[!info]
>In case for **undercomplete system** $n < m$
>
>An alternative way is to find the **QR factorization** of $A$ $$A = Q\,R$$ where $Q$ is orthogonal matrix, and $R$ is *upper triangular*.
>
 >Then the solution can be found via solving $$R\,x = Q^{T}b:= y$$
>- This is a *triangular system*
>- A typical iterative method is based on the **modified Gram-Schmidt orthogonalization process**
>- We can also apply **Hourseholder reflection** or **Givens rotations** to compute *QR factorization*.

>[!important]
>**QR factorization** is preferred compared to **Cholesky factorization** of **normal equations**.
>
>-- [[Matrix Computations by Golub]] pp 268


- [[QR Factorization of Matrix]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[Householder QR Factorization]]
- [[Givens QR Factorization]]
- [[Least Square Estimation with QR Factorization]]

- [[Back Substitution of Upper Triangular System]]

#### SVD and Matrix Analysis

>[!info]
>An equivalent way is to find the **Singular Value Decomposition (SVD)** of $A$ $$A = U\,\Sigma\,V^{T}$$ where $U, V$ are orthogonal matrices, and $\Sigma$ is *diagonal*.
>
 >Then the solution can be found as $$x = \sum_{i=1}^{\min\{ n,m \}}\,\frac{\left\langle u_{i} , b \right\rangle }{\sigma_{i}}\,v_{i}$$

- [[Singular Value Decomposition of Linear Map]]
- [[Least Square Estimation via Singular Value Decomposition]]

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [[Schur Complement and Inversion of Block Matrix]]

#### Iterative Method to Solve Large Least Square Problem

>[!info]
>The **iterative methods** can be used to solve the **high dimensional normal equation**

- [[Krylov Subspace Methods]]

- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]
- [[GMRES as Regression on Krylov Space]]


>[!info]
>Since $S = A^{T}A$ is symmetric positive semidefinite, the **conjugate gradient method** can be used.
>- Solving $$A^TAx = A^Tb \iff \min \lVert Ax - b \rVert_{2}^2 $$
>	- compute **step size** $$\alpha_{k} = - \frac{r_{k}^T\,d_{k}}{d_{k}^T\,A\,d_{k}}$$
>	- update solution: $$x_{k+1} = x_{k} + \alpha_{k}\,d_{k}$$
>	- update **residual**: $$r_{k+1} = Ax_{k+1} - b$$
>	-  $$\beta_{k+1} = \frac{r_{k+1}^T\,A\,d_{k}}{d_{k}^T\,A\,d_{k}}$$ 
>	- $$d_{k+1} = - r_{k+1} + \beta_{k+1}\,d_{k}$$

- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Normal Equation Residual and CGNER]]


### Ridge Regression

>[!info]
>The **ridge regression** problem solves
>$$
>\min_{x} \; \lVert Ax - b \rVert_{2}^2 + \lambda\,\lVert x \rVert_{2}^2  
>$$
>This is equivalent to solve a **least square** problem with **augmented design matrix**
>$$
>\min_{x}\; \lVert \widetilde{A}\,x -   \widetilde{b}\rVert^2 
>$$
>where $$\widetilde{A}:= \left[ \begin{array}{c}A\\[5pt] \sqrt{ \lambda}I \end{array} \right]$$ and $$\widetilde{b}:= \left[ \begin{array}{c}b\\[5pt] 0 \end{array} \right]$$

- [[Ridge Regression and L2 Regularization]]

### Logistic Regression

![[Logistic Regression Solution via Iterative Reweighted Least Square#^bd6332]]

![[Logistic Regression Solution via Iterative Reweighted Least Square#^8e7fe7]]

>[!info]
>Using Netwon's method to solve the logistic regression requries solving the equation
>$$
>\nabla^2 \ell(\beta)\, d = - \nabla \ell(\beta)
>$$
>The **iterative reweighted least sequare (IRLS)** need to solve a **weighted least square problem** at each iteration
>- It solve the *weighted normal equation*
>$$
>X^{T}WX\,d = X^{T}(y-p)
>$$
>- or it solves the least square problem $$\min_{d} \lVert \hat{X}d - \hat{b} \rVert_{2}^2$$
>	- $$\hat{X} = W^{1 / 2}X, \quad \hat{b} = W^{1 / 2}z_{t}$$

![[Logistic Regression Solution via Iterative Reweighted Least Square#^3e8b8a]]

- [[Logistic Regression]]
- [[Logistic Regression Solution via Iterative Reweighted Least Square]]


### Gradient-based Optimization

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Gradient Descent Algorithm]]

>[!info]
>In **gradient-based methods**, $$x_{t+1} = x_{t} + \alpha_{k}\,d_{t}$$ where $$\left\langle  d_{t}\,,\,\nabla f(x_{t})    \right\rangle < 0$$

#### Newton Methods and Gradient Descent Direction

>[!info]
>In **Newton's method**, the gradient descent **direction**
>$$
>d_{t} = - \left( \nabla^2 f(x_{t}) \right)^{-1}\,\nabla f(x_{t})
>$$
>Thus the finding the direction $d_{t} = d$ is the *solution of linear system* $$\nabla^2 f(x_{t})\,d =  - \nabla f(x_{t}) \iff H_{t}\,d = - g_{t}$$ where
>-  $H_{t}$ and $g_{t}$ are **Hessian matrix** and **gradient** of $f$ at $x_{t}$ respectively  $$H_{t} := \nabla^2 f(x_{t}), \quad g_{t} := \nabla f(x_{t})$$
>- The linear system $$H_{t}\,d = - g_{t}$$ is a **symmetric positive semidefinite system**

- [[Newton Method]]

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]

#### Quasi-Newton Methods and Secant Equation

>[!info]
>Instead of computing the Hessian $H_{t}:= \nabla^2 f(x_{t})$, we can use the gradient to approximate $H_{t}$. These methods are called the **quasi-Newton methods.**
>
>In particular, for $\Delta_{t}:= x_{t+1} - x_{t}$, then by definition of **Hessian**  $$\lim_{ \lVert \Delta_{t} \rVert \to 0 } \left\langle  H_{t}\,\Delta_{t} \,,\, \Delta_{t} \right\rangle  = \left\langle \nabla f(x_{t}+ \Delta_{t}) - \nabla f(x_{t}) \,,\,\Delta_{t} \right\rangle $$
>Thus the following equation is approximately correct for small $\Delta_{t}$
>$$
>H_{t}\,\Delta_{t} \approx \nabla f(x_{t}+ \Delta_{t}) - \nabla f(x_{t})
>$$
>This system of equations is called the **secant equation**. Let $$y_{t} := \nabla f(x_{t+1}) - \nabla f(x_{t}), \quad s_{t} := x_{t+1} - x_{t}.$$ Then the **secant equation** is $$\hat{B}_{t}\,s_{t} = y_{t}$$
>- Given $\hat{B}_{t}$, we need to solve the following to obtain direction $$\hat{B}_{t}\,d = -g_{t}$$
>- We can also define the **secant equation** using **inverse of Hessian** $$\hat{\Theta}_{t}\,y_{t} = s_{t}$$ where $$\hat{\Theta}_{t} \approx H_{t}^{-1}$$
>	- This way we do not need to further solve the equations in Newton's method
>	- $$d_{t} = - \hat{\Theta}_{t}\,g_{t}$$
>	- This is the equation to solve in the **BFGS method**
>- The **quasi-Newton methods** involve estimating the **symmetric positive definite** matrix $$\begin{align*}\min_{B}&\; \lVert B - B_{t} \rVert_{W}^{2} \\[5pt] \text{s.t. }& B = B^{T} \\[5pt] &\,B\,s_{t} = y_{t}  \end{align*}$$ 
>	- For **BFGS method**, $$\begin{align*}\min_{\Theta}&\; \lVert \Theta - \Theta_{t} \rVert_{W}^{2} \\[5pt] \text{s.t. }& \Theta = \Theta^{T} \\[5pt] &\,\Theta\,y_{t} = s_{t}  \end{align*}$$ 

- [[Covariant Hessian Tensor]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]

#### KKT System and Optimization with Equality Constraint



- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]


### Linear Optimization

- [[Linear Optimization Problem]]

>[!info]
>Two major steps require solving linear systems based on **basis matrix** $B$:
>- Computation of **simplex multipliers** $$p^{T}B = c_{B}^{T}$$
>- Computation of **basic feasible direction**: $$B\,d = -A_{j}$$
>  
>Note that  $$B= [B(1) \,{,}\ldots{,}\, B(m)]\in \mathbb{R}^{m\times m}$$ may be sparse since the columns are basic solutions, which are *vertices of the polytope*.

- [[Basic Solution for Linear Optimization]]


![[Simplex Method for Linear Optimization#^3b2740]]

![[Simplex Method for Linear Optimization#^0e8413]]

- [[Simplex Method for Linear Optimization]]
- [[Simplex Method for Linear Optimization Efficient Implementation]]

>[!info]
>**Interior Point method** involves **Newton's method** for each iteration.

- [[Interior Point Method for Linear Optimization]]

####  Optimal Transport

>[!info]
>Finding the **optimal transport coupling** is a **linear programming problem**.

![[Optimal Transport in Discrete Setting#^ad1beb]]

- [[Optimal Transport in Discrete Setting]]
- [[Entropic Regularized Optimal Transport in Discrete Settings]]
- [[Entropic Regularized Optimal Transport in Dual Form]]

#### Network Flow 

- [[Network Flow Problem as Linear Optimization]]


#### MAP Inference in Graphical Model

>[!info]
>**MAP inference** can be reformulated as **integer programming problem**

- [[Maximum A Posteriori Probability Query of Graphical Model]]
- [[Max-Product Variable Elimination]]
- [[Clique Tree Invariant of Max-Product and Reparameterization]]


### Convex Optimization

- [[Convex Optimization Problem]]
- [[Methods of Lagrangian Multipliers]]
- [[Lagrangian Dual Function]]
- [[Lagrange Dual Problem]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Interior Point Method or Barrier Method for Convex Optimization]]

### Quadratic Programming

![[Quadratic Programming#^387671]]

- [[Quadratic Programming]]
- [[Sequential Quadratic Programming]]
- [[Tridiagonal Reduction of Symmetric Matrix via Householder Transformation]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[GMRES as Regression on Krylov Space]]
- [[Conjugate Gradient Algorithm Linear]]

#### Support Vector Machine

- [[Support Vector Machine Linear Separable Case]]
- [[Support Vector Machine General with Soft-Margin Relaxation]]


### Eigenvalue Problem as Convex Optimization on Manifold

- [[Semidefinite Programming]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]
- [[Convex Optimization for Eigenvalue Problem]]


#### Principle Component Analysis

![[Principle Component Analysis#^028c45]]

![[Principle Component Analysis#^feea32]]

![[Principle Component Analysis#^ab6364]]

- [[Principle Component Analysis]]
- [[Nonnegative Matrix Factorization]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]



### Latent Variable Model and Factor Analysis

![[Factor Analysis#^a9ed6d]]

![[Factor Analysis#^cb4966]]

- [[Latent Variable Models]]
- [[Factor Analysis]]

![[Gaussian Process Latent Variable Model#^6c8c67]]

![[Gaussian Process Latent Variable Model#^cb892f]]

- [[Gaussian Process Latent Variable Model]]

### Dynamic System

>[!info]
>The key for Kalman filter is to solve the **Kalman information gain matrix**
>$$K_{t} = \Sigma_{t|t-1}\,C(t)^{T}\,\left(\Sigma_{t:t-1}^{O}\right)^{-1}$$
>This involves the *linear system* $$(\Sigma_{t:t-1}^{O})^{T}\,K_{t}^{T}\, = (\Sigma_{t}^{O,X})^{T}$$ where $$\Sigma_{t}^{O,X}:= \Sigma_{t|t-1}\,C(t)^{T}$$

- [[Linear Dynamic System]]
- [[Kalman Filter Discrete-Time]]


### Gaussian Graphical Model

>[!info]
>Probability inference on **Gaussian Graphical model (GGM)** using the mean field approximation can be seen as the **Gauss-Seidel iteration** 

- [[Mean Field Approximation for Gaussian Markov Random Field]]
- [[Gauss-Seidel Iteration for Sparse Linear System]]
- [[Gaussian Graphical Model]]
- [[Marginal and Conditional Distribution of Gaussian]]
- [[Canonical Form of Gaussian Graphical Model]]

>[!info]
>**Structure learning** on Gaussian graphical model via **Graph LASSO** can be seen as solving the **sparse linear equations** 

- [[Inverse Covariance Estimation]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]



### Markov Process and Markov Chain

>[!info]
>The **transition kernel matrix** $$K = [p(X_{t+1}=j | X_{t}=i)]_{i,j}$$ is a **nonnegative** and **stochastic matrix**

- [[Nonnegative and Positive Matrix]]
- [[Markov Chain and Markov Process]]
- [[Markov Chain Monte Carlo Methods]]
- [[Markov Transition Kernel and Transition Function]]

- [[Birkhoff Theorem on Characterization of Doubly Stochastic Matrix]]

>[!info]
>The **first left eigenvector** associated with $1$ of $K$ is the **invariant measure** $$\pi^{T}K = \pi^{T}$$

- [[Invariant Measure and Stationary Distribution]]
- [[Kac Theorem on Markov Chain]]
- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]

>[!info]
>We can use many numerical methods to compute the largest eigenvector.

- [[Power Iteration and Inverse Iteration for General Eigenvalue Problem]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]






### Linear ODE and Stochastic Linear ODE

- [[Concepts and Theorems for Differential Equations]]
- [[Concepts and Theorems for Stochastic Differential Equations]]
- [[Theory and Algorithms for Numerical Solution of Differential Equations]]

- [[Exponential Map of Linear Operator]]
- [[Homogeneous Linear Differential Equations]]
- [[Linear ODE with Constant Coefficients]]
- [[Jordan Canonical Form]]




-----------
##  Recommended Notes and References


- [[Theory and Algorithms for Linear Optimization]]
- [[Theory and Algorithms for Convex Optimization]]
- [[Concepts and Theorems in Convex Analysis and Convex Optimization Theory]]
- [[Theory and Algorithms for Nonlinear Optimization]]
- [[Theory and Algorithms for Numerical Linear Algebra]]
- [[Theory and Algorithms for Numerical Solution of Differential Equations]]
- [[Concepts and Theorems in Graph Theory]]
- [[Concepts and Theorems for Stochastic Process]]
- [[Concepts and Theorems for Matrix Theory]]
- [[Concepts and Theorems in Finite Dimensional Vector Space]]
- [[Concepts and Theorems in Tensor Space]]
- [[Concepts and Theorems in Hilbert Space]]