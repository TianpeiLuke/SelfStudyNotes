---
tags:
  - concept
  - deep_learning/sequential_networks
  - deep_learning/models
keywords:
  - bidirectional_rnn
  - bidirectional
topics:
  - deep_learning/models
name: EMLo or Embeddings from Language Models for Word Embedding
date of note: 2024-08-31
---

## Concept Definition

>[!important]
>**Name**: EMLo or Embeddings from Language Models for Word Embedding

![[Recurrent Neural Network#^81c4ad]]

>[!important] Definition
>Let $d$ be a sequence of $n$ tokens $$d := (w^{1}\,{,}\ldots{,}\,w^{T}).$$
>- The **forward language model (LM)** factorizes the joint probability of $d$ in time forward direction $$p(d) := p(w^{1}\,{,}\ldots{,}\,w^{T}) = \prod_{t=1}^{T}p(w^{t}\,|\,w^{1} \,{,}\ldots{,}\,w^{t-1})$$
>- The **backward language model (LM)** factorizes the joint probability of $d$ in time reversal direction $$p(d) := p(w^{1}\,{,}\ldots{,}\,w^{T}) = \prod_{t=1}^{T}p(w^{t}\,|\,w^{t+1} \,{,}\ldots{,}\,w^{T})$$
>- A **bidirectional language model (biLM)** combines both *forward* and *backward* language model. It jointly maximizes the likelihood of both models as $$L:= \sum_{t=1}^{T}\left[ \log p(w^{t}\,|\,w^{1} \,{,}\ldots{,}\,w^{t-1};\;\Theta_{f}) + \log p(w^{t}\,|\,w^{t+1} \,{,}\ldots{,}\,w^{T};\;\Theta_{b} )\right] $$

- [[Autoregressive Models]]

>[!important] Definition
>**ELMo** or the **Embedding from Language Models** is based on a *bidirectional recurrent neural network*.
>- For each token $w^{k}$, a *L*-layer *bidirectional language model (biLM)* computes a set of $2L+1$ representations 
>	- For each layer:
>		- The forward representation from **forward LSTM** $$\begin{align*} h_{k}^{(f)} := ( h_{k,1}^{(f)} \,{,}\ldots{,}\,h_{k,L}^{(f)} )&=  \text{LSTM}\left(\Theta_{x}w^{k},\, \Theta_{f},\,L\right)\end{align*}$$
>		- The backward representation from **backward LSTM** $$\begin{align*} h_{k}^{(b)} := ( h_{k,1}^{(b)} \,{,}\ldots{,}\,h_{k,L}^{(b)} )&=  \text{LSTM}\left(\Theta_{x}w^{k},\, \Theta_{b},\,L\right)\end{align*}$$
>		- The *input mapping* $\Theta_{x}$ and the *output softmax mapping* $\Theta_{s}$ of both *forward and backward LSTMs* are **tied** with **shared weight**
>		- Denote that $$x_{k} := h_{0}^{(f)} = h_{0}^{(b)}$$
>	-  Collect all hidden representation in all layers into *one vector* $R_{k}$ $$R_{k} := \left\{ (h_{k,j}^{(f)}, h_{k,j}^{(b)}),\; j=0\,{,}\ldots{,}\,L \right\} $$
>- A **task specific ELMo representation** is computed by *weighting* of all biLM layers $$\text{ELMo}_{k}^{\text{task}} := E\left(R_{k}; \Theta^{\text{task}}\right) = \gamma^{\text{task}}\;\sum_{j=0}^{L}s_{j}^{\text{task}}\;(h_{k,j}^{(f)}, h_{k,j}^{(b)})$$ where $(s_{j}^{\text{task}})$ are *normalized weight*
>- For downstream task, we can either 
>	- *concatenate* **ELMO vector** with **representation vector** for token $w^{k}$ as $$[x_{k}, \; \text{ELMo}_{k}^{\text{task}}]$$ as input the task-specific RNNs.
>	- at the *output* of the RNN,  *replace* $h_{k}$ with  **ELMO vector** and $h_{k}$ passing a linear weight as $$h_{k} \leftarrow W\,[h_{k}, \; \text{ELMo}_{k}^{\text{task}}]$$


- [[Long-Short Term Memory Network or LSTM]]
- [[Bidirectional Recurrent Neural Network]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Soft Weight Sharing for Deep Learning]]


![[bidirectional_rnn.png]]


## Explanation

>[!quote]
>As the name suggests, **bidirectional RNNs** combine 
>- an RNN that *moves forward* through time, beginning from the *start* of the sequence, 
>- with another RNN that *moves backward through time*, beginning from the end of the sequence.
>
>Figure 10.11 illustrates the typical bidirectional RNN, with 
>- $h(t)$ standing for the *state* of the sub-RNN that *moves forward* through time 
>- and $g(t)$ standing for the *state* of the sub-RNN that *moves backward* through time. 
>  
>This allows the *output units* $o(t)$ to compute a *representation* that depends on **both the past and the future** but is most sensitive to the *input values* around time $t$, without having to specify a *fixed-size window* around t (as one would have to do with a feedforward network, a convolutional network, or a regular RNN with a fixed-size look-ahead buffer).
>
>-- [[Deep Learning by Goodfellow]] pp 384

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


### Compared with PLM

- [[Bidirectional Encoder Representation from Transformer or BERT]]




-----------
##  Recommended Notes and References





- [[Recurrent Neural Network]]
- [[Gated Recurrent [[Long-Short Term Memory Network or LSTM]]-Short Term Memory Network]]
- [[Residual Neural Network]]

- [[Linear Dynamic System]]
- [[Autoregressive Models]]

- [[Deep Learning by Goodfellow]] pp 383 - 384
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- [[petersDeepContextualizedWord2018]] Matthew E. Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, and Luke Zettlemoyer. 2018. [Deep Contextualized Word Representations](https://aclanthology.org/N18-1202). In _Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers)_, pages 2227–2237, New Orleans, Louisiana. Association for Computational Linguistics.
- Liu, Q., Kusner, M. J., & Blunsom, P. (2020). A survey on contextual embeddings. _arXiv preprint arXiv:2003.07278_.