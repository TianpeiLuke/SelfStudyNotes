---
tags:
  - concept
  - math/functional_analysis
keywords:
  - continuous_function_calculus
topics:
  - functional_analysis
name: Continuous Functional Calculus
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Continuous Functional Calculus

>[!important] Theorem
>Let $A$ be a  **self-adjoint**  *operator* on a *Hilbert space* $\mathcal{H}$. 
>
>Then there is a **unique map** $$\phi: \mathcal{C}(\sigma(A)) \to \mathcal{L}(\mathcal{H})$$ with the following properties: 
>
>-  $\phi$ is an **algebraic $*$-homomorphism**, that is,  for any $f, g \in \mathcal{C}(\sigma(A))$, and any $\lambda \in \mathbb{C}$,  
>	- **Preserve Operator Product** $$\phi(fg) = \phi(f)\phi(g)$$
>	- **Preserve Scalar Product** $$\phi(\lambda f) = \lambda \phi(f)$$
>	- **Preserve Identity** $$\phi(1) = I$$
>	- **Preserve Adjoint/Conjugacy** $$\phi(\bar{f}) =  \phi(f)^{*}$$
>
>-  $\phi$ is **continuous**, that is,
>$$
> \begin{align*}
> \lVert \phi(f) \rVert_{\mathcal{L}(\mathcal{H})}  &\le C  \lVert f \rVert_{\infty}.
> \end{align*}
>$$
> 
>- Let $f$ be the function $f(x) = x$; then $$\phi(f) = A.$$
>  
> 
> Moreover,  $\phi$ has the *additional properties*: 
>- If $\psi$ is the **eigenvector** of $A$ associated with **eigenvalue** $\lambda$, $$A\psi = \lambda \psi,$$ then $\psi$ is the **eigenvector** of $\phi(f)$ associated with **eigenvalue** $f(\lambda)$,
>$$  
> \begin{align}
> \phi(f)\psi  = f(\lambda) \psi 
> \end{align}
>$$ 
>
>-  **Spectral Mapping Theorem**
>$$   
> \begin{align}
> \sigma(\phi(f)) &= \left\{ f(\lambda): \lambda \in \sigma(A) \right\}  
> \end{align}
>$$ 
>- **Preserve Positivity**  If $f \ge 0$, then $$\phi(f) \succeq 0.$$ 
>- **Preserve Norm** (This strengthens the (2)).
>$$  
> \begin{align}
> \lVert \phi(f) \rVert_{\mathcal{L}(\mathcal{H})}  &= \lVert f \rVert_{\infty} 
> \end{align}
>$$

^bc47ad


- [[Self-Adjoint Operator in Hilbert Space]]
- [[C-star Algebra]]
- [[Homomorphism between Groups]]
- [[Continuous Function]]
- [[Norm and Normed Space]]
- [[Positive Semidefinite Operator]]
- [[Hilbert Space]]
- [[Involutory and Coninvolutory Transformations]]



## Explanation

>[!important]
>We sometimes write $$f(A) \quad \text{ or } \quad \phi_{A}(f)$$ for $\phi(f)$ to emphasize the dependency on $A$.

>[!info]
>As $f \in \mathcal{C}(\sigma(A)) \subset \mathcal{C}(\mathbb{R})$, the form
>$$
>f(A)
>$$
>cannot be understood by "$f$ taking value of an operator $A$" but as an abbreviation of $\phi(f) \in \mathcal{L}(\mathcal{H})$ for the *continuous star-homomorphism* $\phi$.

## Proof

>[!info]
>Note that for a polynomial $p \in \mathbb{C}[x]$:
>$$
> p_{n}(x) = a_{0} + \sum_{i=1}^{n}a_{i} x^i,
>$$
>we can map it to a linear operator via
>$$
>p_{n}(A) := a_{0}I + \sum_{i=1}^{n}a_{i}A^i.
>$$
>
>For this mapping, the above conditions holds.
>
>For instance, if $\psi$ is an eigenvector of $A$ associated with $\lambda$, then
>$$
>p_{n}(A) \psi = p_{n}(\lambda) \psi
>$$

- [[Polynomial Ring]]


>[!info]
>Then we can use the fact that $p_{n} \to f\in \mathcal{C}(\sigma(A))$ *uniformly* via the classical result of [[Stone-Weierstrass Theorem]], given that $\sigma(A) \subset \mathbb{R}$ is *compact Hausdorff*.

- [[Compact Hausdorff Space]]
- [[Stone-Weierstrass Theorem]]


>[!info]
>It remains to prove
>$$
>\lVert \phi(f) \rVert_{\mathcal{L}(\mathcal{H})}  \le C  \lVert f \rVert_{\infty}.
>$$
>
>This can be shown by [[Bounded Linear Transform Theorem]] as we expand our domain from *the space of polynomial functions* on $\sigma(A)$ to the space of continuous functions on $\sigma(A)$.

- [[Bounded Linear Transform Theorem]]


-----------
##  Recommended Notes and References


- [[Norm and Normed Space]]
- [[Positive Semidefinite Operator]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[star Algebra]]
- [[Homomorphism between Groups]]
- [[Continuous Function]]
- [[Self-Adjoint Operator in Hilbert Space]]
- [[Hilbert Space]]

- [[Matrix Polynomial]]
- [[Matrix Exponential]]

- [[Functional Analysis by Reed]]