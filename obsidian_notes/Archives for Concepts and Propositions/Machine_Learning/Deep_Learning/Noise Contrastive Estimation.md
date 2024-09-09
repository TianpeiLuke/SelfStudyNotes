---
tags:
  - concept
  - deep_learning/algorithms
  - machine_learning/noise_tolerate_learning
  - deep_learning/representation_learning
keywords:
  - noise_contrastive_estimation
  - representation_learning
topics:
  - deep_learning/models
  - deep_learning/contrastive_learning
  - representation_learning
name: Noise Contrastive Estimation
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Noise Contrastive Estimation

![[Gibbs Measure and Energy-based Model#^c81bcd]]


>[!important] Definition
>Let $p_{\text{data}}(x)$ be the *data distribution*, and let $p_{\text{noise}}(x)$ be a *known distribution*, called the **noise distribution**. 
>- It is common to choose simple noise distribution such as $\mathcal{N}(0, I)$ so that we can sample from it easily. 
>
>Let $Y\in \{ 0, 1 \}$ be a *binary variable* with Bernoulli distribution, which *selects* the component from a *mixture distribution* of noise and data $$p_{\text{joint}}(x) := p(Y = 1)\,p_{\text{data}}(x) + p(Y = 0)\,p_{\text{noise}}(x).$$ 
>- $$p_{\text{joint}}(x | Y=1) = p_{\text{data}}(x) , \;\; p_{\text{joint}}(x | Y=0) = p_{\text{noise}}(x).$$
>- The *posterior distribution* of $Y=0$ given data is $$p_{\text{joint}}(Y=0 \,|\,x) = \frac{p(Y = 0)\,p_{\text{noise}}(x)}{p_{\text{joint}}(x)} = \frac{p_{\text{noise}}(x)}{ p_{\text{noise}}(x) + \nu\,p_{\text{data}}(x)}$$ where $$\nu = \frac{p(Y = 1)}{p(Y = 0)}$$
>- We can replace the *data distribution* with the *model distribution*, e.g. $$p_{\text{data}}(x) \leftarrow p_{\theta}(x)$$
>- Then $$p_{\text{joint}, \theta}(Y=0 \,|\,x) = \frac{p_{\text{noise}}(x)}{ p_{\text{noise}}(x) + \nu\,p_{\theta}(x)}.$$
>
>The **noise contrastive estimation (NCE)** indirectly fits the model distribution $p_{\theta}(x)$ to data distribution $p_{\text{data}}(x)$ by fitting the posterior of noise indicator from $p_{\text{joint}, \theta}(Y \,|\,x)$ to $p_{\text{joint, data}}(Y\,|\,x)$ via *conditional maximum likelihood estimation*
>$$
>\begin{align*}
> \theta^{*} &= \arg\min_{\theta}\; \mathbb{E}_{p_{\text{joint, data}}(Y| X) }\left[  \mathbb{KL}\left(  p_{\text{joint, data}}(Y \,|\,X) \left\|\right. p_{\text{joint}, \theta}(Y \,|\,X) \right) \right] \\[5pt]
> &= \arg\max_{\theta}\;\mathbb{E}_{p_{\text{joint, data}}(X, Y) }\left[ \log p_{\text{joint}, \theta}(Y \,|\,X) \right] 
>\end{align*}
>$$
  

- [[Gibbs Measure and Energy-based Model]]
- [[Bernoulli Distribution]]
- [[Gaussian Mixture Models]]
- [[Maximum Likelihood Estimation]]
- [[Kullback-Leibler Divergence]]


>[!info]
>The *posterior distribution* of $Y=0$ given data is $$p_{\text{joint, model}}(Y=0 \,|\,x) = \frac{p(Y = 0)\,p_{\text{noise, model}}(x)}{p_{\text{joint}}(x)} = \frac{p_{\text{noise}}(x)}{ p_{\text{noise}}(x) + \nu\,p_{\text{model}}(x)}$$ where $$\nu = \frac{p(Y = 1)}{p(Y = 0)}$$ 
>
>It is essentially just **logistic regression**
>$$
>\begin{align*}
> p_{\text{joint, model}}(Y=1 \,|\,x) &= \frac{1}{1 + \nu^{-1}\, \frac{p_{\text{noise}}(x)}{p_{\text{model}}(x)}  } \\[5pt]
> &= \sigma \left(- \log \left(\nu^{-1}\, \frac{p_{\text{noise}}(x)}{p_{\text{model}}(x)}  \right)\right)  \\[5pt]
> &= \sigma \left(\log p_{\text{model}}(x) - \log p_{\text{noise}}(x) + \log \nu\right)
>\end{align*}
>$$
>- Set $P(Y=0) = P(Y=1) = 1 / 2$, so that $\log \nu = 0.$ So that 
>$$
>\begin{align*}
> p_{\text{joint, model}}(Y=1 \,|\,x) &= \frac{1}{1 +  \frac{p_{\text{noise}}(x)}{p_{\text{model}}(x)}  } \\[5pt]
> &= \sigma \left(\log p_{\text{model}}(x) - \log p_{\text{noise}}(x) \right)
>\end{align*}
>$$
>- The **final layer** is to **contrast two log-densities**
>- The loss function is $$\begin{align*}L(\theta) &= \sum_{i=1}^{n} \left\{Y_{i} \log p_{\text{joint}, \theta}(Y_{i} = 1 \,|\,X_{i}) + (1 - Y_{i})\,\log \left( 1 - p_{\text{joint}, \theta}(Y_{i} = 1\,|\,X_{i}) \right) \right\} \\[5pt] &= \sum_{i=1}^{n} \left\{Y_{i} \log h(X_{i}; \theta) + (1 - Y_{i})\,\log \left( 1 - h(X_{i}; \theta)\right) \right\}  \end{align*}$$

- [[Logistic Regression]]


>[!info]
>When the *mixture of noise and model* matches *the mixture of noise and data*, we have
>$$
>\begin{align*}
> p_{\text{joint, model}}(Y=0 \,|\,x) &= p_{\text{joint, data}}(Y=0 \,|\,x) \\[5pt]
> \iff \frac{p_{\text{noise}}(x)}{ p_{\text{noise}}(x) + \nu\,p_{\text{model}}(x)} &= \frac{p_{\text{noise}}(x)}{ p_{\text{noise}}(x) + \nu\,p_{\text{data}}(x)} \\[5pt]
> \iff p_{\text{model}}(x) &= p_{\text{data}}(x)
>\end{align*}
>$$



## Explanation

### Intractable Partition Function

>[!quote]
>Most techniques for estimating models with **intractable partition functions** do not provide an *estimate of the partition function*. **SML** and **CD** estimate only the gradient of the log partition function, rather than the partition function itself. **Score matching** and **pseudolikelihood** avoid computing quantities related to the partition function altogether.
>
>**Noise-contrastive estimation (NCE)** (Gutmann and Hyvarinen, 2010) takes a different strategy. In this approach, the probability distribution estimated by the model is represented explicitly as $$\log p_{\text{model}}(x) = \log \tilde{p}_{\text{model}}(x; \theta) + c,$$ where $c$ is explicitly introduced as an **approximation** of $- \log Z(\theta).$ Rather than estimating only $\theta$, the noise contrastive estimation procedure treats $c$ as just *another parameter* and estimates $\theta$ and $c$ *simultaneously*, using the same algorithm for both. The resulting $\log p_{\text{model}}(x)$ thus may *not* correspond *exactly to a valid probability distribution*, but it will become closer and closer to being valid as the estimate of $c$ improves.
>
>-- [[Deep Learning by Goodfellow]] pp 612

- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Gibbs Measure and Energy-based Model]]

