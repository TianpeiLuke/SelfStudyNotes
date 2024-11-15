---
tags:
  - concept
  - deep_learning/discriminative_models
  - deep_learning/models
  - deep_learning/sequential_networks
keywords:
  - recurrent_network
  - rnn
  - recurrent_neural_network
topics:
  - deep_learning/models
  - deep_learning/algorithm
name: Recurrent Neural Network
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Recurrent Neural Network


>[!info]
>Consider a *nonlinear dynamic system* which is described by the **recursion**
>$$
>x^{(t+1)} = f(x^{(t)}; \theta)
>$$
>where $x^{(t)}$ is the state of the system.
>
>The system can be represented as the *recursive composition* of the system function through time, e.g.
>$$
>x^{(t+1)} = f(f(x^{(t-1)}; \theta); \theta)  = f(f(f(x^{(t-2)}; \theta); \theta); \theta)
>$$ 
>*Unfolding* the equation by repeatedly applying the definition in this way has yielded an expression that does *not involve recurrence*. Such an expression can now be represented by a traditional directed acyclic computational graph.

![[recurrent_layer.png]]

>[!important] Definition
>**Recurrent neural networks**, or **RNNs** is a family of neural networks for processing sequential data.
>
>*RNN* is described by a **recurrent** equation 
>$$
>h^{(t+1)} = f(h^{(t)}, x^{(t+1)}; \theta)
>$$
>where $h^{(t)}$ is the **state** of system, and $x^{(t)}$ is the **inputs** (**control vectors**).
>
>- typical RNNs will add extra architectural features such as **output layers** that read information out of the state $h$ to make predictions.
>- the **state transition function** $f$ is defined by a neural network such as $$f(h^{(t)}, x^{(t+1)}; \theta) := \sigma \left(W_{h}\,h^{(t)} + W_{x}\,x^{(t+1)} + b\right)$$

^81c4ad

- [[Linear Dynamic System]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Autoregressive Models]]

### Unfolding the Recurrent Structure

>[!important]
>We can represent the **unbolded recurrence** after $t$ steps with a function $g^{(t)}$ as
>$$
>\begin{align*}
>h^{(t+1)} &= f(h^{(t)}, x^{(t+1)}; \theta) \\[5pt]
>&= g^{(t)}\left(x^{(t+1)},\,x^{(t)} \,{,}\ldots{,}\, x^{(1)}\right)
>\end{align*}
>$$
>- The function $g^{(t)}$ takes the *entire history* of $x$ as inputs $(x^{(t+1)} \,{,}\ldots{,}\,x^{(1)})$
>- The function $g^{(t)}$ can be **factorized** into *repeated application* of a function $f$, i.e. via **recursion**.

>[!quote]
>The **unfolding process** thus introduces two major **advantages**:  
>1. *Regardless of the sequence length*, the learned model always has the *same input size*, because it is specified in terms of transition from one state to another state, rather than specified in terms of a variable-length history of states.  
>2. It is possible to use the *same transition function* $f$ with the same parameters at every time step.
>   
>These two factors make it possible to learn a *single model* $f$ that operates on *all time steps* and *all sequence lengths*, rather than needing to learn a *separate model* $g^{(t)}$ for all possible time steps.   
>
>-- [[Deep Learning by Goodfellow]] pp 365


### Computation Graph of RNN

>[!important]
>There are two ways of drawing graph for RNN
>- **Template Graph (Folded)**: One way is to draw with a *diagram* containing one node for every component that might exist in a **physical implementation** of the model. 
>	- In this view, the network defines a *circuit* that operates in real time, with physical parts whose current state can influence their future state. For instance, the *left hand side* of the following figure.
>	- Throughout this chapter, we use a *black square* in a circuit diagram to indicate that an interaction takes place with a **delay** of a *single time step*, from the state at time $t$ to the state at time $t + 1$.
>- **Unfolded Graph**: The other way to draw the RNN is as an **unfolded computational graph**, in which each component is represented by many different variables, with *one variable per time step*, representing the state of the component at that point in time. 
>	- Each variable for each time step is drawn as a separate node of the computational graph,


![[rnn.png]]

>[!info]
>The variable on the left-hand side (e.g. $h$) is called the **template variable** since it need to *instantiated* at each time $t$ (e.g. as $h^{(t)}$)

- [[Dynamic Bayesian Network]]

### An End-to-End Sequence-to-Sequence Model

>[!example]
>We can consider the **sequence-to-sequence RNN model** described by above computation graph. It consists of several components
>- the **state transition equation** $$h^{(t)} = \sigma \left(W \,h^{(t-1)} + U\,x^{(t)} + b\right)$$
>	- in control system, $h^{(t)}$ is the **state** of system, and $x^{(t)}$ is the **control vectors**.
>- the **observation equation** $$o^{(t)} = V\,h^{(t)} + c$$
>	- $o^{(t)}$ is the **observation**
>- the **softmax layer** than transforms the observation input target prediction $$\hat{y}^{(t)} = \text{softmax}(o^{(t)})$$
>- the **objective (loss) function** that measures the loss of prediction with respect to true target $$\sum_{t=1}^{\tau}\,L(\hat{y}^{(t)}, y^{(t)})$$
>	- $y^{(t)}$ is the **target**
>	- the loss is chosen as the **negative log-likelihood** $$L(\hat{y}^{(t)}, y^{(t)}) = - \log \mathcal{P}_{\text{model}}(y^{(t)}\,|\, x^{(t)} \,{,}\ldots{,}\,x^{(1)})$$
>	- $\mathcal{P}_{\text{model}}$ is given by reading entry of $\hat{y}^{(t)}$

