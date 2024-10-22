---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/architecture
keywords:
  - attention_mechanism_network
  - attention_network
topics:
  - deep_learning/network_block
  - deep_learning/algorithm
name: Attention Mechanism in Neural Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Attention Mechanism in Neural Network

>[!quote]
>**Transformers** represent one of the most important developments in deep learning. They are based on a processing concept called **attention**, which allows a network to *give different weights to different inputs*, with weighting coefficients that themselves *depend on the input values*, thereby capturing powerful *inductive biases* related to sequential and other forms of data.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 357

- [[Inductive Bias in Machine Learning]]

>[!info]
>Given an input vector $x\in \mathbb{R}^{d}$, a standard *feedforward layer* would transform it into a hidden vector $z\in \mathbb{R}^{d_{v}}$ by a composite of *linear mapping* $f(\cdot) = \left\langle w , \cdot \right\rangle$ and *nonlinear activation function* $\sigma$ for each coordinate component. That is,
>$$
>z^{j} = \sigma \left( \left\langle w^{j} , x \right\rangle \right),\, \quad j=1\,{,}\ldots{,}\,d_{v}
>$$
>or in matrix form for $n$ inputs
>$$
>Z = \sigma \left( X\,W^{T}\right)
>$$
>where  
>- $X = [x_{1}\,{,}\ldots{,}\,x_{n}]^{T}\in \mathbb{R}^{n\times d}$, 
>- and  $W = [w^{1}\,{,}\ldots{,}\,w^{d_{v}}]^{T} \in \mathbb{R}^{d_{v}\times d}$
>
>The idea of **attention** is to allow the weight matrix $W$ to *depend on the inputs* $X$ as 
>$$
>Z =  X\,W(X)^{T}
>$$
>- This mechanism provides a **multiplicative interaction**. 
>- For instance when $$W(X) = V^{T}X \implies Z =  \left(X\,X^{T}\right)V $$ i.e.  $$w^{j} = v^{j}\,x_{j}\; \implies z^{j} =  \left\langle x_{j} , x \right\rangle\,v^{j},\, \quad j=1\,{,}\ldots{,}\,d_{v}$$

- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Activation Functions for Deep Learning]]

### Scaled Dot-Product Attention based on Query-Key-Value

>[!important] Definition
>Let 
>- $q\in \mathbb{R}^{d_{k}}$ be a representation of input, called the **query**. 
>- A collection of *stored input-output representations*  $$\left\{ (k_{1},v_{1})\,{,}\ldots{,}\,(k_{m}, v_{m})\right\} \subset \mathbb{R}^{d_{k}}\times \mathbb{R}^{d_{v}}$$ is called the **key-value pairs**; where
>	- $k_{i}\in \mathbb{R}^{d_{k}}$ is the **key** 
>	- and $v_{i} \in \mathbb{R}^{d_{v}}$ is called the corresponding **value**.
>
>A **query-key-value representation** of **attention layer** is given by
>$$
>\begin{align*}
>&\text{attn}\left( q, \left\{ (k_{1}, v_{1}) \,{,}\ldots{,}\, (k_{m}, v_{m})\right\}  \right) \\[5pt]
>&:= \text{attn}(q, k_{1:m}, v_{1:m})  \\[5pt]
>&= \sum_{i=1}^{m} \alpha_{i}(k_{i} , q)\,v_{i}
>\end{align*}
>$$
>where
>- the function $$\alpha_{i}(k_{i} , q) \in [0,1]$$ is called the **attention weight**. We require $\sum_i \alpha_{i}(k_{i} , q) = 1.$ 
>- A common choice for *attention weight* is the **softmax function**  $$\alpha_{i}(k_{i} , q) := \text{softmax}\left( \left\langle k_{i} , q \right\rangle / \sqrt{ d_{k} } \right) = \frac{\exp(\left\langle k_{i} , q \right\rangle / \sqrt{ d_{k} })}{\sum_{i=1}^{m}\exp(\left\langle k_{i} , q \right\rangle / \sqrt{ d_{k} })}$$  
>- Here the **attention score function** is the *scaled dot-product score* $$a(k_{i}, q) :=\frac{\left\langle k_{i} , q \right\rangle}{\sqrt{ d_{k} }},$$ and the multiplicative factor $1 / \sqrt{ d_{k} }$ is to reduce dependency on dimensionality.
>- The corresponding attention is also called the **scaled dot-product attention.**
>
>All of key, value, query representation can be **learned** via a *different linear mapping* of same input $$q = (W^{Q})^{T}x, \quad  k_{i} = (W^{K})^{T}x_{i},  \quad v_{i} = (W^{V})^{T}x_{i}, \quad i=1\,{,}\ldots{,}\,m$$

