---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/latent_variable_model
  - recommender_system/information_filter
  - non-negative_matrix_factorization
  - NMF
keywords:
  - dimensionality_reduction
  - non-negative_matrix_factorization
topics:
  - probabilistic_graphical_model
  - machine_learning_models
name: Nonnegative Matrix Factorization or NMF
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Nonnegative Matrix Factorization or NMF


>[!important] Definition
>Consider a non-negative matrix $V \in \mathbb{R}_{\ge 0}^{m \times n}$. 
>
>The goal of **Non-negative Matrix Factorization (NMF)** is to 
>- find two *non-negative matrices* $W \in \mathbb{R}_{\ge 0}^{m \times k}$ and $H \in \mathbb{R}_{\ge 0}^{k \times n}$ such that their product approximates the original matrix $V$:
>$$V \approx WH$$
>where $k$ is a user-specified rank, and typically $k < \min(m, n)$.

- [[Nonnegative and Positive Matrix]]
- [[Irreducible Nonnegative Matrix]]
- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]

### Loss Function

>[!important] Definition
>The objective is to minimize a loss function that measures the difference between $V$ and $WH$. Common loss functions include:
>- **Squared Euclidean distance (Frobenius norm):** $$\mathcal{L}(W, H) = \|V - WH\|_F^2 = \sum_{i=1}^m \sum_{j=1}^n (V_{ij} - (WH)_{ij})^2$$
>- **Kullback-Leibler (KL) divergence (for probabilistic interpretations):** $$\mathcal{L}(W, H) = \sum_{i=1}^m \sum_{j=1}^n \left( V_{ij} \log\left(\frac{V_{ij}}{(WH)_{ij}}\right) - V_{ij} + (WH)_{ij} \right)$$

- [[Frobenius Norm of Matrix]]
- [[Minimum Mean Square Estimation]]
- [[Kullback-Leibler Divergence]]
- [[Maximum Entropy Learning]]

### Algorithm


>[!important] Definition
>The **Non-negative Matrix Factorization algorithm** iteratively updates the matrices $W$ and $H$ to minimize the chosen loss function while maintaining their non-negativity.
>
>A common approach to update $W$ and $H$ using the **Frobenius norm** is based on multiplicative update rules:
>
>- *Require*: a non-negative matrix $V \in \mathbb{R}_{\ge 0}^{m \times n}$
>- *Require*: a positive integer $k < \min(m, n)$ (the rank)
>- *Require*: initialize non-negative matrices $W^{(0)} \in \mathbb{R}_{\ge 0}^{m \times k}$ and $H^{(0)} \in \mathbb{R}_{\ge 0}^{k \times n}$ (e.g., with random non-negative values)
>- *Require*: a number of iterations $N$ or a convergence criterion
>- For $i = 1, \ldots, N$:
>	- Update $H$: $$H_{ji}^{(t+1)} = H_{ji}^{(t)} \frac{(W^{(t)})^T V_{ji}}{(W^{(t)})^T W^{(t)} H^{(t)}_{ji}}$$
>	- Update $W$: $$W_{ij}^{(t+1)} = W_{ij}^{(t)} \frac{V (H^{(t+1)})^T_{ij}}{W^{(t)}_{ij} H^{(t+1)} (H^{(t+1)})^T_{j}}$$
>	- (Element-wise multiplication and division are assumed)
>	- Check for convergence if a criterion is defined.
>- *Return*: 
>	- the non-negative factor matrices $W^*$ and $H^*$ that approximate $V \approx W^*H^*$


## Explanation

>[!important]
>The resulting matrices $W$ and $H$ of **NMF** can provide a *parts-based representation* of the data in $V$. 
>- The *columns* of $W$ can be seen as *basis vectors*, and 
>- the *columns* of $H$ contain the *coefficients that represent* each data point in $V$ as a non-negative linear combination of these basis vectors.



## Applications

### Dimensionality Reduction

- [[Curse of Dimensionality]]
- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]

### Collaborative Filtering

- [[Collaborative Filtering]]
- [[Model-based Collaborative Filtering]]
- [[User-Item Preference and Rating for Recommendation]]

### Topic Modeling

- [[Topic Models]]
- [[Word Embedding]]
- [[Co-Occurrence Matrix]]

### Clustering

- [[Spectral Clustering]]

### Text Summarization

- [[Text Summarization]]





-----------
##  Recommended Notes and References


- [[Nonnegative and Positive Matrix]]
- [[Principal Component Analysis or PCA]]
- [[Probabilistic Principal Component Analysis]]
- [[Gaussian Random Vector]]

- [[Latent Variable Models]]







- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Elements of Information Theory by Cover]]
- [[Matrix Analysis by Horn]]
- [[Convex Optimization Algorithms by Bertsekas]] pp 30 
- [[Recommender Systems Textbook by Aggarwal]] pp

- [[Kullback-Leibler Divergence]]