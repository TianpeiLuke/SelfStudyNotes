---
tags:
  - concept
  - natural_language_processing/large_language_models
  - deep_learning/large_language_models
keywords: 
topics: 
name: Masked Language Modeling as Language Model Training Task
date of note: 2024-11-27
---

## Concept Definition

>[!important]
>**Name**: Masked Language Modeling as Language Model Training Task

>[!important] Definition
>One of two tasks to training bidirectional encoders is called **Masked Language  Modeling (MLM)**.
>- It is a *self-supervised task*, where the *training corpus* contains a large amount of *unannotated text*.
>- The model is presented with a series of sentences from the training corpus where a *random sample* of tokens from each training sequence is selected in learning task
>
>In **MLM**, a token is used in one of *three ways*:
>- It is replaced with a *special token* called `[MASK]`
>- It is replaced with *another token*, which is *randomly sampled* based on *unigram probabilities*.
>- It is left unchanged.

- [[Self-Supervised Training of Large Language Model and Teacher Forcing]]
- [[n-Gram Model and Language Model]]
- [[Large Language Model and Pretrained Language Models]]

>[!example]
>In **BERT**,
>-  *$15\%$ of the input tokens* in a training sequence are *sampled* for learning.
>- Among these,
>	- *$80\%$* are replaced with `[MASK]`,
>	- *$10\%$* are replaced by *randomly selected* tokens,
>	- *$10\%$* are left unchanged. 

^7164fd

- [[Bidirectional Encoder Representation from Transformer or BERT]]

### Masked Language Model Training

>[!important] Definition
>The **masked language model training** objective is to predict the original text for each of *masked tokens* given the *context* using the bidirectional encoder.
>
>A new layer called the **Masked Language Modeling (MLM) head** is introduced as the last layer of bidirectional encoder network.
>- The **MLM head** takes the output of last layer of *transformer*  $h_{L}^{i}$  for each *masked tokens* $w_{i}$ as inputs, i.e. $$h_{L}^{i}\in \mathbb{R}^{d}$$
>	- The $h_{L}^{i}$ is the *learned contextual embedding* of masked token $w_{i}$.
>	- The input dimension of the language modeling head is $$(T, d)$$ where $T$ is the context window length. (For BERT $T=512.$)
>- For each masked token $w_{i}$, the output of **MLM head**  is given by the *logits* $$u^{i} =  E\,h_{L}^{i} \in \mathbb{R}^{|\mathcal{V}|\times 1}$$ where  $E\in \mathbb{R}^{|\mathcal{V}|\times d}$ is the *unembedding layer*.
>	- Each logit bit $u_{j}^{i}$ is given by *cosine similarity* between the *contextual embedding*  $h_{L}^{i}$  and the input embedding of *each token* $$u_{j}^{i} := \left\langle h_{L}^{i} , E(w_{j}) \right\rangle, \quad \forall t_{j}\in \mathcal{V}$$
>- Then the *softmax function* transforms the *logits* into probabilities $$y^{i} := \text{softmax}(u^{i}) \in \Delta_{|\mathcal{V}|}$$
>	- $y^{i}$ represent the conditional distribution of masked token $w$ given the context.  $$y^{i} := p(w\,|\,h_{L}^{i}) \implies y_{j}^{i} := p(w = w_{j}\;|\;h_{L}^{i})$$ 
>	  
>Let 
>- the input sequence be $$w = (w_{1}\,{,}\ldots{,}\,w_{T}),$$
>- and the *masked sequence* be $$w_{\text{mask}},$$ where a set $M$ of tokens in $w$ is randomly selected to be masked. 
>  
>For a masked token $w_{i}\in M$, the *negative likelihood loss* of $w_{i}$ conditioned on $w_{\text{mask}}$  is given by $$L_{\text{MLM}}(w_{i}) = -\log p(w_{i}\,|\, h_{L}^{i}) := -\mathbb{1}\left\{ w = w_{i} \right\}\log p(w\,|\, h_{L}^{i})$$
>where $h_{L}$ summarizes the context of masked sequence $w_{\text{mask}}$.
>
>Thus the **cross-entropy training loss** for **masked language model (MLM)** is given by 
>$$
>\begin{align*}
>L_{\text{MLM}} := -\frac{1}{|M|} \sum_{i\in M}\mathbb{1}\left\{ w = w_{i} \right\}\log p(w\,|\, h_{L}^{i}) :=  -\frac{1}{|M|} \sum_{i\in M}\log y_{i}^{i}
\end{align*}
>$$
>where
>- $w_{i}\in M$
>- Note that *only masked tokens* $M$ are involved in the learning, and the rest are not.
>- Thus it is *sample-inefficient* to train bidirectional encoders to use the MLM.

^0229dc

- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Cosine Similarity and Cosine Distance]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Cross-Entropy Loss Function]]

>[!info]
>Suppose that the input context window size is $T$ with batch size $N$. 
>
>Then the output of **MLM Input Dense Layer** $h_{L}$ is of dimension $$(\cdot, T, d)$$
>- The contextual embedding for masked token is $h_{L}^{i}$ of dimension $(,d)$
>  
>Then the **MLM Similarity Layer** will take $h_{L}^{i}$ in the context window and output the *conditional probability* over vocabulary. 
>- The output dimension of  **MLM Similarity Layer** is $$(\cdot, T, |\mathcal{V}|)$$
>- This corresponding to a stack of $y^{i}$ for $i$ in context window.


![[masked_language_model_training.png]]

### MLM Layer






## Explanation

>[!quote]
>The **first token** of every input string is given by a special token `<class>`, and the corresponding *output* of the model is *ignored* during pre-training. 
>- Its role will become apparent when we discuss *fine-tuning*. 
>
>The model is pre-trained by presenting token sequences at the input. 
>- A *randomly chosen subset* of the tokens, say $15\%$, are *replaced* with a special token denoted `<mask>`. 
>- The model is trained to *predict the missing tokens* at the corresponding output nodes. 
>- This is analogous to the masking used in **word2vec** to learn *word embeddings*.
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 388  

>[!quote]
>The **focus** of *mask-based learning* is on predicting words from *surrounding contexts* with the goal of producing effective **word-level representations**.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 228

- [[Next Sentence Prediction as Language Model Training Task]]




-----------
##  Recommended Notes and References


- [[liuRoBERTaRobustlyOptimized2019]]
- [[devlinBERTPretrainingDeep2019]]

- [[Speech and Language Processing by Jurafsky]] pp 226 - 228
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1052
- [[Deep Learning Foundations and Concepts by Bishop]] pp 388