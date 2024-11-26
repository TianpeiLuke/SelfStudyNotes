---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/architecture
  - deep_learning/models
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords:
  - transformer_network
  - attention_network
  - self_attention_network
topics:
  - deep_learning/network_block
  - deep_learning/models
  - deep_learning/generative_models
name: Transformer Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Transformer Network

### Transformer Block

![[Attention Mechanism in Neural Network#^332141]]

![[Attention Mechanism in Neural Network#^876ec1]] ^f6ea6a

![[Attention Mechanism in Neural Network#^a47445]]

>[!info] 
>A **transformer layer** consists of following components:
>- a *multi-head self-attention*
>- a *residual connection* that bypass the multi-head attention
>- then followed by a *layer normalization*
>  
>The resulting **transformer** function is given by 
>$$
>Z = \text{LayerNorm}\left(\, \text{Multi-Head-Attn}(X) + X \,\right)
>$$  
>- In order to use residual connection, we requires the *output dimension is the same as the input*  $$\text{Multi-Head-Attn}(X) \in \mathbb{R}^{n\times d}$$ i.e.  $W_{i}^{O} \in \mathbb{R}^{d\times d}$
>- sometimes the layer normalization is replaced by *pre-norm*, i.e. the normalization is applied in the input before attention. $$Z = \text{Multi-Head-Attn}(\,\text{LayerNorm}(X)\,) + X$$


- [[Attention Mechanism in Neural Network]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Residual Connection for Deep Learning]]
- [[Layer Normalization]]

>[!quote]
>We have seen that the **attention mechanism** 
>- creates *linear combinations* of the value vectors, which are then *linearly* combined to produce the output vectors. 
>- Also, the values are *linear functions of the input* vectors, and 
>- so we see that the **outputs** of an attention layer are constrained to be **linear combinations of the inputs**. 
>
>*Nonlinearity* does enter through the **attention weights**, and so the outputs will depend nonlinearly on the inputs via the *softmax function*, but the output vectors are still constrained to lie in the **subspace spanned by the input vectors** and this limits the expressive capabilities of the attention layer.
>
>We can *enhance* the flexibility of the transformer by post-processing the output of each layer using a standard **nonlinear neural network** with $D$ inputs and $D$ outputs,
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 369

>[!important] Definition
>Let $X\in \mathbb{R}^{n\times d}$ be a batch of $n$ samples with $d$ dimension. 
>
>A **transformer layer** represents the following function 
>$$
>\begin{align*}
>\widetilde{X} & = \text{LayerNorm}\left(\, \text{MLP}\left(Z\right) + Z \,\right) \\[5pt]
>Z &= \text{LayerNorm}\left(\, \text{Multi-Head-Attn}(X) + X \,\right)
>\end{align*}
>$$
>- A similar architecture using *pre-norm* is given by 
>$$
>\begin{align*}
>\widetilde{X} & = \text{MLP}\left(\,\text{LayerNorm}\left( Z \right)\,\right) + Z \\[5pt]
>Z &= \text{Multi-Head-Attn}(\,\text{LayerNorm}\left(X\right) \,) + X
>\end{align*}
>$$

^e9ade3


![[transformer_block.png]]

![[langugage_model_head.png]]
#### Computational Complexity

>[!important]
>The attention layer discussed so far takes a set of $n$ vectors each of length $d$ and maps them into another set of $n$ vectors having the same dimensionality. 
>
>- Thus, the inputs and outputs each have *overall dimensionality* $nd$. If we had used a standard fully connected neural network to map the input values to the output values, it would have $$O(n^2d^2)$$ **independent parameters**. 
>
>- Likewise the **computational cost** of evaluating one forward pass through such a network would also be $$O(n^2d^2).$$
>- Assume that $d_{k} \approx d_{v} \approx d$, and assume that the matrices $W_{i}^{Q}, W_{i}^{K}, W_{i}^{V}$ are *shared accross input*, there are $O(d^2)$ **independent parameters**. 
>- Since there are $n$ inputs, the number of computational steps to evaluate the *dot product* is $$O(n^2d)$$
>- We can think of a **self-attention layer** as a *sparse matrix* in which *parameters are shared* between specific *blocks* of the matrix. 
>- The subsequent neural network layer, which has  $d$ inputs and $d$ outputs, has a cost that is $O(d^2).$ Since it is shared across tokens, it has a complexity that is **linear** in $n$ , and therefore overall this layer has a cost that is $$O(n d^2).$$
>- Depending on the relative sizes of $n$ and $d$, either the **transformer layer** or the **MLP layer** may dominate the computational cost.
>	- Transformer layer is computationally more efficient than MLP layer.
>	- Many modifications are proposed to improve the efficiency.

- [[Flash Attention Mechanism for Large Language Model]]

![[transformer_cost_comp.png]]

### Positional Encoding

>[!important] Definition
>Since the linear mapping $W_{i}^{Q}, W_{i}^{K}, W_{i}^{V}$ are shared across all input tokens, the **transformer** has **permutation invariance**,
>- i.e. permuting the order of input tokens (rows of $X$) will result in permutation of outputs (rows of $\widetilde{X}$) $$\text{Transformer}(P\,X) = P\,(\text{Transformer}(X)).$$

>[!info]
>Compare to RNN, attention mechanism 
>- allows the network to learn **long range dependencies** that are not easily captured by recurrent networks such as LSTM, GRU etc.
>- It also facilitates the **massive parallel processing** which is not available from *recurrent networks* which is **sequential.**
>  
>On the other hand, i in *sequence data processing*, where the sequential position is important, attention mechanism and transformer need additional **positional encoding**  

- [[Long-Short Term Memory Network]]
- [[Gated Recurrent Units in Neural Network]]

>[!info]
>Position encoding is also needed in **diffusion networks**

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

>[!important] 
>An ideal **positional encoding** should 
>- provide a *unique representation* for *each position*, 
>- it should be *bounded*, 
>- it should *generalize to longer sequences*,
>- and it should have a *consistent* way to express the number of steps between any two input vectors *irrespective of their absolute position* because the **relative position** of tokens is often more important than the absolute position.

>[!important] Definition
>The **positional encoding** provides additional representation of the *relative position* of the input token in the entire sequence. 
>- This is critical to remedy the *lack* of dependency on **token order** in *original transformer*
>  
>In particular, it is a vector map $$r: \{ 1\,{,}\ldots{,}\,n \} \to \mathbb{R}^{d}$$ which is added to the input representation  $$\hat{x}_{n} = x_{n} + r_{n}.$$
>
>One example of such positional encoding is the **sinusoidal position encoding** introduced by Vaswani et al.
>- The $i$-th dimension of *encoding* for *$n$-th position*  is given by $$r_{n}^{i} = \left\{\begin{array}{cl}\sin \left(\dfrac{n}{L^{i / d}}\right) & \text{ if }i \text{ is even} \\[5pt] \cos \left(\dfrac{n}{L^{(i-1)/ d}}\right) & \text{ if }i \text{ is odd}\end{array}\right. \quad i=1\,{,}\ldots{,}\,d$$ 
>- One nice property of the sinusoidal representation given by (12.25) is that, for any **fixed offset** $k$, the **encoding at position** $n + k$ can be represented as a **linear combination** of the *encoding at position* $n$, in which the coefficients do not depend on the *absolute position* but only on the *value of* $k$. The network should therefore be able to learn to *attend to* **relative positions**. Note that this property requires that the encoding makes use of both sine and cosine functions.

- [[vaswaniAttentionAllYou2017]]


![[position_encoding.png]]

>[!quote]
>At first it might seem that adding position information onto the token vector would *corrupt the input vectors* and make the task of the network much more difficult. However, some intuition as to why this can work well comes from noting that **two randomly chosen uncorrelated vectors tend to be nearly orthogonal in spaces of high dimensionality**, indicating that the network is able to process the token identity information and the position information *relatively separately*. Note also that, because of the **residual connections** across every layer, the *position information does not get lost* in going from one transformer layer to the next. Moreover, due to the **linear processing layers** in the transformer, a concatenated representation has similar properties to an *additive one*.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 372

### Encoder-Decoder Transformer Network

>[!important]
>The **encoder-decoder transformer architecture** is described in the figure below:
>- Both **encoder** and **decoder** consists of *transformer layers* stacked on top of each other
>- Both **encoder** and **decoder** take *input tokens* with corresponding **embedding representation** from user
>- All inputs are *added by* **positional encoding**
>- **Encoder** transforms the input token embedding with position encoding into the **encoded representation**;
>	- The encoder is a stack of **multi-head self-attention.**
>- **Decoder** is an **autoregressive model**
>	- like the *encoder*, it consists of *multi-head self-attention*
>	- besides, each block has a **multi-head attention layer** that takes the **encoded representation** from the output of encoder as **keys and values**, and takes the output of encoder subnetwork as **query**
>	- the *decoder* is a stack of **multi-head self-attention** and **multi-head cross-attention.**
>- **Causal decoding**: To ensures that the predictions for *position* $i$ can depend only on the known outputs at positions *less than* $i$.,
>	- additional **causal masking** is present in *decoder* to avoid *positions* from attending to *subsequent positions*.
>	- Also the outputs are **shifted right** by one position 
>  
>  
>This model is proposed in [[vaswaniAttentionAllYou2017]] for **machine translation task.**  


![[transformer.png]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Encoder-Decoder Sequence-to-Sequence Architecture]]
- [[Autoregressive Models]]


## Explanation

>[!quote]
>**Transformers** represent one of the most important developments in deep learning. They are based on a processing concept called **attention**, which allows a network to *give different weights to different inputs*, with weighting coefficients that themselves *depend on the input values*, thereby capturing powerful *inductive biases* related to sequential and other forms of data.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 357




## Pretrained Large Language Models

- [[Large Language Model and Pretrained Language Models]]
- [[Foundational Models for Transfer Learning]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]


-----------
##  Recommended Notes and References



- [[Artificial Neural Network and Deep Learning]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 637
- [[Deep Learning Foundations and Concepts by Bishop]] pp 368 - 374
- [[vaswaniAttentionAllYou2017]] Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is All you Need. _Advances in Neural Information Processing Systems_, _30_. [https://proceedings.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html](https://proceedings.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html)
- [[Foundations of Computer Vision by Torralba]] pp 379 - 382
- [[Speech and Language Processing by Jurafsky]] pp 190 - 193