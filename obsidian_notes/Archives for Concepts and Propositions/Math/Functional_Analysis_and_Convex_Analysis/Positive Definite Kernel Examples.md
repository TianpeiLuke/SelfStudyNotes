---
tags:
  - concept
  - machine_learning/kernel_methods
  - math/functional_analysis
keywords: 
topics:
  - kernel_methods
  - functional_analysis
name: Positive Definite Kernel Examples
date of note: 2024-11-12
---

## Concept Definition

>[!important]
>**Name**: Positive Definite Kernel Examples

![[Positive Definite Kernel#^4f8970]]

![[Positive Definite Kernel#^f55e18]]

- [[Positive Definite Kernel]]

### Dirac Kernel

>[!example]
>The **Dirac kernel** is defined as
>$$
>  \begin{align}
> K(x, x') &= \delta \left( x - x' \right) = \left\{\begin{array}{cc}1 &\text{ if } x = x' \\[5pt] 0 &\text{ otherwise}\end{array}\right.
> \end{align}
>$$  
>where $\delta(x)$ is the delta function.

- [[Delta Function]]
- [[Dirac Measure]]
- [[Evaluation Functional]]
- [[Characteristic Function of Set]]


### Linear Kernel

>[!example]
>The **linear kernel** is defined as
>$$
>  \begin{align}
> K(x, x') &= \left\langle x , x' \right\rangle
> \end{align}
>$$  


### Polynomial Kernel

>[!example]
>The **homogeneous polynomial kernel** is defined as
>$$
>  \begin{align}
> K(x, x') &= \left( \left\langle x , x' \right\rangle \right)^{d}, \quad d>0 
> \end{align}
>$$  
>
>The **inhomogeneous polynomial kernel** is defined as
>$$
>  \begin{align}
> K(x, x') &= \left( \left\langle x , x' \right\rangle + c \right)^{d}, \quad d>0 
> \end{align}
>$$ 

- [[Polynomial Ring]]
- Wikipedia [Polynomial_kernel](https://en.wikipedia.org/wiki/Polynomial_kernel)
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 89 - 90

### Gaussian Kernel or Radial Basis Function 

>[!example]
>The **Radial basis function** (**RBF**) **kernel** are kernels that can be written in the form
>$$
> \begin{align}
> K(x, x') &= f\left( d(x ,x') \right), \; x,x'\in \mathcal{X}
> \end{align}
>$$  
>where
>-  $d(x, x')$ is a metric on $\mathcal{X}$ and
>- $f: [0,\infty) \to \mathbb{R}$ is called a **radial function.**
>- The RBF kernels are **unitary invariant**  $$K(Ux, Ux') = K(x, x');$$
>- and **translation invariant** $$K(x- a, x'-a) = K(x, x')$$
>  
>The **Gaussian kernel** or **Gaussian RBF kernel** is defined as 
>$$
> \begin{align}
> K_{\sigma}(x, x') &= \exp\left( - \frac{\lVert x - x' \rVert^2 }{2\sigma^2} \right)
> \end{align}
>$$
>- The parameter $\sigma >0$ is the **bandwidth.**

- [[Gaussian Measure]]
- [[Gaussian Random Vector]]
- Wikipedia [Radial_basis_function_kernel](https://en.wikipedia.org/wiki/Radial_basis_function_kernel)
- [[Unitary Group]]
- [[Isometry and Isometric isomorphism]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 83 - 84

### Laplacian Kernel

>[!example]
>The **Laplacian kernel** or **Laplacian RBF kernel** is defined as 
>$$
> \begin{align}
> K_{\gamma}(x, x') &= \exp\left( - \gamma \lVert x - x' \rVert_{1} \right)
> \end{align}
>$$
>- The parameter $\gamma >0$.
>- This kernel is the *covariance function* for the **Ornstein-Uhlenbeck process.**

- [[Laplace Distribution]]
- [[Ornstein–Uhlenbeck Process]]
- [[Langevin Equation]]

### Cosine Kernel



### Discrete Kernel and Bag-of-Words

>[!example]
>Let $\mathcal{X} := \left\{ s_{1}\,{,}\ldots{,}\, s_{n}\right\} \subset \Sigma^{*}$ be space of *strings* of *arbitrary length* over an *alphabet* $\Sigma$.
>
>A **string kernel** on $\mathcal{X}$ between two strings $s,t\in \mathcal{X}$ from *exact matches* is defined as 
>$$
>K(s, t) := \sum_{r\in \mathcal{X}}\,w_{r}\;\#\left( s, r \right)\;\#\left( r, r \right)
>$$
>where
>- $$\#\left( s, r \right) = \lvert \left\{ i: r = s[i:i+|r|] \right\} \rvert $$ is defined as the **number of ocurrance (exact match)** of a *substring* $r$ in $s$.
>- $w_{r} \ge 0$ are coefficients.
>- This kernel compare the strings by **means of the substrings** they *contain*. 
>	- The *more substrings* two strings have in common, the *more similar* they are.
>	- The substrings need *not always be* **contiguous**; that said, the *further* apart the *first and last element* of a substring are, the *less weight* should be given to the similarity.

- [[Word Embedding]]
- [[Prefix-Free String]]
- [[Bag-of-Word Model for Document Representation]]
- [[Sequence Classification and Sequence-Pair Classification]]
- Wikipedia [String_kernel](https://en.wikipedia.org/wiki/String_kernel)
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 100

### B-Spline

>[!example]
>The **B-Spline kernel** is defined in $\mathbb{R}^{d}$ as 
>$$
>\begin{align}
>K(x, x') &= B_{2p+1}\left( \lVert x - x' \rVert  \right), p>0 
>\end{align} 
>$$
>where
>- the order $n =2p+1$ is **odd.**
>
>The **B-Spline function** of degree order $n$ is defined *recursively* as the *convolution* of *indicator functions*
>$$
>B_{n} = B_{n-1} * I_{B}
>$$ 
>where
>- $I_{B}$ is the indicator function on a *unit box* $[1 /2 , 1 / 2]^{d}$ or *unit ball* $B(0,1)$ in $\mathbb{R}^{d}$; 
>-  the convolution operation $$f * g = \int f(t)g(\tau- t)dt.$$
>- From this definition, we see that $B_{2p+1}$ can be seen as an *inner product* between two $B_{p}$ functions.

^ba3d76

- [[Convolution Operation]]
- [[B-Spline Functions]]
- Wikipedia [B-spline](https://en.wikipedia.org/wiki/B-spline)
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 87 - 88 

### Matérn Kernel

>[!example]
>The **Matérn kernel** is defined as
>$$
>\begin{align*}
>K(x, x') := \frac{2^{1-\nu}}{\Gamma(\nu)}\left( \frac{\sqrt{2\nu}\lVert x - x' \rVert }{\sigma} \right)^{\nu}\;B_{\nu}\left( \frac{\sqrt{2\nu}\lVert x - x' \rVert}{\sigma} \right)
>\end{align*}
>$$
>where $\nu >0$ and $\sigma >0$
>- $B_{\nu}$ is a  **modified Bessel function**.


- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 84

### Sobolev Space


- [[Sobolev Space]]


### Exponential Kernel and Information Divergence

>[!example]
>The **kernel** from **information-theoretical metric** between two p.d.f. $p,q\in \mathscr{P}(\Omega)$ is defined as 
>$$
> \begin{align}
> K(p, q) &= \exp\left( - \alpha\; \psi(p, q) \right)
> \end{align}
>$$
>Examples of the **information-theoretical metric** include
>- **Jensen-Shannon divergence** $$\begin{align*}\psi(p, q) &= \mathbb{D}_{JSD}\left( p \left\|\right. q \right) \\[5pt] &:= \frac{1}{2}\mathbb{KL}\left( p \left\|\right. \frac{p + q}{2} \right) + \frac{1}{2}\mathbb{KL}\left( q \left\|\right. \frac{p + q}{2} \right)\end{align*}$$
>- **Squared Hellinger distance** $$\begin{align*}\psi(p, q) &= H^2(p, q) \\[5pt] &:= \frac{1}{2} \int_{\Omega}\left(\sqrt{p} - \sqrt{q}\right)^2\,d\mu\end{align*}$$
>- **Symmetric $\chi^2$-divergence** or **triangle discrimination**  $$\begin{align*}\psi(p, q) &= \Delta(p, q) \\[5pt] &:= \frac{1}{2} \int_{\Omega} \frac{\left(p - q\right)^2}{p + q}d\mu \end{align*}$$
>- **Total Variation** $$\begin{align*}\psi(p, q) &= V(p, q) \\[5pt] &:= \frac{1}{2}\int_{\Omega}|p - q| \;d\mu \end{align*}$$

- [[Jensen-Shannon Divergence]]
- [[Chi-squared Divergence]]
- [[Hellinger Distance between Distributions]]
- [[Total Variation between Measures]]
- [[Density Ratio Estimation via Binary Classifiers]]

### Fisher Kernel

>[!example]
>The **Fisher kernel** on $\mathcal{X}$ with respect to a p.d.f. $p(x;\theta)$ in *statistical manifold* $\mathcal{M}_{\theta} \subset \mathcal{P}(\mathcal{X})$ is defined as
>$$
>\begin{align*}
>K_{\theta}(x, x') &= \nabla_{\theta}\ell(\theta; x)^{T}\;I(\theta)^{-1}\;\nabla_{\theta}\ell(\theta; x') \\[8pt]
>&= \sum_{i=1}^{d}\sum_{j=1}^{d} \frac{ \partial \ell }{ \partial \theta^{i} }(\theta; x)\;g^{i,j}(\theta) \frac{ \partial \ell }{ \partial \theta^{j} }(\theta; x')
>\end{align*}
>$$
>where 
>- $I(\theta)$ is **Fisher information matrix** or **Fisher metric** $$I(\theta) = [g_{i,j}(\theta)] = \left[  \mathbb{E}_{ \theta }\left[\frac{ \partial}{ \partial \theta^{i} }\ell(\theta; X) \;\frac{ \partial}{ \partial \theta^{j} }\ell(\theta; X)  \right] \right]_{i,j}$$
>- The **inverse** of Fisher information is denoted as $g^{i,j}$
>- The *Fisher score function* is given as $$s(x;\,\theta) := \nabla_{\theta}\ell(\theta; x) = \left( \frac{ \partial \ell }{ \partial \theta^{1} } \,{,}\ldots{,}\,\frac{ \partial \ell }{ \partial \theta^{d}}\right)^{T}.$$
>- $p(x;\theta)$ plays the role of a **generative model** for both samples $x, x'.$
>- The *Fisher kernel* measure the **similarity** between two **samples** using their corresponding *likelihood scores* relative to a **given model**.
>- The *Fisher kernel* is measured against the *information geometry* in $\mathcal{M}$.

^b8f451

- [[Fisher Information]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]
- [[Log-Likelihood Score Function and Fisher Score]]
- [[Statistical Manifold as Parametric Family]]
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 102

### Tree Kernels and Graph Kernels


- [[Tree Graph and Forest]]
- [[Graph]]
- Wikipedia [Graph_kernel](https://en.wikipedia.org/wiki/Graph_kernel)
- Wikipedia [Tree_kernel](https://en.wikipedia.org/wiki/Tree_kernel)

### Kernel on Sets and Probability Measure


- [[Jaccard Similarity and Jaccard Distance between Two Sets]]
- [[Measure Space and Countably Additive Measure]]
- [[Set Operations]]



### Neural Network as Kernel


- [[Artificial Neural Network and Deep Learning]]

## Explanation


![[pd_kernel_function_table_1.png]]




-----------
##  Recommended Notes and References

- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]


- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 80 - 102
- [[Elements of Statistical Learning by Hastie]] pp 209 - 212
- [[Kernel Methods in Machine Learning by Hofmann]] pp 10 - 16
- [[Learning with Kernels by Schölkopf]] pp 45 - 47,  56 - 57
- [[Foundations of Machine Learning by Mohri]] pp 108 - 131
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 181 - 185
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 38
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 675
- [[Lectures on Gaussian Processes by Lifshits]]
- Wikipedia [Positive-definite_kernel](https://en.wikipedia.org/wiki/Positive-definite_kernel)