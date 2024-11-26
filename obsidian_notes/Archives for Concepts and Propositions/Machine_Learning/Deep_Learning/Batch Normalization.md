---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - batch_normalization
topics:
  - deep_learning/algorithm
  - deep_learning/regularization
name: Batch Normalization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Batch Normalization

### Training Phase

>[!important] Definition
>**Batch normalization** provide additional layer that normalize the *hidden unit values* for every time the weight is *updated.* It normalizes across *all examples* for *each hidden unit independently*.
>
>Let $a_{n,i}$ be the **pre-activations**, for a sample $n$ in a mini-batch  of $K$ samples, 
>$$
>a_{n,i} = \left\langle  w_{i}\,,\, x_{n} \right\rangle, \quad n=1 \,{,}\ldots{,}\,K
>$$
>where $x_{n}\in \mathbb{R}^{d}$ is the input or the output of previous layer. Denote the *activation values*  as $z_{i} = h(a_{i})$
>
>For each *mini-batch* of size $K$, **batch normalization** is described as below:
>- For each hidden units $i=1\,{,}\ldots{,}\,d$ (in parallel)
>	- Compute the *sample mean* $$\mu_{i} = \frac{1}{K} \sum_{n=1}^{K}a_{n,i}$$ and *sample variance* $$\sigma_{i}^2 = \frac{1}{K} \sum_{n=1}^{K}\left(a_{n,i} - \mu_{i}\right)^2$$
>	- **Normalize** the **pre-activations** for each sample within mini-batch $$\hat{a}_{n,i} = \frac{a_{n,i} - \mu_{i}}{\sqrt{ \sigma_{i}^2 + \delta  }}, \quad n=1 \,{,}\ldots{,}\,K$$
>	- **Re-scaling** the *normalized pre-activations* to have **mean** $\beta_{i}$ and **standard deviation** $\gamma_{i}$ $$\tilde{a}_{n,i} = \gamma_{i}\,\hat{a}_{n,i} + \beta_{i}$$
>  
>- *Output*: *rescaled normalized pre-activation* $(\tilde{a}_{n,i})$ for $n=1\,{,}\ldots{,}\,K$ and $i=1\,{,}\ldots{,}\,d$ 


![[batch_norm.png]]


>[!important]
>The *learnable* parameter for **batch normalization** are the **rescaling mean** and **standard deviations** $$(\gamma_{i}, \beta_{i}), \quad i=1\,{,}\ldots{,}\,d.$$
>
>They can be learned via *gradient descent jointly* with weights and biases.

- [[Stochastic Gradient Descent Algorithm]]

### Inference Phase

>[!important] Definition
>During the **prediction time**, there is no mini-batch and we cannot determine $\mu_{i}$ and $\sigma_{i}^2$ based on mini-batch. 
>
>To solve this, we can evaluate these two quantities **throughout the training phase** via **moving averages**
>$$
>\begin{align*}
> \bar{\mu}_{i} &= \alpha\,\hat{\mu}_{i}^{(t-1)} + (1- \alpha)\,\mu_{i}\\[5pt]
> \bar{\sigma}_{i}^2 &= \alpha\, \bar{\sigma}_{i}^{(t-1)} + (1- \alpha)\,\sigma_{i} 
>\end{align*}
>$$
>where $\alpha\in [0,1]$. 
>
>These moving averages *play no role* during **training** but are used to **process new data points** during the **inference phase**.



## Explanation

>[!info]
>The formula above assume the batch normalization **before activation**. In practice, either before or **after activation** can be used.

>[!info]
>To solve the lack of mini-batch in prediction time, we could in principle evaluate $\mu_{i}$ and $\sigma_{i}^2$ as 
>$$
>\begin{align*}
> \mu_{i} &= \frac{1}{N} \sum_{n=1}^{N}a_{n,i}\\[5pt]
> \sigma_{i}^{(t)} &= \frac{1}{N} \sum_{n=1}^{N}\left(a_{n,i} - \mu_{i}\right)^2
>\end{align*}
>$$
>for *each layer* **across the whole training set** **after** we have made the **final update** to the weights and biases. However, this would involve processing the whole data set just to evaluate these quantities and is therefore usually **too expensive**.


>[!quote]
>It might appear that the transformation (7.55) has simply *undone the effect* of the batch normalization since the mean and variance can now adapt to arbitrary values again. However, the **crucial difference** is in the way the parameters evolve during training. For the original network, the *mean and variance* across a mini-batch are **determined** by a complex function of **all the weights and biases** in the layer, whereas in the representation given by (7.55), they are determined directly by **independent parameters** $\beta_{i}$ and $\gamma_{i}$, which turn out to be much **easier to learn** during gradient descent.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 228

>[!quote]
>Although batch normalization is very effective in practice, there is uncertainty as to why it works so well. *Batch normalization* was originally motivated by noting that *updates to weights in earlier layers* of the network *change the distribution* of values seen by *later layers*, a phenomenon called **internal covariate shift**. However, later studies (Santurkar et al., 2018) suggest that covariate shift is not a significant factor and that the improved training results from an improvement in the smoothness of the error function landscape.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 229

- [[Covariate Shift or Domain Shift in Machine Learning]]

## Vanishing and Exploding Gradient

>[!important] Definition
>One of the main **motivations** for *batch normalization* arises from the phenomena of **vanishing gradients** and **exploding gradients**, which occur when we try to train very deep neural networks. 
>
>From the chain rule of calculus, the gradient of an error function $E$ with respect to a parameter in the *first layer* of the network is given by
>$$
>\begin{align*}
> \frac{ \partial E }{ \partial w_{i} } = \sum_{m}\,\ldots\,\sum_{l}\sum_{j}\frac{ \partial z_{m}^{(1)} }{ \partial w_{i} }\,\ldots\,\frac{ \partial z_{j}^{(K)} }{ \partial z_{l}^{(K-1)} }\frac{ \partial E }{ \partial z_{j}^{(K)} }
>\end{align*}
>$$
>where $z_{j}^{(k)}$ denotes the *activation* of node $j$ in layer $k$, and each of the partial derivatives on the right-hand side represents the elements of the *Jacobian matrix* for that layer.
>
>The **product** of *a large number* of such terms will tend **towards** $0$ if *most of them* have a magnitude $< 1$ and will tend **towards** $\infty$ if *most of them* have a magnitude $> 1$. Consequently, as the depth of a network increases, **error function gradients** can tend to become either *very large* or *very small*.

- [[Vanishing and Exploding Gradient Problems for Sequential Networks]]
- [[Jacobian Matrix and Jacobian Determinant]]

## Layer Normalization

- [[Layer Normalization]]




-----------
##  Recommended Notes and References

- [[Layer Normalization]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627
- [[Deep Learning by Goodfellow]] pp 260, 413
- [[Deep Learning Foundations and Concepts by Bishop]] pp 227