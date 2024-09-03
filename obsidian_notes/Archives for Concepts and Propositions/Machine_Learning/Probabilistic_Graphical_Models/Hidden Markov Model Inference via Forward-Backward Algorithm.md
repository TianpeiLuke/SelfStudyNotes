---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
keywords:
  - hidden_markov_model
topics:
  - probabilistic_graphical_model
  - machine_learning_models
name: Hidden Markov Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Hidden Markov Model Inference via Forward-Backward Algorithm

![[State-Observation Models#^dc6850]]

- [[State-Observation Models]]

![[Hidden Markov Model#^f3f54e]]

- [[Hidden Markov Model]]
- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]

![[hmm.png]]

### Posterior Inference of HMM

>[!important] Definition
>Our goal is to infer the *hidden states* by computing the *posterior* over all the *hidden nodes* in the model $$\mathcal{P}(X^{(t)} | O^{(1: T)}).$$
>This is called the **smoothing distribution.**
>
>By Markov property, we can *decompose* the smoothing distribution into *two terms* by separating the observation into *past* and *future*
>$$
>\begin{align*}
>\mathcal{P}\left(X^{(t)}\;|\; O^{(1: t)},\, O^{(t+1:T)}\right) &\propto \mathcal{P}(X^{(t)}, O^{(t+1:T)}\;|\; O^{(1:t)}) \\[5pt]
>&=\mathcal{P}\left(X^{(t)}\;|\;O^{(1:t)}\right)\,\mathcal{P}\left(O^{(t+1:T)}\;|\;X^{(t)},\, O^{(1:t)}\right)  \\[5pt]
>&=\mathcal{P}\left(X^{(t)}\;|\;O^{(1:t)}\right)\,\mathcal{P}\left(O^{(t+1:T)}\;|\;X^{(t)}\right) 
>\end{align*}
>$$
>- The first proportion equality is due to *Bayes rule*.
>- The last equality is due to Markov property for observation, i.e. the current observation is *conditionally independent* from past and future observations given the current state
>- The *first term* of the decomposition above is called the **filtering distribution**, or **belief state** $$\mathcal{P}(X^{(t)}\;|\;O^{(1:t)})$$  since it is the *posterior distribution* of *current state* given all *past and present observations*.
>	- The first team can be computed in **forward pass** as it does not depend on future information.
>- The *second term* of above decomposition $$\mathcal{P}\left(O^{(t+1:T)}\;|\;X^{(t)}\right) $$ can only be computed via **backward pass**


- [[Bayes Theorem]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]

### Forward-Backward Algorithm

>[!important] Definition
>The posterior inference of HMM is called the **forward-backward (FB)  algorithm.** 
>- In the **forward pass**, we *recursively* compute the **belief state** for $t=1\,{,}\ldots{,}\,T$ $$\alpha_{t}(j) := \mathcal{P}(X^{(t)} = j\;|\;O^{(1:t)})$$ given *prior beliefs* $\alpha_{t-1}$ and *new observation* $O^{(t)}$ and transition matrix $A_{i,j}$
>	- the matrix form propagation is $$\alpha_{t} = \text{Normalize}\left(\lambda_{t} \odot \left[ A^{T}\, \alpha_{t-1} \right]\right)$$
>- In the **backward pass**, we *recursively* compute the **conditional likelihood** for $t=T, T-1\,{,}\ldots{,}\,1$ $$\beta_{t}(j) := \mathcal{P}\left(O^{(t+1:T)}\;|\;X^{(t)} = j\right)$$
>	- the matrix form update is $$\beta_{t-1} = A\left(\lambda_{t} \odot \beta_{t} \right)$$
>- Finally, we combine both terms to infer the **posterior distribution** 
>$$
>\begin{align*}
>\gamma_{t}(j) &:= \mathcal{P}\left(X^{(t)} = j\;|\; O^{(1: t)},\, O^{(t+1:T)}\right) \\[5pt]
>&\propto \mathcal{P}(X^{(t)} = j, O^{(t+1:T)}\;|\; O^{(1:t)}) \\[5pt]
>&=\mathcal{P}\left(X^{(t)} = j\;|\;O^{(1:t)}\right)\,\mathcal{P}\left(O^{(t+1:T)}\;|\;X^{(t)} = j\right) \\[5pt]
>&=\alpha_{t}(j) \, \beta_{t}(j)
>\end{align*}
>$$
>- In matrix form, $$\gamma_{t} = \text{Normalize}\left(\alpha_{t} \odot \beta_{t}\right)$$
>- Note that the forwards and backwards passes can be **computed independently**, but both need access to the *local evidence* $\mathcal{P}(O^{(t)}|X^{(t)})$.


![[forward_backward_hmm.png]]


### Forward Algorithm

>[!important] Definition
>Define the **local evidence** $$\lambda_{t}(i) := \mathcal{P}(O^{(t)}\;|\;X^{(t)} = i)$$ and denote the **Markov state transition matrix (kernel)** as  $$A_{i,j} := \mathcal{P}(X^{(t)} = j\;|\;X^{(t-1)}= i).$$
>
>The **forwards algorithm** is described as the following:
>- *Require*: the *state transition matri*x $A:= [A_{i,j}]_{i,j}$
>- *Require*: the *local evidences* $\lambda_{t}(i)$ for all $t=1\,{,}\ldots{,}\,T$, $i\in \mathcal{X}$
>- Initialize $\alpha_{0}(j)= \mathcal{P}(X^{(0)} = j)$
>- For $t=1 \,{,}\ldots{,}\,T$
>	- Compute the **prediction distribution** for each state $j\in \mathcal{X}$, $$\begin{align*}\alpha_{t|t-1}(j) &:= \mathcal{P}(X^{(t)} = j \;|\;O^{(1:t-1)}) \\[5pt] &= \sum_{i \in \mathcal{X}}\mathcal{P}(X^{(t)} = j \;|\;X^{(t-1)} = i)\, \mathcal{P}(X^{(t-1)} = i \;|\;O^{(1:t-1)}) \\[5pt] &= \sum_{i \in \mathcal{X}}\,A_{i,j}\,\alpha_{t-1}(i)\end{align*}$$
>	- Update the **belief state** using *prediction distribution* and *local evidence* for each state $j\in \mathcal{X}$ $$\begin{align*}\alpha_{t}(j) &= \frac{1}{Z_{t}}\,\mathcal{P}(O^{(t)}| X^{(t)} = j)\,\mathcal{P}\left(X^{(t)} = j\;|\;O^{(1:t-1)}\right) \\[5pt] &= \frac{1}{Z_{t}} \lambda_{t}(j)\; \alpha_{t|t-1}(j) \end{align*}$$  
>		-  the **partition function** is given by $$\begin{align*}Z_{t} &= \mathcal{P}(O^{(t)}\;|\;O^{(1:t-1)})\\[5pt] &=\sum_{j\in \mathcal{X}}\,\mathcal{P}(O^{(t)}\;|\;X^{(t)} = j)\,\mathcal{P}(X^{(t)} = j\;|\;O^{(1: t-1)}) \\[5pt] &= \sum_{j\in \mathcal{X}}\,\lambda_{t}(j)\,\alpha_{t|t-1}(j)\end{align*}$$
>		- the **matrix notation** of update is $$\begin{align*}\alpha_{t}(j)&= \frac{1}{Z_{t}} \lambda_{t}(j) \left[ \sum_{i\in \mathcal{X}}\alpha_{t-1}(i)\,A_{i,j} \right],\; \forall j\in \mathcal{X} \\[5pt] \implies \alpha_{t} &= \text{Normalize}\left(\lambda_{t} \odot \left[A^{T}\,\alpha_{t-1}\right] \right) \end{align*}$$

### Backward Recursion

>[!important] Definition
>The **backwards recursion** is described as the following:
>- *Require*: the *state transition matri*x $A:= [A_{i,j}]_{i,j}$
>- *Require*: the *local evidences* $\lambda_{t}(i)$ for all $t=1\,{,}\ldots{,}\,T$, $i\in \mathcal{X}$
>- Initialize $\beta_{T}(j) = 1$ for all $j$
>- For $t= T, T-1, \,{,}\ldots{,}\,1$:
>	- Update the **conditional likelihood** $$\begin{align*}\beta_{t-1}(i) &=  \mathcal{P}\left(O^{(t:T)}\;|\;X^{(t-1)} = i\right) \\[5pt] &= \sum_{j}\mathcal{P}(X^{(t)} = j,\, O^{(t)},\, O^{(t+1:T)} \;|\;X^{(t-1)} = i ) \\[5pt] &=  \sum_{j}\mathcal{P}(O^{(t+1:T)} \;|\;X^{(t-1)} = i,\, X^{(t)} = j,\, O^{(t)} )\; \mathcal{P}(X^{(t)} = j,\, O^{(t)} \;|\;X^{(t-1)} = i ) \\[5pt] &=  \sum_{j}\mathcal{P}(O^{(t+1:T)} \;|\;X^{(t)} = j )\; \mathcal{P}(X^{(t)} = j,\, O^{(t)} \;|\;X^{(t-1)} = i )\;\\[5pt] &=  \sum_{j}\mathcal{P}(O^{(t+1:T)} \;|\;X^{(t)} = j )\; \mathcal{P}( O^{(t)} \;|\;X^{(t)} = j,\,X^{(t-1)} = i  )\;\mathcal{P}(X^{(t)} = j\;|\;X^{(t-1)} = i )  \\[5pt] &=  \sum_{j}\mathcal{P}(O^{(t+1:T)} \;|\;X^{(t)} = j )\; \mathcal{P}( O^{(t)} \;|\;X^{(t)} = j)\;\mathcal{P}(X^{(t)} = j\;|\;X^{(t-1)} = i )  \\[5pt] &=\sum_{j\in \mathcal{X}}\,\beta_{t}(j)\,\lambda_{t}(j)\,A_{i,j}  \end{align*}$$
>		- The **matrix form** of the update $$\beta_{t-1} = A\left( \lambda_{t} \odot \beta_{t}\right)$$

## Explanation

>[!important]
>The *forward-backward algorithm* is a **sum-product belief propagation algorithm** for temporal graphical model. 

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]

>[!info]
>The *forward-backward algorithm* is a **Bayesian smoothing algorithm**.

- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]

>[!quote]
>In practice it is more numerically stable to compute the **log probabilities** $$\ell_{t}(j) = \log \mathcal{P}(y^{(t)}\,|\,x^{(t)} = j)$$ of the evidence, rather than the probabilities $$\lambda_{t}(j) = \mathcal{P}(y^{(t)}\,|\,x^{(t)} = j).$$ We can combine the state *conditional log likelihoods* $\lambda_{t}(j)$ with the *state prior* $p(x^{(t)} = j| y^{(1:t-1)})$ by using the **log-sum-exp trick**,
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 401

>[!important]
>An alternative implementation perform offline smoothing is to use **forwards filtering**/**backwards smoothing**. In this approach, we first perform the **forwards or filtering pass**, and then compute the **smoothed belief states** by working backwards,
>
>This is close to **belief update algorithm**.

- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]

## Fast Implementation

>[!quote]
>It is clear that a straightforward implementation of the **forwards-backwards algorithm** takes *$O(K^2T )$ time*, since we must perform a $K \times K$ *matrix multiplication* at each step. For some applications, such as speech recognition, $K$ is very large, so the $O(K^2)$ term becomes *prohibitive*. Fortunately, if the transition matrix is **sparse**, we can reduce this substantially. For example, in a sparse left-to-right transition matrix (e.g., Figure 9.6(a)), the algorithm *takes $O(T K)$ time*.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 402

>[!quote]
>In some cases, we can exploit *special properties* of the *state space*, even if the transition matrix is not sparse. In particular, suppose the states represent a **discretization** of an underlying **continuous state-space**, and the transition matrix has the form $$A_{i,j} \propto  \rho(x_{j} - x_{i}),$$ where $x_{i}$ is the *continuous vector* represented by state $i$ and $\rho(u)$ is some scalar cost function, such as Euclidean distance. Then one can implement the forwards-backwards algorithm *in $O(T K \log K)$ time*. The **key** is to rewrite Equation (9.5) as a **convolution**,  $$\alpha_{t|t-1}(j) = \mathcal{P}(X^{(t)} = j \,|\, O^{(1\vartheta-1)}) =  \sum_{i}\,\alpha_{t-1}(i)\,A_{i,j} = \sum_{i}\,\alpha_{t-1}(i)\,\rho(j-i)$$  and then to apply the **Fast Fourier Transform**. (A similar transformation can be applied in the backwards pass.) This is very useful for models with large state spaces.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 402

- [[Convolution Operation]]
- [[Fourier Series and Fourier Transform]]

>[!quote]
>We can also reduce inference to $O(\log T )$ time by using a **parallel prefix scan operator** that can be run efficiently on GPUs.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 402

>[!quote]
>In some cases, the **bottleneck is memory**, not time. In particular, to compute the *posteriors* $\gamma_{t}$, we must store the *fitered distributions* $\alpha_{t}$ for $t = 1 \,{,}\ldots{,}\, T$ until we do the backwards pass. It is possible to devise a simple **divide-and-conquer algorithm** that reduces the **space complexity** from $O(KT )$ to $O(K \log T )$ at the cost of increasing the *running time* from $O(K^2T )$ to $O(K^2 T \log T)$. The basic idea is to **store** $\alpha_{t}$ and $\beta_{t}$ vectors at a *logarithmic number of intermediate checkpoints*, and then recompute the missing messages on demand from these checkpoints.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 403





-----------
##  Recommended Notes and References


- [[Hidden Markov Model]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]


- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Variable Elimination]]
- [[Statistical Prediction Filtering and Smoothing for State Observation Model]]
- [[Kalman Filter Discrete-Time]]


- [[State-Observation Models]]
- [[Bayesian Filtering and Smoothing Equations for State Observation Models]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Dynamic Bayesian Network]]
- [[Markov Chain and Markov Process]]


- [[Probabilistic Graphical Models by Koller]] pp 652 - 655
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 15 - 19
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 397 - 399
- [[Deep Learning Foundations and Concepts by Bishop]] pp 480
- [[Elements of Statistical Learning by Hastie]]
- [[Artificial Intelligence Modern Approach by Russell]]