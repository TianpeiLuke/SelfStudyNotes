---
tags:
  - concept
  - DBN
  - RBM
  - probabilistic_graphical_models/models
  - deep_learning/models
  - deep_belief_network
keywords:
  - DBN
  - deep_belief_network
topics:
  - probabilistic_graphical_model
  - deep_learning/models
name: Deep Belief Network or DBN
date of note: 2025-05-04
---

## Concept Definition

>[!important]
>**Name**: Deep Belief Network or DBN

>[!important] Definition
>A **Deep Belief Network (DBN)** is a probabilistic generative model composed of multiple layers of stochastic latent variables. 
>- The top two layers have undirected, symmetric connections and form a *Restricted Boltzmann Machine (RBM)*, 
>- while the lower layers have *directed connections* towards the top. DBNs can learn a *hierarchical representation* of the input data.

- [[Restricted Boltzmann Machine or RBM]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]

### Architecture


>[!important] Definition
>A **DBN** with $L$ layers can be thought of as 
>- a *stack* of $L$ *Restricted Boltzmann Machines (RBMs)* where the hidden layer of each RBM serves as the visible layer for the next RBM in the stack.

### Joint Distribution

>[!important] Definition
>Let $v$ be the vector of visible units (input layer) and $h^{(k)}$ be the vector of hidden units in the $k$-th layer, for $k = 1, \ldots, L$.
>
>The **joint distribution** over the visible units $v$ and the hidden units $h^{(1)}, \ldots, h^{(L)}$ in a DBN can be approximated as:
>$$P(v, h^{(1)}, \ldots, h^{(L)}) = P(v | h^{(1)}) \prod_{k=1}^{L-1} P(h^{(k)} | h^{(k+1)}) P(h^{(L-1)}, h^{(L)})$$
>where:
>- $P(h^{(L-1)}, h^{(L)})$ is the *joint distribution* of the top-level *RBM*.
>- $P(h^{(k)} | h^{(k+1)})$ represents the *conditional probability* distribution of the hidden units at layer $k$ given the hidden units at layer $k+1$.
>- $P(v | h^{(1)})$ represents the conditional probability distribution of the visible units given the first hidden layer.

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]

### Training DBN via Greedy Layerwise Pre-training

>[!important] Definition
>The training of a DBN typically involves a **greedy layer-wise unsupervised learning algorithm**:
>
>- *Require*: Training data $V = \{v^{(1)}, v^{(2)}, \ldots, v^{(N)}\}$
>- *Require*: Number of hidden units for each layer $m_1, m_2, \ldots, m_L$
>- *Require*: Learning rates $\alpha_1, \alpha_2, \ldots, \alpha_L$
>- *Initialize*: Weights $W^{(k)}$, visible biases $a^{(k)}$, and hidden biases $b^{(k)}$ for each RBM layer $k=1, \ldots, L$ (e.g., with small random values)
>- **Layer-wise Pre-training:**
>	- For each layer $k = 1$ to $L$:
>		- If $k=1$, train an RBM with visible units $v$ and hidden units $h^{(1)}$ using **Contrastive Divergence (CD)** to learn parameters $$\theta^{(1)} = \{W^{(1)}, a^{(1)}, b^{(1)}\}.$$ 
>			- The learned $h^{(1)}$ activations become the input for the next layer.
>		- If $k > 1$, treat the activations of the hidden layer of the *previously trained RBM* ($h^{(k-1)}$) as the visible input for the current RBM. 
>			- Train an RBM with these visible units and hidden units $h^{(k)}$ using **CD** to learn parameters $$\theta^{(k)} = \{W^{(k)}, b^{(k-1)}, b^{(k)}\}$$ 
>				- note that the 'visible' bias for this RBM is the hidden bias of the previous layer. 
>			- The learned $h^{(k)}$ activations become the input for the next layer.
>- **Optional Supervised Fine-tuning:**
>	- If labeled data is available, an additional supervised layer (e.g., a softmax layer for classification) can be *added on top* of the DBN.
>	- The entire network (including the pre-trained layers and the new supervised layer) can then be **fine-tuned** using supervised learning algorithms like backpropagation to optimize performance on the labeled task.
>- *Return*: A deep network with learned hierarchical representations.

- [[Contrastive Divergence as Approximate Markov Chain Monte Carlo]]

## Explanation

>[!info]
>DBNs can be used for both **generative tasks** (by sampling from the learned distribution) and **discriminative tasks** (after supervised fine-tuning). 

>[!info]
>The **unsupervised pre-training** helps to initialize the network with meaningful weights, often leading to better generalization and faster convergence compared to training deep networks from random initialization.


>[!quote]
>DBNs were one of the **early effective deep learning architectures** that demonstrated the power of *unsupervised pre-training* to initialize deep networks, helping to overcome issues like *vanishing gradients* and *poor local optima*.


## DBN vs. Feedforward Network

>[!info]
>In essence, 
>- **DBNs** leverage *unsupervised learning* to find useful representations of data before potentially being fine-tuned for a specific supervised task. 
>- **MLPs**, on the other hand, are trained directly in a *supervised manner* to perform a specific mapping. 
>
>While both can be deep architectures, their fundamental building blocks and training philosophies differ significantly. 
>
>DBNs were particularly important in the *early days of deep learning* for *initializing deep networks effectively*, a challenge that MLPs faced more acutely when trained purely with backpropagation from *random initial weights*.  


| Feature             | Deep Belief Network (DBN)                                                     | Multi-Layer Perceptron (MLP)                  |
| ------------------- | ----------------------------------------------------------------------------- | --------------------------------------------- |
| **Architecture**    | *Stacked RBMs* (undirected top, directed down)                                | Feedforward with fully connected layers       |
| **Training**        | Primarily *unsupervised* (greedy layer-wise), optional supervised fine-tuning | Primarily *supervised* (backpropagation)      |
| **Learning Goal**   | Learn data distribution (generative)                                          | Learn input-output mapping (discriminative)   |
| **Initial Layers**  | Restricted Boltzmann Machines (RBMs)                                          | Standard neurons with activation functions    |
| **Connections**     | Initially learned to model data distribution                                  | Learned directly for input-output mapping     |
| **Layer Structure** | *Top undirected*, lower directed                                              | All layers typically *directed* (feedforward) |




-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]
- [[Supervised Learning and Unsupervised Learning]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]]