- [[Cosine Similarity and Cosine Distance]]
- [[Similarity Search]]

>[!important] Definition
>In the matrix form, the  **query-key-value attention** for $n$ inputs are given by 
>$$
>\begin{align*}
> Z &:= \text{attn}\left( Q, K, V  \right) \\[5pt] 
>&= \text{softmax}\left( \frac{Q\,K^{T}}{\sqrt{ d_{k} }} \right)\,V
>\end{align*}
>$$
>where 
>- the **query matrix** $Q = [q_{1}\,{,}\ldots{,}\,q_{n}]^{T} \in \mathbb{R}^{n\times d_{k}}$
>- the **key matrix** $K = [k_{1}\,{,}\ldots{,}\,k_{m}]^{T} \in \mathbb{R}^{m\times d_{k}}$
>- the **value matrix** $V = [v_{1}\,{,}\ldots{,}\,v_{m}]^{T} \in \mathbb{R}^{m\times d_{v}}$
>  
>For each query, the *output* of attention layer is
>$$
>z_{j} = \text{attn}\left( q_{j}, K, V  \right) = \sum_{i=1}^{m} \alpha_{i}(q_{j}, K)\,v_{i} \in \mathbb{R}^{d_{v}}, \quad j=1\,{,}\ldots{,}\,n
>$$
>- The attention layer described so far allows the output vectors to *attend to data-dependent patterns* of input vectors and is called an **attention head**.

- [[Softmax Function and Log-Sum-Exp Function]]


>[!important] Definition
>We can construct all *query, key and value* matrices *directly* from the design matrix $X\in \mathbb{R}^{n\times d}$ as $$Q = XW^{Q},\quad K = XW^{K},\quad V = XW^{V}$$ where
>- $$W^{Q} \in \mathbb{R}^{d\times d_{k}},\quad W^{K}\in \mathbb{R}^{d\times d_{k}},\quad W^{V} \in \mathbb{R}^{d\times d_{v}},$$
>
>This process is called **self-attention** since we use the same input to determine the query, key and values.


![[scaled_dot_product_attention.png]]

>[!quote]
>In practice we can also include **bias parameters** in these linear transformations. However, the bias parameters can be *absorbed* into the weight matrices, as we did with standard neural networks, by augmenting the data matrix $X$ with an additional column of $1$’s and by augmenting the weight matrices with an additional row of parameters to represent the biases. From now on we will treat the bias parameters as *implicit* to avoid cluttering the notation.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 365

### Masked Attention




### Multi-Head Attention

>[!important] Definition
>The **multi-head attention** extends the formulation of attention layer by introducing *additional query, key and value mapping*, each generating a new query-key-value pair.
>- It allows the network to capture *multiple pattens of attention* that are relevant *at the same time*