- [[Back-Propagation Through Time]]

### Architectures of RNN

>[!important] Definition
>Depending on the input and output dependency structure, RNN model architectures can be categorized into several classes:
> 
>- **One-to-Many:** or **One-to-Sequence**
>	- Generate a *sequence of outputs* for each single input $$x^{(t)} \to (y^{(t+s)} \,{,}\ldots{,}\,y^{(t)})$$ 
>	- Typically seen in **decoding** and *sequence generation*
>	- Example: **Image Caption**  image -> caption sentence  
>- **Many-to-One:** or **Sequence-to-One** 
>	- Provide *one output* for a sequence of inputs  $$(x^{(t)} \,{,}\ldots{,}\,x^{(t-s)}) \to y^{(t)}$$
>	- Typically used in **encoding**  and  *sequence classification* task
>	- Example: **Sentiment Analysis** sentence -> sentiment (positive / negative label)  
>- **Many-to-Many** *with delay*: or **Sequence-to-Sequence**
>	- Generate a *sequence of outputs* given a sequence of inputs  $$(x^{(t)} \,{,}\ldots{,}\,x^{(t-s)}) \to (y^{(t+s)} \,{,}\ldots{,}\,y^{(t)})$$
>	- Typically seen in **encoding-decoding** and *auto-regressive generation*
>	- Example: **Machine Translation** a sentence in English -> a sentence in Turkish  
>- **Many-to-Many** without delay: 
>	- $$(x^{(t)} \,{,}\ldots{,}\,x^{(t-s)}) \to (y^{(t)} \,{,}\ldots{,}\,y^{(t-s)})$$
>	- Typically seen in *part-of-speech*, *name entity recognition*
>	- Example: **Video Processing**: frames of video -> coordinates of bounding boxes around an object


![[rnn_sequence_one_sequence.png]]

- [[Encoder-Decoder Sequence-to-Sequence Architecture]]


## Explanation

>[!info]
>Recurrent neural network is base on the idea of **unfolding** a *recursive or recurrent computation* into a *computational graph* that has a *repetitive structure*, typically corresponding to a chain of events. Unfolding this graph results in the **sharing of parameters** across a deep network structure.

![[rnn_template.png]]

>[!info]
>RNN is an **extension** of *linear dynamic system* in [[Linear Dynamic System]]. 



## RNN as Dynamic Bayesian Network

>[!important] 
>A **recurrent neural network** can be seen as a **dynamic Bayesian network** which models the conditional dependency of output sequence $(Y^{(t)} \,{,}\ldots{,}\,Y^{(1)})$ given all histories of inputs $(X^{(t)} \,{,}\ldots{,}\,X^{(1)})$
>- For instance, if there is no direct edge from $Y^{(t-1)}$ to $Y^{(t)}$ then $$Y^{(t)} \perp Y^{(s)} \;|\; (X^{(t)} \,{,}\ldots{,}\,X^{(1)})$$

>[!important]
>- One way to interpret an RNN as a **graphical model** is to view the RNN as defining a graphical model whose structure is the **complete graph**, able to represent direct dependencies between any pair of $y$ values.
>	- The complete graph interpretation of the RNN is based on ignoring the hidden units $h^{(t)}$ by **marginalizing** them out of the model.
>	- $$\mathcal{P}(Y^{(t)} \,{,}\ldots{,}\,Y^{(1)} | X^{(t)} \,{,}\ldots{,}\,X^{(1)} ) = \sum_{h^{(t)}}\,{}\ldots{}\,\sum_{h^{(1)}}\mathcal{P}(Y^{(t)} \;|\;h^{(t)}, X^{(t)})$$
>- Another way is to consider hidden units $h^{(t)}$ as *random variables*; $$\mathcal{P}(Y^{(t)} \;|\;h^{(t)}, X^{(t)})$$
>	- Because of **parameter sharing**, the number of parameters in the RNN is $\mathcal{O}(1)$ as a function of sequence length.
>	- Incorporating the $h^{(t)}$ nodes in the graphical model **decouples the past and the future**, acting as an intermediate quantity between them.


![[rnn_dbn.png]]

- [[Dynamic Bayesian Network]]

## Gated Recurrent Neural Network

- [[Long-Short Term Memory Network]]
- [[Gated Recurrent Units in Neural Network]]



-----------
##  Recommended Notes and References


- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network]]
- [[Residual Neural Network]]
- [[Transformer Network]]


- [[Hidden Markov Model]]
- [[Markov Transition Kernel and Transition Function]]
- [[Dynamic Bayesian Network]]
- [[Artificial Neural Network and Deep Learning]]



- [[Deep Learning by Goodfellow]] pp 368 - 384
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] p36
- [[Probabilistic Graphical Models by Koller]]
- Towards Data Science [introduction-to-rnns-sequence-to-sequence-language-translation-and-attention](https://towardsdatascience.com/introduction-to-rnns-sequence-to-sequence-language-translation-and-attention-fc43ef2cc3fd)