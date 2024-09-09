---
tags:
  - concept
  - deep_learning/representation_learning
  - machine_learning/models
  - probabilistic_graphical_models/theory
keywords:
  - score_function
  - score_matching
  - log_partition_function
topics:
  - representation_learning
  - probabilistic_graphical_model
  - machine_learning_theory
name: Score Matching and Score Loss Minimization
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: Score Matching and Score Loss Minimization

![[Exponential Family of Distributions#^c95a01]]

![[Log-Partition Function and Score Function of Graphical Models#^830c6c]]

>[!important] Definition
>The **score function** or **Stein score** is defined as the *gradient of the log-likelihood* with respect to the *data vector* $x$ and is given by $$s(x) := \nabla_{x} \log p(x).$$

- [[Exponential Family of Distributions#Score Function]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Log-Likelihood Score Function]]
- [[Likelihood Function]]
- [[Information Projection and Moment Projection]]


>[!important] Definition
>The **score matching (SM)** strategy is to minimize the *expected square difference* between the derivatives of the *model's log density* with respect to the **input**, and the derivatives of the *data's log density*  with respect to input
>$$
>\min_{\theta} \mathbb{E}_{ X \sim p_{\text{data}} }\left[ \frac{1}{2}  \lVert \nabla_{x} \log p_{\text{data}}(X) - \nabla_{x} \log p_{\text{model}}(X; \theta)  \rVert_{2}^2 \right] 
>$$ 
>The loss above is called the **Fisher divergence**. The goal of training is to **match** the *model score* to the *data score*.
>
>Under certain **regularity conditions** on data $p_{\text{data}}$, (e.g. *continuously differentiable*, *finite everywhere*),  the loss function can be reformulated as
>$$
>\begin{align*}
>L(\theta)&:= \mathbb{E}_{ X \sim p_{\text{data}} }\left[ \sum_{j=1}^{d}\left\{\frac{ \partial^2 }{ \partial x_{j}^2 } \log p_{\text{model}}(X; \theta) + \frac{1}{2} \left(\frac{ \partial  }{ \partial x_{j} } \log p_{\text{model}}(X; \theta)\right)^2  \right\} \right] \\[5pt]
>&:= \mathbb{E}_{ X \sim p_{\text{data}} }\left[\text{tr}\left(\frac{ \partial s(X; \theta) }{ \partial x } \right)  +  \frac{1}{2} \lVert s(X; \theta) \rVert^2  \right] 
>\end{align*}
>$$
>where the *Jacobian* of the score function
>$$
>\frac{ \partial s(X; \theta) }{ \partial x } = D\,s(X; \theta) \in \mathbb{R}^{d\times d}
>$$

^6a12a8

- [[Deep Learning by Goodfellow]] pp 609
- [[Minimum Mean Square Estimation]]
- [[REINFORCE Algorithm with Baseline]]

>[!important]
>Here it is important to emphasize that the *gradient* is *with respect to the* **data vector**, **not** with respect to any **parameter vector**.
>$$\nabla_{x} \log p(x; \theta) \neq \nabla_{\theta} \log p(x ; \theta)$$


>[!info]
>Note that since we need to compute $\nabla \log p$, it is *not applicable* to models of **discrete data** but the *latent variables* in the model may be discrete.



## Explanation


>[!quote]
>**Score matching** (Hyvärinen, 2005) is an alternative to maximum likelihood. It provides a consistent estimator of probability distributions based on encouraging the model to have the same **score** as the data distribution at every training point $x$.
>
>-- [[Deep Learning by Goodfellow]] pp 503

>[!quote]
>Initially, score matching appears to have a new difficulty: **computing the score** of the **data distribution** requires knowledge of the *true distribution* generating the training data, $p_{\text{data}}$. Fortunately, minimizing the expected value of $L(x, \theta)$ is equivalent to minimizing the expected value of 
>$$
>\mathbb{E}_{ X \sim p_{\text{data}} }\left[ \sum_{j=1}^{d}\left\{\frac{ \partial^2 }{ \partial x_{j}^2 } \log p_{\text{model}}(X; \theta) + \frac{1}{2} \left(\frac{ \partial  }{ \partial x_{j} } \log p_{\text{model}}(X; \theta)\right)^2  \right\} \right] 
>$$
>
>-- [[Deep Learning by Goodfellow]] pp 609

>[!quote]
>Like **pseudolikelihood**, *score matching* only works when we are able to **evaluate** $\log \tilde{p}(x)$ and its *derivatives directly*. It is not compatible with methods that provide only a lower bound on $\log \tilde{p}(x)$, because score matching requires the derivatives and second derivatives of $\log \tilde{p}(x)$, and a lower bound conveys no information about its derivatives. This means that score matching **cannot be applied** to estimating models with *complicated interactions* between the hidden units, such as sparse coding models or deep Boltzmann machines. While score matching can be used to pretrain the first hidden layer of a larger model, it has *not been applied as a pretraining strategy* for the deeper layers of a larger model. This is probably because the hidden layers of such models usually contain some discrete variables.
>
>-- [[Deep Learning by Goodfellow]] pp 610


## Fisher Divergence and KL Divergence

- [[Fisher Divergence]]
- [[Kullback-Leibler Divergence]]



## Denoising Score Matching with Smoothed Density

>[!info] 
>One problem with the loss function is that we *cannot minimize it directly* because we do not know the *true data score* $\nabla_{x} \log p(x)$.
>
>Thus instead of computing the true data score, we can estimate it using **kernel density estimation**

>[!important] Definition
>Let $K_{\sigma}(y, x)$ be a **noise kernel** that defines the *corruption process*. The role of $K$ is to *smooth out* the data points and to give a smooth, differentiable representation of density (i.e. the **kernel density estimation**). 
>
>The **smoothed data density** is defined as  
>$$
>p_{\text{smooth}}(x ; \sigma) = \int_{\mathcal{Y}}\; K_{\sigma}(y, x) p_{\text{data}}(y) dy
>$$ 
>where $p_{\text{data}}(y)$ is the empirical measure
>$$
>p_{\text{data}}(y) = \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\left\{ X_{i} = y \right\}. 
>$$
>
>The **denoising score matching (DSM)** strategy is to minimize the mean squared error between model score and the *smoothed data score* 
>$$
>\begin{align*}
>L(\theta) &:=  \frac{1}{2} \mathbb{E}_{ X \sim p_{\text{smooth}} }\left[ \lVert \nabla_{x} \log p_{\text{smooth}}(X) - \nabla_{x} \log_{x} p_{\text{model}}(X; \theta)  \rVert_{2}^2 \right] \\[5pt]
>& := \frac{1}{2} \int \lVert \nabla_{x} \log p_{\text{model}}(x; \theta) - \nabla_{x} \log p_{\text{smooth}}(x ; \sigma)  \rVert_{2}^2\; p_{\text{smooth}}(x ;  \sigma)\; dx \\[5pt]
>& = \frac{1}{2n} \sum_{i=1}^{n} \int \lVert \nabla_{x} \log p_{\text{model}}(x; \theta) - \nabla_{x} \log K_{\sigma}(X_{i}, x)  \rVert_{2}^2\; K_{\sigma}(X_{i}, x)\; dx + \text{ const.}\\[5pt]
>\end{align*}
>$$ 

^bbecdb

- [[Markov Transition Kernel and Transition Function]]
- [[Empirical Process and Empirical Measure]]

>[!info]
>To compute the expectation, we can *sample* from the data distribution, and then *sample* the *noise term*.

- [[Denoising Auto-Encoder]]

>[!quote]
>The **major drawback** of adding noise to data arises when $p_{D}(x)$ is already a well-behaved distribution that *satisfies the regularity conditions* required by score matching. In this case, $$\mathbb{D}_{F}\left( q(\tilde{x}) \left\|\right. p_{\theta}(\tilde{x}) \right) \neq \mathbb{D}_{F}\left( p_{D}(x) \left\|\right. p_{\theta}(x) \right),$$ and DSM is **not a consistent objective** because the optimal EBM matches the noisy distribution $q(\tilde{x})$, not $p_{D}(x)$. This inconsistency becomes non-negligible when $q(\tilde{x})$ *significantly differs* from $p_D(x)$.

## Contrastive Divergence

- [[Contrastive Divergence]]




-----------
##  Recommended Notes and References


- [[Exponential Family of Distributions#Score Function]]
- [[Log-Partition Function and Score Function of Graphical Models]]


- [[Log-Likelihood Score Function]]
- [[Likelihood Function]]
- [[Information Projection and Moment Projection]]
- [[Log-Partition Function of Exponential Family]]


- [[Exponential Family of Distributions]]
- [[Gibbs Distribution]]
- [[Markov Network on Undirected Graph]]


- [[Deep Learning by Goodfellow]] pp 503, 609 - 611
- [[Deep Learning Foundations and Concepts by Bishop]] pp 594 - 597
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 847 - 850