>[!important] Definition
>For each **attention head** $$H_{i} = \text{attn}\left( Q_{i},\, K_{i},\, V_{i} \right), \quad i=1\,{,}\ldots{,}\,h$$ where
>- the corresponding **query**, **key** and **value** matrix are $$Q_{i} = XW_{i}^{Q},\quad K_{i} = XW_{i}^{K},\quad V_{i} = XW_{i}^{V}$$ and
>- the linear mappings for given head are $$W_{i}^{Q} \in \mathbb{R}^{d\times d_{k}},\quad W_{i}^{K}\in \mathbb{R}^{d\times d_{k}},\quad W_{i}^{V} \in \mathbb{R}^{d\times d_{v}},$$
>- Each head output has dimension $$H_{i} \in \mathbb{R}^{n\times d_{v}}$$
>  
>The output of **multi-head self-attention** is the *weighted sum* of all *attention-head outputs*  
>$$
>\begin{align*}
>Z &= \text{Multi-Head-Attn}(X) \\[5pt]
>&:= \sum_{i=1}^{h}H_{i}W_{i}^{O} \\[5pt]
>&:= \text{Cat}\left[H_{1}\,{,}\ldots{,}\, H_{h} \right]\,W^{O}\,\in \mathbb{R}^{n\times d}
>\end{align*}
>$$
>where 
>- $$\text{Cat}\left[H_{1}\,{,}\ldots{,}\, H_{h} \right] \in \mathbb{R}^{n\times h d_{v}}$$
>- and $$W_{i}^{O} \in \mathbb{R}^{d_{v}\times d},\quad W^{O} = [(W_{1}^{O})^{T} \,{,}\ldots{,}\,(W_{h}^{O})^{T}]^{T} \in \mathbb{R}^{hd_{v} \times d}$$
>
>Note that $W_{i}^{O}$ is **redundant** since in the final output, the role of matrix $W_{i}^{V}$ and $W_{i}^{O}$ are combined
>$$
>\begin{align*}
>Z &= \sum_{i=1}^{h}H_{i}W_{i}^{O} \\[5pt]
>&= \sum_{i=1}^{h}\text{softmax}\left( \frac{XW_{i}^{Q}\,(W_{i}^{K})^{T}X^{T}}{\sqrt{ d_{k} }} \right)\,X\,\underbrace{ W_{i}^{V}W_{i}^{O} }_{ \text{combine} } \\[5pt]
>\end{align*}
>$$

>[!important] Definition
>In the original paper, the **multi-head attention** is formulated in terms of *three inputs*: 
>- the query matrix input , $Q_{in} \in \mathbb{R}^{n\times d}$
>- key matrix input $K_{in}\in \mathbb{R}^{n\times d}$
>- value matrix input $V_{in}\in \mathbb{R}^{n\times d}$
>  
>Then  **multi-head attention** is computed via 
>$$
>Z = \text{Multi-Head-Attn}(Q_{in}, K_{in}, V_{in}) = \text{Cat}\left[H_{1}\,{,}\ldots{,}\, H_{h} \right]\,W^{O}
>$$
>where *each head* is based on a different **linear transformed query, key, value** matrix
> $$H_{i} = \text{attn}\left( Q_{in}W_{i}^{Q},\, K_{in}W_{i}^{K},\, V_{in}W_{i}^{V} \right), \quad i=1\,{,}\ldots{,}\,h$$ and the linear maps are of dimension $$W_{i}^{Q} \in \mathbb{R}^{d\times d_{k}},\quad W_{i}^{K}\in \mathbb{R}^{d\times d_{k}},\quad W_{i}^{V} \in \mathbb{R}^{d\times d_{v}}$$ and each head has output dimension $$H_{i} \in \mathbb{R}^{n\times d_{v}}$$
>- Normally these three inputs are the same which is the input data. 
>- For **multi-head self-attention**, all inputs are the same $$Q_{in} = K_{in} = V_{in} = X.$$


![[multihead_attention.png]]


## Explanation


>[!quote]
>The fundamental concept that underpins a transformer is **attention**. This was originally developed as an *enhancement to RNNs* for machine translation (Bahdanau, Cho, and Bengio, 2014). However, Vaswani et al. (2017) later showed that significantly improved performance could be obtained by *eliminating the recurrence structure* and instead focusing **exclusively on the attention mechanism**. Today, transformers based on attention have completely superseded RNNs in almost all applications.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 358

