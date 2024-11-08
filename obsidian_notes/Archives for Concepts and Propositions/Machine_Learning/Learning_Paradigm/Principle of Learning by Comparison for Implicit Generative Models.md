---
tags:
  - concept
  - machine_learning/paradigm
  - deep_learning/generative_models
keywords:
  - learning_by_comparison
topics:
  - machine_learning_paradigm
name: Learning by Comparison
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Learning by Comparison

### Implicit Probabilistic Models

>[!quote]
>To develop a probabilistic formulation for GANs, it is useful to first distinguish between two types of probabilistic models: “**prescribed probabilistic models**” and “**implicit probabilistic models**” [DG84]. 
>- **Prescribed probabilistic models**, which we will call **explicit probabilistic models**, provide an explicit parametric specification of the distribution of an observed random variable $x$, specifying a *log-likelihood function* $\log q_{\theta}(x)$ with parameters $\theta$. Most models we encountered in this book thus far are of this form, whether they be state-of-the-art classifiers, large-vocabulary sequence models, or fine-grained spatio-temporal models. 
>- Alternatively, we can specify an **implicit probabilistic model** that defines a *stochastic procedure* to *directly generate data*. Such models are the natural approach for problems in climate and weather, population genetics, and ecology, since the mechanistic understanding of such systems can be used to *directly describe the generative model*. We illustrate the difference between implicit and explicit models in Figure 26.1.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883

- [[Monte Carlo and Applications]]


### Compare with Principle of Maximum Likelihood

>[!quote]
>In most of this book, we rely on the **principle of maximum likelihood** for learning. 
>
>By maximizing the likelihood we effectively *minimize the KL divergence* between the **model** $q_{\theta}$ and the unknown true data distribution $p^{*}$, $$\min_{\theta}\,\mathbb{KL}\left( p^{*} \left\|\right. q_{\theta} \right)$$
>
>In **implicit models** we *cannot evaluate* $q_{\theta}(x)$, and thus cannot use maximum likelihood training. As implicit models provide a **sampling procedure**, we instead are searching for *learning principles* that *only use samples from the model*.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 885

- [[Maximum Likelihood Estimation]]

### Principle of Learning by Comparison

>[!important]
>The task of **learning in implicit models** is to determine, from *two sets of samples*, whether their *distributions* are *close* to each other and to quantify the distance between them. 
>- We can think of this as a ‘two sample’ or **likelihood-free approach** to **learning by comparison**. 
>- There are many ways of doing this, including using 
>	- *distributional divergences* or 
>	- *distances* through binary classification, 
>	- the *method of moments*, and 
>	- other approaches.
>	  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 885  

^1fd0d6


![[learning_by_comparison_methods.png]]

### Guiding Principles 

>[!info]
>The ideal *objective function* $\mathcal{D}(p^{*}, q)$ should satisfies the following conditions
>- $$p^{*} = \arg\min_{q}\mathcal{D}(p^{*}, q)$$
>	- Many statistical divergences and distance metrics can be used such as
>		- [[f-Divergence]]
>		- [[Renyi Divergence and Renyi Entropy]]
>		- [[Wasserstein Distance]]
>- Can be evaluated **only using samples** from the *data* $p^{*}$ and *model distribution* $q$.
>	- [[Kullback-Leibler Divergence]] cannot be evaluated only using samples.
>- Are **computationally cheap** to *evaluate*.
>	- [[Wasserstein Distance]] is hard to evaluate.

>[!important] Definition
>Let $p^{*}$ be the unknown true data distribution, and $q_{\theta}$ is a distribution from model $\mathcal{P}_{\Theta}.$
>
>The *Implicit generative model* assume that we have no access to likelihood function $\mathcal{P}_{\Theta}$ but only the real samples from $p^{*}$ and  the *synthetic samples* *generated* by $q_{\theta}$ given by 
>$$
>X\sim p^{*}, \quad X' \sim q_{\theta}
>$$
>- Due to lack of access to likelihood function, the objective function is not determined beforehand.
>
>The **principle of learning by comparison** 
>- *approximates* the desired objective function through *optimization* 
>
>by introducing a *comparison model*, often called a **discriminator** or a **critic** $D$, such that:
>$$
>\begin{align*}
>D(p^{*}, q) &= \arg\max_{\mathcal{D}}F(D, p^{*}, q) 
>\end{align*}
>$$
>where 
>- $F$ is a functional that depends on $p^{*}$ and $q$ *only through samples* $X, X'$.
>- $D$ is an *approximate objective function* for learning the model $q_{\theta}$.
>- The *maximization principle* is to make sure that the *optimal critic* can *separate* the data distribution  and model distribution.
>  
>Assume that the **discriminator** $D$ is parameterized by $\psi$. Then the learning of discriminator is given by the optimization  $$\psi^{*} := \arg\max_{\psi}F(D_{\psi}, p^{*}, q_{\theta})$$
>- For a fixed *critic* $D_{\psi^{*}}$, the model $q_{\theta}$ is learned via  $$\theta^{*} = \arg\min_{\theta}\,D_{\psi^{*}}(p^{*}, q_{\theta})$$
>- It is common to define $F$ using the expectation of (bounded continuous) functions $f$ and $g$ with respect to the data distribution and model distribution, respectively, i.e. $$F(D_{\psi}, p^{*}, q_{\theta}) :=  \mathbb{E}_{ X \sim p^{*} }\left[ f(X; \psi) \right] + \mathbb{E}_{X' \sim q_{\theta}}\left[ g(X'; \psi) \right]$$ 
>	- Assuming $$X' \sim G_{\theta}(Z), \; Z\sim p(z)$$ then $$F(D_{\psi}, p^{*}, G_{\theta}) :=  \mathbb{E}_{ X \sim p^{*} }\left[ f(X; \psi) \right] + \mathbb{E}_{Z \sim p(z)}\left[ g(G_{\theta}(Z); \psi) \right]$$ 
>	- This formulation is seen as the *variational formulation* for *optimal transport*.

^d5e48f

- [[Actor-Critic Algorithm]]
- [[Space of Bounded Continuous Function]]
- [[Variational Formulation of Optimal Transport]]
- [[Variational Representation of Wasserstein Distance]]


### Learning Discriminator 

#### Density Ratio Estimation



- [[Density Ratio Estimation via Binary Classifiers]]
- [[Noise Contrastive Estimation]]
- [[Jensen-Shannon Divergence]]

#### Variational Representation of $f$-Divergence

![[Variational Formula for f-Divergence#^9e3cf2]]

- [[f-Divergence]]
- [[Variational Formula for f-Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]

#### Wasserstein Distance and Integral Probability Metrics

![[Variational Representation of Wasserstein Distance#^7ba1e7]]

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]



- [[Integral Probability Metric between Probability Measures]]
- [[Total Variation between Measures]]


- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]



#### Moment Matching

- [[Information Projection and Moment Projection]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Exponential Family of Distributions]]


## Explanation





-----------
##  Recommended Notes and References

- [[Generative Adversarial Network]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883 - 894
- [[Deep Learning Foundations and Concepts by Bishop]] pp 533 - 544
- [[Deep Learning by Goodfellow]] pp 679, 690
