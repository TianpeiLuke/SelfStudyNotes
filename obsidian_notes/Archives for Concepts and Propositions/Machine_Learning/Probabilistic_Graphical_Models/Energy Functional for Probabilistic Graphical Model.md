---
tags:
  - concept
  - machine_learning/theory
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/theory
  - statistics/inference
keywords:
  - factorized_energy_functional
  - energy_functional
topics:
  - probabilistic_graphical_model
  - machine_learning_theory
  - machine_learning_models
  - statistics/estimation
name: Energy Functional for Probabilistic Graphical Model
date of note: 2024-10-12
---

## Concept Definition

>[!important]
>**Name**: Energy Functional for Probabilistic Graphical Model

![[Kullback-Leibler Divergence#^4f1ef4]]

![[Evidence Lower Bound#^c74005]]


>[!important] Definition
>Let $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ be a graph and $(P_{\Phi}, \mathcal{G})$ be a *probabilistic graphical model* over $\mathcal{G}$. That is, the  joint distribution  $P_{\Phi}$ with factors $\Phi := \left\{ \phi_{\alpha},\; \alpha\in I\right\}$  *factorizes over* $\mathcal{G}$, i.e. $$
> P_{\Phi}(X_{v}\,,\, v\in \mathcal{V}) = \frac{1}{Z} \tilde{P}_{\Phi} := \frac{1}{Z}\prod_{\phi\in \Phi}\phi(X_{\phi})$$ 
>where $$ \tilde{P}_{\Phi} := \prod_{\phi\in \Phi}\phi$$ is the *unnormalized distribution*, and the *domain of factor* $\phi$ is $$X_{\phi} = (X_{v}, \; v\in D_{\phi}) = \text{scope}(\phi).$$
>
>
>Define the **energy functional** for the variational distribution $Q$, or the **variational free energy**, as  
>$$
>\begin{align*}
>\mathcal{L}(Q, \Phi; \mathcal{X}) &:= \mathbb{E}_{ Q }\left[ \log \left(\frac{\tilde{P}_{\Phi}(X)}{Q(X)}\right) \right] \\[5pt]
>&= \mathbb{E}_{ Q }\left[\log \tilde{P}_{\Phi}(X) \right]  - \mathbb{E}_{ \mathcal{Q} }\left[  \log Q \right] \\[10pt]
>&= \sum_{\phi\in \Phi}\mathbb{E}_{ Q }\left[  \log(\phi) \right] + H_{Q}(X)
\end{align*}
>$$
>- The *first term* of energy functional is the **negative cross-entropy**, which is defined as the *expected (unnormalized) log-likelhood function* of $\tilde{P}_{\Phi}$ with respect to variational distribution $Q$, $$\mathbb{E}_{ Q }\left[\log \tilde{P}_{\Phi}(X) \right] = \sum_{\phi\in \Phi}\mathbb{E}_{ Q }\left[  \log(\phi) \right] := H_{ce}(Q, \tilde{P}_{\Phi})$$
>- The *second term* of energy functional is the Shanon energy of variational distribution $$H_{Q}(X) := \mathbb{E}_{ Q }\left[  -\log(Q(X)) \right]$$

^c01c98

- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Probabilistic Graphical Models]] 
- [[Cross-Entropy Loss Function]]


>[!important]
>$$
>\mathbb{KL}\left( Q \left\|\right. P_{\Phi} \right) = \log Z - \mathcal{L}(Q, \Phi; \mathcal{X}) 
>$$
>Thus the *energy functional* is the **lower bound** on the *log-partition function*
>$$
>\log Z \ge \mathcal{L}(\mathcal{Q}, \Phi; \mathcal{X}) 
>$$

- [[Kullback-Leibler Divergence]]


## Explanation

>[!info]
>Note that **KL divergence** requires us to know the log-partition function $Z$, which is intractable.
>$$
>\mathbb{KL}\left( Q \left\|\right. P_{\Phi} \right) = \log Z - \mathcal{L}(Q, \Phi; \mathcal{X}) 
>$$
>
>But the **energy functional** only need the *unnormalized distribution*, which is more convenient.


### Evidence Lower Bound

![[Evidence Lower Bound#^c74005]]

![[Evidence Lower Bound#^afb000]]

- [[Evidence Lower Bound]]


## Energy Functional for Exponential Family

>[!important] Definition
>Consider an *exponential family* $P_{\phi}$ with a collection $\phi = (\phi_{\alpha}, \alpha \in I)$ of *sufficient statistics* associated with the *cliques* of $\mathcal{G} = (\mathcal{V}, \mathcal{E})$ and natural parameters $\theta^{P}$
>- The space of all *$\phi$-exponential family* that factorizes over $\mathcal{G}$ is $$\mathscr{P} := \left\{P_{\phi} \in \mathcal{M}:  P_{\phi} \vDash \mathcal{I}(\mathcal{G}) \right\}$$ 
>- and the corresponding p.d.f. has the form $$P_{\Phi}(x; \theta^{P}) = \exp \left(\sum_{\alpha \in I} \theta^{P}_{\alpha }\,\phi_{\alpha }(x_{\alpha}) - A(\theta^{P})\right)$$ where  $A(\theta^{P})$ is the *log-partition function*, $$X_{\alpha}:= \text{scope}(\phi_{\alpha}),\; \implies\; \phi: X_{\alpha} \to \mathbb{R}$$
>- The *unnormalized distribution* $$\tilde{P}_{\Phi}(x; \theta^{P}) = \exp \left(\sum_{\alpha \in I} \theta^{P}_{\alpha }\,\phi_{\alpha }(x_{\alpha})\right)$$
>
>Define the **energy functional** for the *variational distribution* $Q_{\mu}$ in *exponential family* parameterized by mean parameter $\mu^{Q}$
>$$
>\begin{align*}
>\mathcal{L}(\mu^{Q}, \theta^{P}; \mathcal{X}) &= \mathbb{E}_{\mu}\left[\log \tilde{P}_{\Phi}(x; \theta^{P})\right]  - \mathbb{E}_{\mu}\left[  \log Q \right] \\[10pt]
>&= \sum_{\alpha \in I} \theta^{P}_{\alpha }\;\mathbb{E}_{\mu}\left[  \phi_{\alpha }(X_{\alpha}) \right]  + H(Q_{\mu}) \\[10pt]
>&= \left\langle  \mu^{Q}\,,\, \theta^{P}\right\rangle - A^{*}(\mu^{Q})
\end{align*}
>$$   
>where 
>- $\mu^{Q}$ is the *expected value of sufficient statistics* with respect to $Q$, i.e. $$\mu^{Q} = (\mathbb{E}_{Q}\left[\phi_{\alpha }(X_{\alpha}) \right], \;\; \alpha\in I)$$
>- and $A^{*}(\mu)$ is the *dual of log-partition* function $A(\theta)$, which is the *negative entropy* $$A^{*}(\mu) = -H(Q_{\mu}) = \mathbb{E}_{ \mu }\left[  \log Q_{\mu}(X) \right]$$

^144559

- [[Kullback-Leibler Divergence for Exponential Family]]
- [[Exponential Family of Distributions]]
- [[Shannon Entropy]]




-----------
##  Recommended Notes and References




- [[Log-Partition Function of Exponential Family]]
- [[Evidence Lower Bound for Exponential Family]]


- [[Mean Field Approximation for PGM]]
- [[Structured Variational Approximation]]
- [[Mean Field Approximation for Exponential Family]]
- [[Mean Field Approximation for Gaussian Markov Random Field]]

- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Variational Inference for Clique Tree]]
- [[Variational Inference Formulation of Expectation Propagation]]
- [[Variational Auto-Encoder]]



- [[Markov Network on Undirected Graph]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 385 - 386