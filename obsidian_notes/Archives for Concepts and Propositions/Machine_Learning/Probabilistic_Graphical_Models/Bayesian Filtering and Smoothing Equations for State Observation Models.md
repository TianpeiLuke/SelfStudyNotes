---
tags:
  - concept
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/sequential_models
  - statistics/signal_processing
keywords:
  - dynamic_bayesian_network
  - bayesian_filtering
  - bayesian_smoothing
topics:
  - probabilistic_graphical_model
  - statistics/signal_processing
  - dynamic_system
name: Bayesian Filtering and Smoothing Equations
date of note: 2024-09-01
---

## Concept Definition

>[!important]
>**Name**: Bayesian Filtering and Smoothing Equations for State Observation Models

![[State-Observation Models#^dc6850]]

- [[State-Observation Models]]

### Bayesian Filtering Equation


>[!important] Definition
>The **Bayes filter** is an algorithm that recursively computing the **belief state** $$\alpha_{t} := \mathcal{P}(X^{(t)}\,|\,O^{(1: t)})$$ given the prior belief from the previous step $\alpha_{t-1}$, the new observation $O^{(t)}$, and the model This is done with **sequential Bayesian updating.** 

>[!important] Definition
>The **Bayesian filtering equation** is 
>$$
>\begin{align*}
>\mathcal{P}\left(X^{(t)}\;|\; O^{(1: t)}\right) &\propto \mathcal{P}(O^{(t)}| X^{(t)})\,\mathcal{P}\left(X^{(t)}\;|\;O^{(1:t-1)}\right)  \\[5pt]
>&=\mathcal{P}(O^{(t)}| X^{(t)})\,\int_{x^{(t-1)}}\,\mathcal{P}(X^{(t)}\,|\,X^{(t-1)} = x^{(t-1)})\,\mathcal{P}(X^{(t-1)} = x^{(t-1)}\,|\,O^{(1: t-1)})\,dx^{(t-1)}
>\end{align*}
>$$
>Or
>$$
>\alpha_{t}(x^{(t)}) = \lambda_{t}(x^{(t)})\;\int_{\mathcal{X}} K(x^{(t-1)}, x^{(t)})\,\alpha_{t-1}(x^{(t-1)})\,dx^{(t-1)}
>$$
>where the **local evidence** $$\lambda_{t}(x^{(t)}) := \mathcal{P}(O^{(t)}\;|\;X^{(t)} = x^{(t)})$$

- [[Hidden Markov Model]]

>[!important] Definition
>For dynamic model, the **sequential Bayesian updating** reduces the **predict-update cycle**
>- **Prediction Step**: compute the probability of predicting the next state given observations in the past time $$\begin{align*}\alpha_{t|t-1} &= \mathcal{P}(X^{(t)}\,|\, O^{(1: t-1)} ) \\[5pt]  &= \int_{x^{(t-1)}}\,\mathcal{P}(X^{(t)}\,|\,X^{(t-1)} = x^{(t-1)})\,\mathcal{P}(X^{(t-1)} = x^{(t-1)}\,|\,O^{(1: t-1)})\,dx^{(t-1)} \\[5pt] &= \int_{x^{(t-1)}}\,K(x^{(t-1)}, X^{(t)})\,\alpha_{t-1}(x^{(t-1)})\,dx^{(t-1)} \end{align*}$$ where 
>	- the *previous belief state* is $$\alpha_{t-1}(x^{(t-1)}) := \mathcal{P}(X^{(t-1)} = x^{(t-1)}\,|\,O^{(1: t-1)})$$
>	- the transition kernel is $$K(x^{(t-1)}, X^{(t)}) = \mathcal{P}(X^{(t)}\,|\,X^{(t-1)} = x^{(t-1)})$$
>	- The above equation in *prediction step* is due to [[Chapman-Kolmogorov Equation]]
>- **Update Step**: update the current belief state using *Bayes rule* $$\begin{align*} \alpha_{t} = \mathcal{P}\left(X^{(t)}\;|\; O^{(1: t)}\right) &= \frac{1}{Z_{t}}\mathcal{P}(O^{(t)}| X^{(t)})\,\mathcal{P}\left(X^{(t)}\;|\;O^{(1:t-1)}\right)\\[5pt] &= \text{Normalize}\left(\lambda_{t}\,\alpha_{t|t-1} \right) \end{align*}$$

^1f4438

- [[Markov Transition Kernel and Transition Function]]
- [[Kalman Filter Discrete-Time]]

>[!info]
>This step is the same of **forward algorithm** for the Hidden Markov Model. 

- [[Hidden Markov Model Inference via Forward-Backward Algorithm#Forward Algorithm]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]

### Bayesian Smoothing Equation

>[!important] Definition
>The **Bayes smoothing** want to compute $$\mathcal{P}(X^{(t)}\,|\,O^{(1: T)}).$$
>
>We first perform the **forwards or filtering pass**, and then compute the **smoothed belief states** by working **backwards**, from right (time $t = T$ ) to left ($t = 1$), as we explain below. Hence this method is also called **forwards filtering backwards smoothing** or **FFBS**.


>[!info] Definition
>The **smoothed distribution** over two consecutive time is
>$$
>\begin{align*}
>\mathcal{P}\left(X^{(t)}, X^{(t+1)}\;|\; O^{(1: T)}\right) &=\mathcal{P}\left(X^{(t)}\;|\;X^{(t+1)},\, O^{(1: T)}\right)\,\mathcal{P}\left(X^{(t+1)}\;|\;O^{(1:T)}\right)  
>\end{align*}
>$$
>
>Note that the first term
>$$
>\begin{align*}
> \mathcal{P}\left(X^{(t)}\;|\;X^{(t+1)},\, O^{(1: T)}\right) &= \mathcal{P}\left(X^{(t)}\;|\;X^{(t+1)},\, O^{(1: t)},\, O^{(t+1: T)}\right)  \\[5pt]
> &= \mathcal{P}\left(X^{(t)}\;|\;X^{(t+1)},\, O^{(1: t)}\right)\\[5pt]
> &= \frac{\mathcal{P}\left(X^{(t)},\,X^{(t+1)} \;|\;O^{(1: t)}\right)}{\mathcal{P}\left(X^{(t+1)}\;|\;O^{(1: t)}\right)}\\[5pt]
> &=  \frac{\mathcal{P}\left(X^{(t)} \;|\; X^{(t+1)} \right)\,\mathcal{P}\left(X^{(t)} \;|\;O^{(1: t)}\right)}{\mathcal{P}\left(X^{(t+1)}\;|\;O^{(1: t)}\right)}
>\end{align*}
>$$
>Thus we have 
>$$
>\begin{align*}
>\mathcal{P}\left(X^{(t)}, X^{(t+1)}\;|\; O^{(1: T)}\right) &=\mathcal{P}\left(X^{(t)} \;|\;O^{(1: t)}\right)   \frac{\mathcal{P}\left(X^{(t)} \;|\; X^{(t+1)} \right)\, \mathcal{P}\left(X^{(t+1)}\;|\;O^{(1:T)}\right)\,}{\mathcal{P}\left(X^{(t+1)}\;|\;O^{(1: t)}\right)} 
>\end{align*}
>$$

>[!important] Definition
>the  **Bayesian smoothing equation** as
>$$
>\begin{align*}
>\mathcal{P}(X^{(t)}\,|\,O^{(1: T)})&= \int_{\mathcal{X}} \mathcal{P}(X^{(t)},\, X^{(t+1)} = x^{(t+1)}\,|\,O^{(1: T)})\, dx^{(t+1)} \\[5pt]
>&=\mathcal{P}\left(X^{(t)} \;|\;O^{(1: t)}\right)\,\int \left[ \frac{\mathcal{P}\left(X^{(t)} \;|\; x^{(t+1)} \right)\, \mathcal{P}\left(x^{(t+1)}\;|\;O^{(1:T)}\right)\,}{\mathcal{P}\left(x^{(t+1)}\;|\;O^{(1: t)}\right)} \right]\,  dx^{(t+1)} \\[5pt]
>&= \int \mathcal{P}(X^{(t)},\,x^{(t+1)}\;|\; O^{(1: T)})\; \frac{\mathcal{P}\left(x^{(t+1)}\;|\;O^{(1:T)}\right)\,}{\mathcal{P}\left(x^{(t+1)}\;|\;O^{(1: t)}\right)}\,  dx^{(t+1)}
>\end{align*}
>$$


## Explanation

>[!info]
>The **forward-backward algorithm** is the algorithm for Bayesian smoothing.
>

- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]


## Monte Carlo Methods and Particle Filter

- [[Sequential Importance Sampling]]
- [[Particle Filter or Sampling-Importance-Resampling]]




-----------
##  Recommended Notes and References


- [[State-Observation Models]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Particle Filter or Sampling-Importance-Resampling]]


- [[State Space Models and Nonlinear Dynamic System]]
- [[Linear Dynamic System]]
- [[Sequential Decision Process]]
- [[Dynamic Bayesian Network]]
- [[Markov Chain and Markov Process]]


- [[Probabilistic Graphical Models by Koller]] pp 653 - 655
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 355 - 357
- [[Deep Learning Foundations and Concepts by Bishop]] pp 480