>[!quote]
> NCE works by reducing the *unsupervised learning problem* of estimating $p(x)$ to that of *learning a probabilistic binary classifier* in which one of the categories corresponds to the data generated by the model. This *supervised learning problem* is constructed in such a way that maximum likelihood estimation defines an *asymptotically consistent estimator* of the original problem.
> 
>-- [[Deep Learning by Goodfellow]] pp 612 

- [[Supervised Learning and Unsupervised Learning]]

>[!quote]
>Another principle for learning the parameters of EBMs is *Noise contrastive estimation (NCE)*, introduced by [GH10]. It is based on the idea that we can learn an EBM by **contrasting it with another distribution** with known density.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 850

### Challenges

>[!quote]
>When NCE is applied to problems with **many random variables**, it becomes *less efficient*. The logistic regression classifier can reject a noise sample by identifying any one variable whose value is unlikely. This means that learning *slows down greatly* after $p_{\text{model}}$ has learned the basic marginal statistics. 
>
 >The **constraint** that $p_{\text{noise}}$ must be *easy to evaluate and easy to sample* from can be overly restrictive. When $p_{\text{noise}}$ is simple, most samples are likely to be *too obviously distinct* from the data to force pmodel to improve noticeably.  
 >
 >Like *score matching* and *pseudolikelihood*, **NCE does not work if only a lower bound on $\tilde{p}$ is available**. Such a lower bound could be used to construct a *lower bound* on $p_{\text{joint}}(Y=1|x)$, but it can only be used to construct an *upper bound* on $p_{\text{joint}}(Y=0|x)$, which appears in half the terms of the NCE objective. Likewise, a *lower bound* on $p_{\text{noise}}$ is not useful, because it provides only an *upper bound* on $p_{\text{joint}}(Y=1|x)$.

### Approximate Partition Function

>[!quote]
>As one unique feature that *contrastive divergence* and *score matching* do not have, NCE provides the **normalizing constant** of an *Energy-Based Model* as a by-product of its training procedure. When the EBM is very expressive, e.g., a deep neural network with many parameters, we can assume it is able to approximate a normalized probability density and absorb $Z(\theta)$ into the parameters of $E_{\theta}(x)$ [MT12], or equivalently, fixing $Z(\theta) = 1$. The resulting EBM trained with NCE will be **self-normalized**, i.e., having a normalizing constant close to $1$.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 851


## Score Matching

- [[Score Matching and Denoising Score Matching]]

## Generative Adversarial Network

>[!quote]
>*Noise contrastive estimation* is based on the idea that a **good generative model** should be able to **distinguish data from noise**. A closely related idea is that a good generative model should be able to generate samples that no classifier can distinguish from data. This idea yields generative adversarial networks.
>
>-- [[Deep Learning by Goodfellow]] pp 614

- [[Generative Adversarial Network]]





-----------
##  Recommended Notes and References


- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Contrastive Learning]]
- [[Denoising Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 850 - 852
- [[Deep Learning by Goodfellow]] pp 612 - 614
- [[Deep Learning Foundations and Concepts by Bishop]] pp 191
- Gutmann, M., & Hyvärinen, A. (2010, March). Noise-contrastive estimation: A new estimation principle for unnormalized statistical models. In _Proceedings of the thirteenth international conference on artificial intelligence and statistics_ (pp. 297-304). JMLR Workshop and Conference Proceedings.