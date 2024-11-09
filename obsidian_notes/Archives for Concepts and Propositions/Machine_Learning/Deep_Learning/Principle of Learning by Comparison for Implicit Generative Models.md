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

^41172b

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
>	- Assuming $$X' = G_{\theta}(Z) \sim q_{\theta}(z), \; Z\sim p(z)$$ then $$F(D_{\psi}, p^{*}, G_{\theta}) :=  \mathbb{E}_{ X \sim p^{*} }\left[ f(X; \psi) \right] + \mathbb{E}_{Z \sim p(z)}\left[ g(G_{\theta}(Z); \psi) \right]$$ 
>	- This formulation is seen as the *variational formulation* for *optimal transport*.

^d5e48f

- [[Actor-Critic Algorithm]]
- [[Space of Bounded Continuous Function]]
- [[Variational Formulation of Optimal Transport]]
- [[Variational Representation of Wasserstein Distance]]


### Learning by Comparison Methods 

![[learning_by_comparison_methods.png]]

#### Density Ratio Estimation and GAN

![[Density Ratio Estimation via Binary Classifiers#^010141]]

>[!important] Definition
>We can compare two distributions $p^{*}$ and $q_{\theta}$ via **density ratio** $$r(x) = \frac{p^{*}(x)}{q(x)}$$
>
>The **density ratio estimation (DRO) trick** allows us to convert this estimate into the classification problem
>$$
>r(x) = \frac{p^{*}(x)}{q(x)} = \frac{D_{\psi}(x)}{1 - D_{\psi}(x)}
>$$
>where $D_{\psi}(x)$ is the **discriminator** or **critics**, parameterized by $\psi$.
>
>The *minimum risk* is given by
>$$
>\begin{align*}
>V(p^{*}, q_{\theta}) := \max_{\psi} \mathbb{E}_{ X,Y }\left[\ell \left( Y\,D_{\psi}(X) \right)  \right]
>\end{align*}
>$$

#### Binary Cross Entropy Loss

![[Density Ratio Estimation via Binary Classifiers#^e7d9e0]]

>[!example]
>If $\ell$ is **binary cross-entropy loss**, the learning objective becomes $$V(p^{*}, q_{\theta}) := \frac{1}{2} \left\{ \mathbb{E}_{p^{*}}\left[ \log \left(  D_{\psi}(X) \right)  \right] +  \mathbb{E}_{q_{\theta}}\left[ \log \left( 1 - D_{\psi}(X) \right) \right] \right\}  $$
>- The optimal critic is $$D_{\psi^{*}} := \frac{p^{*}}{p^{*} + q_{\theta}}$$
>- Thus the minimum risk is $$V^{*}(p^{*}, q_{\theta}) = \mathbb{D}_{JSD}\left( p^{*} \left\|\right. q_{\theta} \right) - \log(2).$$
>- As a result, the generative model parameter $\theta$ can be learned by minimizing the **Jensen-Shannon divergence**  $$\begin{align*} &\min_{\theta}\mathbb{D}_{JSD}\left( p^{*} \left\|\right. q_{\theta} \right) \\[5pt] &= \min_{\theta}\max_{\psi}\left\{ \mathbb{E}_{p^{*}}\left[ \log \left(  D_{\psi}(X) \right)  \right] +  \mathbb{E}_{q_{\theta}}\left[ \log \left( 1 - D_{\psi}(X) \right) \right]  \right\} \end{align*}$$
>- This is a **min-max problem** that is defined in the original **Generative Adversarial Network**.

^b00731

- [[Density Ratio Estimation via Binary Classifiers]]
- [[Margin-based Loss Function]]
- [[Cross-Entropy Loss Function]]
- [[Jensen-Shannon Divergence]]
- [[Noise Contrastive Estimation]]
- [[Generative Adversarial Network]]  

#### Exponential Loss

![[Density Ratio Estimation via Binary Classifiers#^f9387f]]

>[!example]
>If $\ell$ is **exponential loss**, the learning objective becomes $$V(p^{*}, q_{\theta}) := \frac{1}{2} \left\{ \mathbb{E}_{p^{*}}\left[ \sqrt{ - \frac{1 - D_{\psi}(X)}{D_{\psi}(X)} } \right] +  \mathbb{E}_{q_{\theta}}\left[ \sqrt{- \frac{D_{\psi}(X)}{1 - D_{\psi}(X)}} \right] \right\}  $$
>- The optimal critic is $$D_{\psi^{*}} := \frac{1}{2} \log \left(\frac{p^{*}}{q_{\theta}}\right)$$
>- Thus the minimum risk is the **squared Hellinger distance** $$V^{*}(p^{*}, q_{\theta}) = H^2(p^{*}, q_{\theta})- 1.$$

^d327d2

- [[Exponential Loss Minimization for AdaBoost]]
- [[Hellinger Distance between Distributions]]

#### Hinge Loss

![[Density Ratio Estimation via Binary Classifiers#^9345f7]]

>[!example]
>If $\ell$ is **hinge loss**, the learning objective becomes 
>$$
>\begin{align*}
>V(p^{*}, q_{\theta}) &:= \mathbb{E}_{p^{*}}\left[ - \max\left\{ 0, 1- \log \left(\frac{D_{\psi}(X)}{1 - D_{\psi}(X)}\right) \right\}   \right]  \\[5pt]
>&+  \mathbb{E}_{q_{\theta}}\left[ - \max\left\{ 0, 1 + \log \left(\frac{D_{\psi}(X)}{1 - D_{\psi}(X)}\right) \right\}   \right] 
>\end{align*}
>$$
>- The optimal critic is $$D_{\psi^{*}} := \text{sgn}(p^{*} - q_{\theta} )$$
>- Thus the minimum risk is the **total variation** $$V^{*}(p^{*}, q_{\theta}) = \lVert  p^{*} - q_{\theta} \rVert_{TV}  - 1$$

^0909f6

- [[Hinge Loss as Surrogate Loss Function]]
- [[Total Variation between Measures]]




>[!quote]
>This establishes a connection between **optimal binary classification** and **distributional divergences**. 
>
>- By using binary classification, we were able to compute the *distributional divergence* **using only samples**, which is the important property needed for learning **implicit generative models**; 
>- as expressed in the guiding principles, we have turned an intractable estimation problem — how to estimate the JSD divergence, into an *optimization problem* — how to learn a classifier which can be used to **approximate that divergence**.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 887  


#### Lower Bound on $f$-Divergence and $f$-GAN

![[Variational Formula for f-Divergence#^9e3cf2]]

- [[f-Divergence]]
- [[Variational Formula for f-Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]

>[!important] Definition
>Let $p^{*}$ be the unknown true data distribution, and $q_{\theta}$ is a distribution from a *generative model* $\mathcal{P}_{\Theta}.$
>
>Let $X$ and $X'$ be samples generated by true data distribution $p^{*}$ and generative model* $q_{\theta}$
>$$
>X\sim p^{*}, \quad X' \sim q_{\theta}
>$$
>
>The **variational representation** of $f$-divergence gives us 
>$$
>\begin{align*}
> \mathbb{D}_{f}\left( p^{*} \left\|\right. q_{\theta} \right) &= \sup\left\{\; \mathbb{E}_{ p^{*}}\left[ g \right] - \mathbb{E}_{q_{\theta}}\left[ f^{*} \circ g \right]: \forall g: \text{ bounded, measurable on }\Omega \;\right\} 
>\end{align*}
>$$
>where
>- $f^{*}$ is the *convex conjugate* of $f$.
>- Replacing $g$ with a *class* of **discriminators** $D_{\psi}$ parameterized by $\psi$, we obtain the *lower bound* of $f$-divergence $$ \mathbb{D}_{f}\left( p^{*} \left\|\right. q_{\theta} \right) \ge \max_{\psi}\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{q_{\theta}}\left[ f^{*} \circ D_{\psi}(X') \right]\right\} $$
>
>Thus *minimizing* $f$-divergence can be seen as a **min-max problem**
>$$
>\begin{align*}
> &\min_{\theta}\mathbb{D}_{f}\left(  p^{*} \left\|\right. q_{\theta} \right) \\[8pt] 
> &\ge \min_{\theta}\max_{\psi}\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{q_{\theta}}\left[ f^{*} \circ D_{\psi}(X') \right]\right\}\\[8pt] 
> &= \min_{\theta}\max_{\psi}\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{Z \sim p(z)}\left[ f^{*} \circ D_{\psi}(g_{\theta}(Z)) \right]\right\}\\[8pt] 
>\end{align*}
>$$
>- This approach to train *implicit generative model* leads to the **$f$-GAN algorithm.**

^ebcbb0

- [[f-Generative Adversarial Network]]

#### Lower Bound on Wasserstein Distance and Wasserstein-GAN

![[Variational Representation of Wasserstein Distance#^7ba1e7]]

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]

>[!important] Definition
>Let $p^{*}$ be the unknown true data distribution, and $q_{\theta}$ is a distribution from a *generative model* $\mathcal{P}_{\Theta}.$
>
>Let $X$ and $X'$ be samples generated by true data distribution $p^{*}$ and generative model* $q_{\theta}$
>$$
>X\sim p^{*}, \quad X' \sim q_{\theta}
>$$
>
>The **variational representation** of *Wasserstein-1 distance* gives us 
>$$
>\begin{align*}
> \mathcal{W}_{1}(p^{*}, q_{\theta} ) &= \sup\left\{\; \mathbb{E}_{ p^{*}}\left[ g \right] - \mathbb{E}_{q_{\theta}}\left[ g \right]: \forall g\in \text{Lip}_{1}  \;\right\} 
>\end{align*}
>$$
>where
>- $\text{Lip}_{1}$ is the space of *Lipschitz continuous function* with *Lipschitz constant* $\lVert g \rVert_{Lip}$ at most $1$
>- Replacing $g$ with a *class* of **discriminators** $D_{\psi}$ parameterized by $\psi$, we obtain the *lower bound* of $f$-divergence $$\mathcal{W}_{1}(p^{*}, q_{\theta} )  \ge \max_{\psi: \lVert D_{\psi} \rVert_{Lip} \le 1  }\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{q_{\theta}}\left[ D_{\psi}(X') \right]\right\} $$
>
>Thus *minimizing* $f$-divergence can be seen as a **min-max problem**
>$$
>\begin{align*}
> &\min_{\theta}\mathcal{W}_{1}(p^{*}, q_{\theta} ) \\[8pt] 
> &\ge \min_{\theta}\max_{\psi: \lVert D_{\psi} \rVert_{Lip} \le 1  }\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{q_{\theta}}\left[ D_{\psi}(X') \right]\right\} \\[8pt] 
> &= \min_{\theta}\max_{\psi: \lVert D_{\psi} \rVert_{Lip} \le 1  }\left\{\; \mathbb{E}_{ p^{*}}\left[ D_{\psi}(X) \right] - \mathbb{E}_{Z\sim p(z)}\left[ D_{\psi}(g_{\theta}(Z)) \right]\right\} \\[8pt] 
>\end{align*}
>$$
>- This approach to train *implicit generative model* leads to the popular **Wasserstein-GAN algorithm**.

^a1fa42

- [[Wasserstein Generative Adversarial Network]]


#### Maximum Mean Discrepancy and Generative Matching Network 


- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 892

#### Moment Matching

>[!important]
>The generalization of *integral probability metric* is the method of **moment matching** over a set of *test statistics* $T(x)$
>$$
>\min_{\theta} \lVert  \mathbb{E}_{ p^{*} }\left[ T(X) \right]  - \mathbb{E}_{ q_{\theta} }\left[ T(X) \right] \rVert_{2}^2 
>$$

- [[Information Projection and Moment Projection]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Exponential Family of Distributions]]
- [[Score Matching and Denoising Score Matching]]




## Explanation





-----------
##  Recommended Notes and References

- [[Generative Adversarial Network]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883 - 894
- [[Deep Learning Foundations and Concepts by Bishop]] pp 533 - 544
- [[Deep Learning by Goodfellow]] pp 679, 690
