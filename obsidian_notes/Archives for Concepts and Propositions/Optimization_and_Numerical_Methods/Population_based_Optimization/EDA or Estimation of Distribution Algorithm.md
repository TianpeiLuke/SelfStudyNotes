---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - eda_algorithm
  - estimation_of_distribution_algorithm
topics:
  - optimization/algorithm
  - evolutionary_algorithm
name: EDA or Estimation of Distribution Algorithm
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: EDA or Estimation of Distribution Algorithm

![[Evolutionary Computation Algorithms#^ac42fa]]

![[Evolutionary Computation Algorithms#^12072d]]

- [[Evolutionary Computation Algorithms]]

>[!important] Definition
>**Estimation of distribution algorithms (EDA)** are based on the idea of replacing the creation of offspring by ‘standard’ variation operators (*recombination* and *mutation*) by a three-step process:
>- First a *graphical model* is chosen to represent the *current state* of the search in terms of the *dependencies* between variables (genes) describing a candidate solution.
>- Next the *parameters* of this model are estimated from the *current population* to create a *conditional probability distribution* over the variables.
>- Finally, offspring are created by *sampling this distribution*.

^ad5721

>[!important] Definition
>The **estimation of distribution algorithms (EDA)** generate *offsprings* based on the following steps:
>- *Initialize* population $\mathcal{S}_{0}$ with $\lambda$ random *candidate solutions*;
>- For $t= 0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- **Compute** the **fitness** for each candidate $X_{t}^{i}$ in $\mathcal{S}_{t}$, $$f(X_{t}^{i})$$
>	- **Select** a *subpopulation* $\mathcal{S}_{t}^{(s)}$ based on the *fittest* subset of the current population. $$\mathcal{S}_{t}^{(s)} = \left\{ X_{t}^{i}: f(X_{t}^{i}) \ge f(X_{t}^{(m)}) \right\}$$ where $$f(X_{t}^{(1)})  \,{\ge}\ldots{\ge}\, f(X_{t}^{(K)})$$
>	- **Model Selection**: 
>		- Create a *graph* $G = (V, E)$ based on dependencies in distribution $\mathcal{P}_{t}^{(s)}$
>	- **Model Fitting**: 
>		- Estimate parameters for a **bayesian network** $\mathcal{B} = (G, \mathcal{P}_{t}^{(s)})$ with graph $G$ and distribution $\mathcal{P}_{t}^{(s)}$ estimated from the subpopulation  $\mathcal{S}_{t}^{(s)}$
>	- **Model Sampling**:
>		- **Generate** a set of $\lambda$ candidates according to the learned *bayesian network* $\mathcal{B}$ $$X_{t+1}^{1} \,{,}\ldots{,}\,X_{t+1}^{\lambda} \sim \mathcal{B}$$
>	- Choose the *offspring population* as the generated candidates $$\mathcal{S}_{t+1} = \left\{ X_{t+1}^{1} \,{,}\ldots{,}\,X_{t+1}^{\lambda} \right\} $$

- [[Combinatorial Optimization Problem]]
- [[Probabilistic Graphical Models]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Gibbs Sampling for Graphical Model]] 
- [[Maximum Likelihood Estimation of Bayesian Network]]

![[boa_eda.png]]

### General Framework

>[!important] Definition
>Consider the *constrained optimization* problem $$\max_{x\in \mathcal{X}} f(x)$$ where $f: \mathcal{X} \to \mathbb{R}$ and $\mathcal{X}$ is discrete or continuous.
> 
>
>The **estimation of distribution algorithm (EDA)** solves an alternative related objective
>$$
>\max_{\theta}\,\log\, \mathbb{E}_{ p(x |  \theta) }\left[  f(X)\right]
>$$
>where $p(x| \theta)$ is a probability density over $\mathcal{X}$, parameterized by $\theta\in \Theta$.
>- The function also called the **log-sum-exp function** for $f=\exp(z)$  $$\text{log-sum-exp}(z) = \log\, \mathbb{E}_{ p }\left[ \exp(z) \right] \approx \max(z)$$
>- Under certain conditions, this objective is *equivalent* to the original objective.
>- For high dimensional $\mathcal{X}$, it is assumed that $p(x|\theta)$ can be *factorized* according to graph $G$. That is, it is a *probabilistic graphical model* $$\mathcal{B} := (G, p(\cdot | \theta))$$

- [[Parametric Models]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Convex Function]]
- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function and Score Function of Graphical Models]]

