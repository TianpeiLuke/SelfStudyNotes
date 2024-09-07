---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
keywords:
  - multinomial_pca
  - multinomial_priniciple_component_analysis
topics:
  - unsupervised_models
  - dimensionality_reduction
  - machine_learning_models
  - probabilistic_graphical_model
name: Multinomial Principle Component Analysis
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Multinomial Principle Component Analysis

>[!important] Definition
>Let $$x_{i}  \in \{ 1 \,{,}\ldots{,}\, V\}$$ be $n$ i.i.d. **categorical variables** where $V$ is the **size** of **category**, 
> 
>Moreover, 
>- define $$z := ( z_{1} \,{,}\ldots{,}\, z_{s} ) \in \Delta_{s-1}$$ as a **latent variable** 
>	- $z$ represent the *proportion* of topics/memberships/groups in the data.  
>	- $z$ is **random**
>	- $$z\in \left\{ (z_{1} \,{,}\ldots{,}\,z_{s}): \sum_{i=1}^{s}z_{i} = 1, \; z_{i} \in [0,1] \right\} $$
>- Let $$W_{i} = [w_{k,v}^{(i)}]\in [0,1]^{s \times V},$$ be the matrix whose **row** represents the **categorical distributions** for each **group (row)** $$W_{i}[k,:] = [w_{k,v}^{(i)}, v\in V] \in \Delta_{V-1}.$$
>	- Denote $p_{i,v} := \mathcal{P}\left(x_{i} = v \;|\; z\right)$, then  $$p_{i} = (p_{i,1} \,{,}\ldots{,}\,p_{i,V}) = z^{T}\,W_{i} \in \Delta_{V-1}$$
>  
>  
>The **Multinomial Principle Component Analysis (mPCA)** considers the following *latent variable model*:
>$$
>\left\{
>\begin{align*}
> \; p(z\,;\, \alpha) &= \text{Dirichlet}(z\;|\;\alpha) \\[5pt]
> \; p(x\;|\; z,\, W) &=  \prod_{i=1}^{n}\text{Multinomial}(x_{i}\;|\; z^{T}\,W_{i})
>\end{align*}
>\right.
>$$  
>where $w_{m_{n}}  := W_{m_{n}, :} \in \Delta_{V-1}$.
>

- [[Multinomial Distribution]]
- [[Dirichlet Distribution]]
- [[Latent Variable Models]]


>[!info]
>This model is also called 
>- **user rating profile model**, 
>- **admixture model** 
>- **mixed membership model**  
>- **multinomial PCA (mPCA)** or 
>- **simplex factor analysis (sFA)**

![[mPCA.png]]



## Explanation





-----------
##  Recommended Notes and References


- [[Dirichlet Distribution]]
- [[Multinomial Distribution]]
- [[Probabilistic Principle Component Analysis]]
- [[Principle Component Analysis]]


- [[Multinomial Naive Bayes Model]]
- [[Latent Dirichlet Allocation]]
- [[Factor Analysis]]
- [[Latent Variable Models]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 952