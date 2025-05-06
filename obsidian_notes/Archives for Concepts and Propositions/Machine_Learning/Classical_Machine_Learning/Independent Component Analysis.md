---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/dimensionality_reduction
  - ICA
  - independent_component_analysis
  - dimensionality_reduction
keywords:
  - dimensionality_reduction
  - ICA
  - independent_component_analysis
topics:
  - probabilistic_graphical_model
  - machine_learning_models
name: Independent Component Analysis
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Independent Component Analysis

>[!important] Definition  
>The **Independent Component Analysis (ICA)** algorithm separates a multivariate signal — typically sensor mixtures — into statistically *independent source components* without knowing the original mixing process.  
>
>- *Require*: an observed data matrix  $\mathbf{X}\in\mathbb{R}^{m\times T}$ containing $m$ mixed signals (rows) over $T$ samples.  
>- *Assume*:  
>	- A *linear, instantaneous* mixing model $$\mathbf{X}= \mathbf{A}\,\mathbf{S}$$ where:  
>	- $\mathbf{S}\in\mathbb{R}^{n\times T}$ holds $n$ unknown, mutually independent sources.  
>	- $\mathbf{A}\in\mathbb{R}^{m\times n}$ is an unknown full-rank mixing matrix.  
>	- At most one source is Gaussian (*non-Gaussianity* drives identifiability).  
>
>- **Step 0  (Pre-whitening)**  
>	- Center: $$\mathbf{X}\leftarrow \mathbf{X}-\mathbb{E}[\mathbf{X}].$$  
>	- Compute covariance $$\mathbf{C}=\frac{1}{T}\mathbf{X}\mathbf{X}^\top.$$  
>	- *Eigen-decompose* $$\mathbf{C}=\mathbf{E}\,\mathbf{\Lambda}\,\mathbf{E}^\top.$$  
>	- *Whiten*: $$\mathbf{Z}= \mathbf{\Lambda}^{-1/2}\mathbf{E}^\top \mathbf{X}$$ so that $$\text{Cov}[\mathbf{Z}]=\mathbf{I}.$$  
>
>- **Step 1  (Estimate un-mixing vectors)** – *FastICA* variant  
>	- For each independent component $k=1,\dots,n$:  
>		- Initialise a random weight vector $\mathbf{w}^{(0)}\in\mathbb{R}^{m}$ with $$ \lVert\mathbf{w}^{(0)}\rVert=1.$$  
>	- **Iterate Newton fixed-point** until convergence:  
> 	    - $$\mathbf{w}^{+} \gets \mathbb{E}\!\bigl[\mathbf{Z}\,g(\mathbf{w}^\top\!\mathbf{Z})\bigr] - \mathbb{E}\!\bigl[g'(\mathbf{w}^\top\!\mathbf{Z})\bigr]\mathbf{w}$$
> 		    - where $g(\cdot)$ is a non-linear *contrast* (e.g. $\tanh$, cube).  
> 	    - **Orthogonalise** against previously found components:  
>       $$\mathbf{w}^{+}\leftarrow \mathbf{w}^{+}-\sum_{j<k}(\mathbf{w}^{+}\!\cdot\!\mathbf{w}_j)\,\mathbf{w}_j.$$  
> 	    - **Normalise**: $$ \mathbf{w}^{+}\leftarrow\mathbf{w}^{+}/\lVert\mathbf{w}^{+}\rVert.$$  
> 	    - If $\bigl|\mathbf{w}^{+\top}\mathbf{w}-1\bigr|<\epsilon$ then **converged**; 
> 		    - set $$\mathbf{w}_k=\mathbf{w}^{+},$$ 
> 	    - else $$ \mathbf{w}\leftarrow\mathbf{w}^{+}.$$  
>
>- **Step 2  (Form un-mixing matrix)**  $$\mathbf{W} = [\mathbf{w}_1^\top;\dots;\mathbf{w}_n^\top] \in\mathbb{R}^{n\times m}.$$  
>
>- **Step 3  (Recover sources)**  $$\widehat{\mathbf{S}} = \mathbf{W}\,\mathbf{Z}$$ (add mean back if needed).  
>
>- *Return*:  
>	- *Independent component estimates* $\widehat{\mathbf{S}}$.  
>	- *Un-mixing matrix* $\mathbf{W}$ such that  $$\mathbf{X}\approx\mathbf{A}\,\widehat{\mathbf{S}}.$$  

- [[Newton Method]]
- [[Fixed Point of Map]]
- [[Gram-Schmidt Orthogonalization]]
- [[QR Factorization of Matrix]]


## Explanation


>[!info]
>- **Typical uses**: EEG/MEG artefact removal, cocktail-party audio separation, financial factor analysis, latent-variable discovery.  
>
>- **Caveats**: component order and scale are indeterminate; requires sufficient samples and non-Gaussian sources.


## Kernel ICA

- [[bachKernelIndependentComponent2002]] Bach, Francis. R., & Jordan, Michael. I. (2002). Kernel Independent Component Analysis. *Journal of Machine Learning Research*, *3*, 1-48. https://doi.org/10.1162/153244303768966085



-----------
##  Recommended Notes and References


- [[Principal Component Analysis]]
- [[Probabilistic Principal Component Analysis]]
- [[Gaussian Random Vector]]

- [[Latent Variable Models]]

- [[QR Iteration for General Eigenvalue Problem]]


- [[Curse of Dimensionality]]
- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]


- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 961 - 968
- [[Deep Learning Foundations and Concepts by Bishop]] pp 514 - 515
- [[Elements of Information Theory by Cover]]

- [[Kullback-Leibler Divergence]]
- Bach, Francis. R., & Jordan, Michael. I. (2002). Kernel Independent Component Analysis. *Journal of Machine Learning Research*, *3*, 1-48. https://doi.org/10.1162/153244303768966085