>[!important] Definition
>A general **estimation of distribution algorithm (EDA)** can be formulated as the following steps
>- For $t= 0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- Generate $\lambda$ samples from model $p(x|\theta)$ $$X_{t}^{1} \,{,}\ldots{,}\,X_{t}^{\lambda} \sim p(x|\hat{\theta}_{t})$$
>	- Compute the **sample weight** based on **fitness** of samples $$w_{i} := \sigma(f(X_{t}^{i}))$$ where $\sigma: \mathbb{R}\to [0,1]$  is a **monotonic shape function**
>	- Estimate the new parameter $\hat{\theta}_{t+1}$ by *maximizing* the **weighted sample expectation** of log-likelihood function $$\hat{\theta}_{t+1} \in \arg\max_{\theta\in \Theta}\; \sum_{i=1}^{\lambda}w_{i}\,\log p(X_{i}|\theta)$$

^6ffc51

- [[Sigmoid Function as Activation for Deep Learning]]
- Brookes, D., Busia, A., Fannjiang, C., Murphy, K., & Listgarten, J. (2020). A view of estimation of distribution algorithms through the lens of expectation-maximization. _Proceedings of the 2020 Genetic and Evolutionary Computation Conference Companion_, 189–190. [https://doi.org/10.1145/3377929.3389938](https://doi.org/10.1145/3377929.3389938)

>[!info]
>In vanilla EDA, the function $\sigma(x)$ is a **hard-thresholding** function
>$$
>\sigma(x) = x\;\mathbb{1}\left\{ x \ge x^{(m)} \right\}. 
>$$


>[!info]
>Note that EDA is equivalent to **minimizing the cross entropy** between the *empirical distribution* defined by *the elite population* $\mathcal{S}_{t}^{(s)}$ and the *model distribution* $p(x|\theta_{t+1})$.
>
>$$
>\begin{align*}
> \theta_{t+1} &=  \arg\min_{\theta \in \Theta} \;  \mathbb{E}_{X \sim \mathcal{S}_{t}^{(s)}}\left[- \log p(X\,|\,\theta)  \right] \\[5pt]
> &= \arg\min_{\theta \in \Theta}\; H_{ce}(\mathcal{S}_{t}^{(s)}, p(\cdot\,|\,\theta))
>\end{align*}
>$$

- [[Cross-Entropy Loss Function]]
- [[Cross-Entropy Method for EDA]]
- [[Differentiable Cross-Entropy Method]]
- [[CMA-ES or Covariance Matrix Adaptation Evolution Strategy]]


## Explanation

### Model Selection

>[!info]
>**Model selection** is the critical element in using a PGM approach to data modelling (in our case modelling a population in an EDA). In essence, it amounts to finding the *appropriate structure* to capture the *conditional (in)dependencies between variables*. In the context of genetics, and also of evolutionary computation, this process is also known as the “**Linkage Learning**” problem
>
>--  [[Introduction to Evolutionary Computing by Eiben]] pp 115

- [[I-Map and Independence Assertion]]

>[!quote]
>Historically the pattern of research in this area has progressed via permitting increasing complexity for the types of structural dependencies examined. The earliest univariate algorithms such as **PBIL** \[35\] assumed variables behaved independently. The second generation of EDAs such as **MIMIC** \[59\] and **BMDA** \[337\] selected structures from the possible pairwise interactions, and current methods such as **Bayesian Optimization algorithm (BOA)** \[336\] select structures from the set of all trees of some prespecified maximum size.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 115


>[!quote]
>Most of the discussion above has tacitly assumed **discrete combinatorial problems** and the models fitted have been **Bayesian networks**. For continuous variable problems a slightly different approach is needed to measure and describe probabilities, which is typically based on normal (Gaussian) distributions.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 115


>[!quote]
>It is straightforward to use more expressive probability models that capture dependencies between the parameters (these are known as **building blocks** in the EA literature). For example, in the case of real-valued parameters, we can use a multivariate Gaussian, $p(x) = N (x|\mu, \Sigma).$ The resulting method is called the **estimation of multivariate normal algorithm** or **EMNA**, [LL02]. (See also Section 6.7.5.)
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 305



>[!quote]
>We can also use **deep generative models** to represent the distribution over good candidates. For example, [CSF16] use *denoising autoencoders* and NADE models (Section 22.2), [Bal17] uses a DNN regressor which is then inverted using gradient descent on the inputs, [PRG17] uses *RBMs* (Section 4.3.3.2), [GSM18] uses *VAEs* (Section 21.2), etc. Such models might *take more data to fit* (and therefore more function calls), but can potentially model the probability landscape more faithfully. (Whether that translates to better optimization performance is not clear, however.)
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 305 - 306

- [[Variational Auto-Encoder]]
- [[Restricted Boltzmann Machine]]
- [[Auto-Encoder]]


>[!quote]
>the first EDA based on the theory of PGMs was called **Factorized Distribution Algorithm (FDA)** and it computed a factorization from a problem structure known apriori. In the field of **EDAs**, the term FDA was initially used to refer to *EDAs* that learned only the parameters of the probabilistic models and not the structure [98, 99, 100, 134, 145, 183]. However, the term was later also used to cover EDAs that *learn the structure from data* [81, 97, 104, 108, 109, 131, 146]. In this sense, the “FDA” and “EDA” terms were both used indistinctly to refer to the same class of algorithm. While the term “*EDA*” attempts to emphasize the role played in the algorithm by the *distribution estimation step*, the term “*FDA*” highlights that a *factorization of the distribution* is used in the estimation.
>
>-- Santana, R. (2017). Gray-box optimization and factorized distribution algorithms: where two worlds collide. _arXiv preprint arXiv:1707.03093_. pp 4


## EM Algorithm

![[Evidence Lower Bound#^c74005]]


>[!important] 
>The connection between **EDA** and **EM algorithm** can be seen as 
>$$
>\begin{align*}
> \mathcal{L}_{EDA}(\theta)&= \log  \mathbb{E}_{ p(x|\theta) }\left[ f(X) \right] \\[5pt]
> &= \log  \mathbb{E}_{ q(x) }\left[ \frac{f(X)\,p(X|\theta)}{q(X)} \right] \\[5pt]
> &\ge  \mathbb{E}_{ q(x) }\left[ \log \left(\frac{f(X)\,p(X|\theta)}{q(X)} \right) \right] \\[5pt]
> &= \mathcal{L}(q, \theta)
>\end{align*}
>$$
>where $\mathcal{L}(q, \theta)$ is the **evidence lower bound (ELBO)** or the **free energy function**.
>
>- The inequality is due to [[Jensen Inequality]].
>- The **variational gap**  between the EM algorithm and EDA is $$\mathcal{L}_{EDA}(\theta) - \mathcal{L}(q, \theta) = - \mathbb{KL}\left( q(x) \left\|\right. \tilde{p}(x|\theta) \right)$$
>- the *normalized density* $$\tilde{p}(x|\theta) := \frac{p(x|\theta)\,f(x)}{Z(\theta)}$$ with *partition function* $$Z(\theta) := \int_{\mathcal{X}}\,p(x|\theta)\,f(x)\,dx.$$
>
>We can formulate an EM-algorithm as
>- **E-step**: $$q_{t+1} = \arg\min_{q}\mathbb{KL}\left( q \left\|\right. \tilde{p}(\cdot|\theta_{t}) \right)$$
>- **M-step**: $$\theta_{t+1} = \arg\max_{\theta\in\Theta}\, \mathbb{E}_{ q_{t+1} }\left[ \log \left( p(X|\theta)\,f(X) \right) \right]$$
>  
>To see how this is equivalent to EDA, 
>- we *approximate E-step* by *sampling* $X_{t}^{1} \,{,}\ldots{,}\,X_{t}^{\lambda}$ and define the posterior density on $x$ as $$q_{t+1}(x) = \frac{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))\,\delta_{X_{t}^{i}}(x)}{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))}$$   
>- Then the *M-step* becomes 
>$$
>\begin{align*}
>\theta_{t+1} &= \arg\max_{\theta\in\Theta}\, \mathbb{E}_{ q_{t+1} }\left[ \log \left( p(X|\theta)\,f(X) \right) \right]\\[5pt]
>&= \arg\max_{\theta\in\Theta}\, \mathbb{E}_{ q_{t+1} }\left[ \log \left( p(X|\theta) \right) \right]\\[5pt]
>&= \arg\max_{\theta\in\Theta}\, \frac{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))\,\delta_{X_{t}^{i}}(x)\, \log  p(x|\theta) }{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))} \\[5pt]
>&= \arg\max_{\theta\in\Theta}\, \frac{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))\,\log p(X_{t}^{i}|\theta)}{\sum_{i=1}^{\lambda}\sigma(f(X_{t}^{i}))} \\[5pt]
>&= \arg\max_{\theta\in\Theta}\, \sum_{i=1}^{\lambda}w_{i}\,\log p\left(  X_{t}^{i}|\theta\right)
>\end{align*}
> $$

^6d994f


- [[Evidence Lower Bound]]
- [[Monte Carlo Expectation Maximization]]
- [[Variational Expectation-Maximization]]
- [[Importance Sampling]]
- [[Kullback-Leibler Divergence]]
- Brookes, D., Busia, A., Fannjiang, C., Murphy, K., & Listgarten, J. (2020). A view of estimation of distribution algorithms through the lens of expectation-maximization. _Proceedings of the 2020 Genetic and Evolutionary Computation Conference Companion_, 189–190. [https://doi.org/10.1145/3377929.3389938](https://doi.org/10.1145/3377929.3389938)



-----------
##  Recommended Notes and References


- [[Gibbs Sampling for Graphical Model]] 
- [[Probabilistic Graphical Models]]
- [[Maximum Likelihood Estimation]]

- [[Population-based Incremental Learning]]
- [[Genetic Algorithms]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]] pp 113 - 116