>[!info]
>The name "**attention**" comes from the fact that the *weight function* introduces **sparisty** among *key-value pairs* for the output of each query,  depending on the **similarity** of *key* to *query*. 
>
>That is, 
>$$
>\alpha_{i}(q_{i}, K) = \text{softmax}(\left\langle k_{j} , q_{i}\right\rangle) \to \left\{\begin{array}{cl} 0 & \text{ if }\left\langle k_{i} ,  q_{j}\right\rangle \to 0 \\[5pt] 1 & \text{ if }\left\langle k_{i} ,  q_{j}\right\rangle \to \max  \end{array}\right.
>$$ 
>is a **sparse vector**.
>- The output of attention $$z_{i} = \sum_{i=1}^{n}\alpha_{i}(q_{i}, K)\,v_{i} \approx \sum_{j: k_{j} \text{ similar to }q_{i}} v_{j} $$
>- *Only a few* key-value pairs affect the output; 
>- This is interpreted as the **query "attending" to a few keys** for output.
>
>
>In **natural language processing (NLP)**, the *word embedding* allows the **semantic similarity** encoded as the *vector similarity in representation*. 
>- Thus the **attention mechanism** allows the model to *attend to a few* **keywords** in learning.

- [[Word Embedding]]
- [[Vector Space Model for Text Representation]]

>[!important] 
>The **strength** of **attention mechanism** lies in its capability to **ignore input in data dependent way** while the traditional neural network has to apply the same mechanism to all input in the same position.


### Compare to Kernel Machine and SVM

>[!important] Definition
>The formulation of **query-key-value attention** is equivalent to **kernel machines** where the output can be seen as the *weighted linear combination* of *target values* on *support vectors*
>$$
>z := f(x) = \sum_{i=1}^{m}K(x_{i}, x)\,z_{i}
>$$
>where 
>- The input corresponds to the **query.**
>- $z_{i}$ are *target values* at *support vectors*; In *attention layer*, it corresponds to the **value** of output.
>- The set of records (i.e. *support vectors*) $\left\{ x_{1} \,{,}\ldots{,}\,x_{m}\right\}$ are *stored* in the system, which are called **keys** in *attention layer*.
>- The evaluations of *kernels* $$\alpha_{i}(x_{i}, x) := K(x_{i}, x)$$ are weights that depends on similarity of the input $x$ and stored vectors $\left\{ x_{1} \,{,}\ldots{,}\,x_{m}\right\}$. These weights are called **attention weights.**

>[!info]
>The main difference between *attention mechanism* and *kernel machine* is that 
>- In **Kernel machines**, we adjust *the kernel* parameters and adjust the *set of keys* (support vectors) but **fix the embedding** of query and keys. 
>
>- But in **attention mechanism**, we *fix the kernel* and **learn the embedding**.  

- [[Support Vector Machine General with Soft-Margin Relaxation]]
- [[Representer Theorem]]
- [[Reproducing Kernel of RKHS]]


### Compare to Convolution

>[!quote]
>Compared to a **conventional neural network**, the signal paths have **multiplicative relations between activation values**. 
>- Whereas standard networks multiply activations by **fixed weights**, 
>- here the *activations* are multiplied by the **data-dependent attention coefficients**. 
>
>This means, for example, that if one of the attention coefficients is close to zero for a particular choice of input vector, the resulting signal path will *ignore* the corresponding incoming signal, which will therefore have no influence on the network outputs. By contrast, if a standard neural network learns to ignore a particular input or hidden-unit variable, it does so for *all input vectors.*
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 365 - 366

- [[Convolutional Filters]]
- [[Convolutional Neural Network]]


### Compare to LSTM and GRU

- [[Long-Short Term Memory Network]]
- [[Gated Recurrent Units in Neural Network]]


## Transformer

- [[Transformer Network]]



-----------
##  Recommended Notes and References


- [[Foundational Models for Transfer Learning]]
- [[Artificial Neural Network and Deep Learning]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 358 - 368
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 629
- [[vaswaniAttentionAllYou2017]] Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is All you Need. _Advances in Neural Information Processing Systems_, _30_. [https://proceedings.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html](https://proceedings.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html)
- [[Foundations of Computer Vision by Torralba]] pp 371 - 378
