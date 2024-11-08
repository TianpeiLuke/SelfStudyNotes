---
tags:
  - concept
  - deep_learning/contrastive_learning
  - deep_learning/representation_learning
keywords:
  - info_nce_loss
  - contrastive_learning
topics:
  - deep_learning/contrastive_learning
  - representation_learning
name: Information Noise Contrastive Estimation as Contrastive Learning
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: Information Noise Contrastive Estimation as Contrastive Learning

![[Contrastive Learning#^9b383a]]

![[Noise Contrastive Estimation#^f34cb8]]

>[!important] Definition
>Let $X\in \mathcal{X}$ be an *anchor point*, and a set of $n$ samples $$\mathcal{K} := \left\{ X^{+},\, X_{1}^{-} \,{,}\ldots{,}\, X_{n-1}^{-} \right\}$$ with *one positive sample* and $n-1$ *negative samples*. Assume that 
>- $$X^{+} \sim p^{+}(\cdot|X)$$
>- $$X_{i}^{-} \sim p^{-}(\cdot|X), \quad i=1\,{,}\ldots{,}\,n$$
>  
>The *conditional probability* of a sample at index $i$ of $\mathcal{K}$ is the *positive sample* is given by the Bayes rule
>$$
>p(i \,|\, X, \mathcal{K}) = \dfrac{p^{+}(X_{i} | X) \prod_{j \neq i}p^{-}(X_{j} | X)}{\sum_{m=1}^{n}p^{+}(X_{m} | X) \prod_{j \neq m}p^{-}(X_{j} | X)}
>$$
>- Assume that $$p^{-}(X_{j} | X) = \frac{1}{n}.$$ We can reformulate the above conditional distribution using the **softmax function** $$p(i \,|\, X, \mathcal{K}) = \frac{\exp \left( d(X, X_{i}) \right)}{\sum_{j=1}^{n}\exp \left( d(X, X_{j})\right)}$$ where 
>	- $$d(X, X_{i}) = \left\langle f_{\theta}(X) , f_{\theta}(X_{i}) \right\rangle$$ represent the similarity between representation $Z$ and $Z_{i}$ of sample pair $X$ and $X_{i}\in \mathcal{K}$ in *embedding space*. Here $$Z = f_{\theta}(X)$$ is the **embedding** of *samples*;
>  
>The **InfoNCE loss** or the **multiclass n-pair loss** is defined as 
>$$
>\begin{align*}
> &L_{\text{infoNCE}}(\theta)  \\[5pt]
> &= \mathbb{E}_{X, \mathcal{K}  }\left[ - \log \left\{ \frac{\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(X^{+}) \right\rangle \right)}{\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(X^{+}) \right\rangle \right) + \sum_{j=1}^{n-1}\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(X_{j}^{-}) \right\rangle \right)} \right\}   \right]
>\end{align*}
>$$   
>

^c99f51

- [[Contrastive Learning]]
- [[Noise Contrastive Estimation]]
- [[Density Ratio Estimation via Binary Classifiers]]
- [[Generalized Linear Models]]
- [[Multinomial Distribution]]
- [[Softmax Function and Log-Sum-Exp Function]]

>[!important]
>Note that the **optimal solution** for the *similarity metric* $d^{*}$
>$$
>d^{*} = \arg\min \mathbb{E}_{X, \mathcal{K}  }\left[ - \log \left\{  \frac{\exp\left( d(X, X^{+})\right) }{ \exp \left(d(X, X^{+})\right) +  \sum_{j=1}^{n-1}\exp \left( d(X, X_{j}^{-}) \right)} \right\}   \right]
>$$
>is equal to $$d(X, X^{+}) = \log p(X^{+}|X) + c(X^{+})$$

### Normalized-Temperature Cross-Entropy

>[!important] Definition
>The **normalized-temperature cross-entropy (NT-Xent) loss** with a temperature parameter $\tau$ is defined as
>$$
>\begin{align*}
> &L_{\text{NT-Xent}}(\theta)  \\[5pt]
> &= \mathbb{E}_{X, \mathcal{K}  }\left[ - \log \left\{ \frac{\exp \left( \dfrac{\left\langle f_{\theta}(X) , f_{\theta}(X^{+}) \right\rangle}{\tau\, \lVert  f_{\theta}(X) \rVert \, \lVert f_{\theta}(X^{+}) \rVert  } \right)}{\exp \left( \dfrac{\left\langle f_{\theta}(X) , f_{\theta}(X^{+}) \right\rangle}{\tau\, \lVert  f_{\theta}(X) \rVert \, \lVert f_{\theta}(X^{+}) \rVert  } \right) + \sum_{j=1}^{n-1}\exp \left( \dfrac{\left\langle f_{\theta}(X) , f_{\theta}(X_{j}^{-}) \right\rangle}{\tau\, \lVert  f_{\theta}(X) \rVert \, \lVert f_{\theta}(X_{j}^{-}) \rVert  } \right)} \right\}   \right]
>\end{align*}
>$$   

- [[Cross-Entropy Loss Function]]

## Explanation


>[!info]
>Compared to NCE loss, instead of having a *binary task* that decides whether each key is *positive or negative*, suppose we want to correctly identify and **rank the positive key** with *highest similarity* to the query in a set $\mathcal{K}$.

>[!info]
>The conditional distribution of choosing $i$-th sample as *positive sample* can be reformulated as 
>$$
>\begin{align*}
>p(i \,|\, X, \mathcal{K}) &= \dfrac{p^{+}(X_{i} | X) \prod_{j \neq i}p^{-}(X_{j} | X)}{\sum_{m=1}^{n}p^{+}(X_{m} | X) \prod_{j \neq m}p^{-}(X_{j} | X)} \\[5pt]
>&=  \dfrac{p^{+}(X_{i} | X) \frac{\prod_{j}p^{-}(X_{j} | X)}{p^{-}(X_{i} | X)}}{\sum_{m=1}^{n}p^{+}(X_{m} | X) \frac{\prod_{j}p^{-}(X_{j} | X)}{p^{-}(X_{m} | X)}} \\[5pt]
>&= \dfrac{\dfrac{p^{+}(X_{i} | X)}{p^{-}(X_{i} | X)}}{\sum_{m=1}^{n}\dfrac{p^{+}(X_{m} | X)}{p^{-}(X_{m} | X)}} \\[5pt]
>&= \dfrac{\dfrac{p^{+}(X_{i} | X)}{p^{-}(X_{i} | X)}}{\dfrac{p^{+}(X^{+} | X)}{p^{-}(X^{+} | X)} + \sum_{j=1}^{n-1}\dfrac{p^{+}(X_{j}^{-} | X)}{p^{-}(X_{j}^{-} | X)}}
>\end{align*}
>$$
>Assume that the negative sample is generated from uniform distribution $$p^{-}(X_{i} | X) = \frac{1}{n}$$ 
>Thus 
>$$
>\begin{align*}
>p(i \,|\, X, \mathcal{K}) &= \dfrac{p^{+}(X_{i} | X)}{\sum_{m=1}^{n}p^{+}(X_{m} | X)}
>\end{align*}
>$$

>[!important]
>In **InfoNCE loss**, the *negative sample distribution* is assumed to be the **noise distribution** and it is a *uniform distribution* on $n$-point $$p^{-}(\cdot|X) = p_{\text{noise}}(\cdot) = \frac{1}{n}$$
>
>The *positive sample distribution* is modeled using embedding similarity
>$$
>p^{+}(\cdot|X) = \frac{\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(\cdot) \right\rangle \right)}{Z(X)}
>$$
>where the normalization factor $Z(X)$ is cancelled when computing
>$$
> \dfrac{p^{+}(X_{i} | X)}{\sum_{m=1}^{n}p^{+}(X_{m} | X)} =  \dfrac{\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(X_{i}) \right\rangle \right)}{\sum_{m=1}^{n}\exp \left( \left\langle f_{\theta}(X) , f_{\theta}(X_{i}) \right\rangle \right)}
>$$

- [[Gibbs Measure and Energy-based Model]]

>[!quote]
>Note that the function resembles a **classification cross-entropy error function** in which the cosine similarity of the *positive pair* gives the logit for the *label class* and the cosine similarities for the *negative pairs* give the logits for the *incorrect classes*.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 191

### Triplet Loss

>[!quote]
>Unlike the **triplet loss**, which uses a hard threshold of $\epsilon$, $L_{\text{infoNCE}}$ can always be improved by *pushing negative examples further* away. Intuitively, the InfoNCE loss ensures that the *positive pair* is closer together than *any* of the $n-1$ negative pairs in the minibatch.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1057

>[!info]
>The contrastive learning via **InfoNCE loss** indicates that using additional *randomly generated samples* could help for learning the representation of the positive samples.

- [[Triplet Loss Minimization for Contrastive Learning]]

## Mutual Information

>[!info]
>The mutual information between $X$ and its positive sample $X^{+}$ is defined as 
>$$
>I(X; X^{+}) =  \mathbb{E}_{ X, X^{+} }\left[\log \left\{ \dfrac{p(X, X^{+})}{p(X)\,p(X^{+})} \right\}   \right]
>$$
>Assume that the negative sample distribution is independent from the anchor point $$p^{-}(X_{i}|X) = p(X_{i})$$
>
>The **InfoNCE loss** is 
>$$
>\begin{align*}
>& \mathbb{E}_{X, \mathcal{K} }\left[ - \log \dfrac{\dfrac{p^{+}(X^{+} | X)}{p^{-}(X^{+} | X)}}{\dfrac{p^{+}(X^{+} | X)}{p^{-}(X^{+} | X)} + \sum_{j=1}^{n-1}\dfrac{p^{+}(X_{j}^{-} | X)}{p^{-}(X_{j}^{-} | X)}}  \right] \\[5pt]
>&= \mathbb{E}_{X, \mathcal{K} }\left[ \log \left\{ 1 +  \dfrac{p^{-}(X^{+} | X)}{p^{+}(X^{+} | X)}\,\sum_{j=1}^{n-1}\dfrac{p^{+}(X_{j}^{-} | X)}{p^{-}(X_{j}^{-} | X)}  \right\}   \right]  \\[5pt]
>&\approx \mathbb{E}_{X, X^{+} }\left[ \log \left\{ 1 +  \dfrac{p^{-}(X^{+} | X)}{p^{+}(X^{+} | X)}\,(n-1) \mathbb{E}_{X_{j}\sim p^{-}}\left[ \dfrac{p^{+}(X_{j} | X)}{p^{-}(X_{j} | X)}\right]  \right\}   \right] \\[5pt]
>&= \mathbb{E}_{X, X^{+} }\left[ \log \left\{ 1 +  \dfrac{p^{-}(X^{+} | X)}{p^{+}(X^{+} | X)}\,(n-1)  \right\}   \right] \\[5pt]
>&\ge \mathbb{E}_{X, X^{+} }\left[ \log \left\{  \dfrac{p^{-}(X^{+} | X)}{p^{+}(X^{+} | X)}\,n \right\}   \right] \\[5pt]
>&= \log(n) + \mathbb{E}_{X, X^{+}}\left[ \log \left\{  \dfrac{p^{-}(X^{+} | X)p(X)}{p^{+}(X^{+} | X) p(X)} \right\}   \right] \\[5pt]
>&= \log(n) + \mathbb{E}_{X, X^{+}}\left[ \log \left\{  \dfrac{p(X^{+})p(X)}{p^{+}(X^{+} , X)} \right\}   \right] \\[5pt]
>&= \log(n) - I(X; X^{+})
>\end{align*}
>$$
>
>Note 
>$$
>\mathbb{E}_{X_{j}\sim p^{-}}\left[ \dfrac{p^{+}(X_{j} | X)}{p^{-}(X_{j} | X)}\right] = \int p^{+}(x_{j} | X) dx_{j} = 1
>$$

>[!important] 
>We have
>$$
>I(X; X^{+}) \ge \log(n) - L_{\text{InfoNCE}}
>$$
>That is, learning representation that *minimizes* the **InfoNCE loss** is equivalent to **maximizing** the **mutual information** between *anchor points* and their *positive samples*.  Hence the name **Info**NCE.
>$$
>\min_{f} L_{\text{InfoNCE}} \quad \iff \quad \max_{p^{+}} I(X; X^{+})
>$$

- [[Mutual Information]]
- [[Evidence Lower Bound]]

## Representation Learning

>[!important]
>Consider a **representation learning** problem, where $Z$ is the *representation* of $X$ and $$Z \sim p(z|X).$$ Given a pair of sample and its representation $(X, Z)$, we can generate $n-1$ additional independent *random representations* from another distribution $$Y_{i} \sim q(y), i=1\,{,}\ldots{,}\,n-1$$ and mix them with the *true representation* as a $n$ sample set $\mathcal{K}$. Denote any sample in $\mathcal{K}$ as $X_{i}$.
>
>A *good representation* $Z$ should be *most likely chosen* among the set of randomly generated samples. That is, the probability of selecting the true representation is maximum among all other choices 
>$$
>\begin{align*}
>p(X_{i} = Z \,|\, X, \mathcal{K}) &= \dfrac{p(X_{i} = Z|X) \prod_{j \neq i}q(Y_{j})}{\sum_{m=1}^{n}p(X_{m} = Z|X) \prod_{j \neq m}q(Y_{j})} \\[5pt]
>&= \frac{\frac{p(X_{i} = Z | X)}{q(Z)}}{\frac{p(X_{i} = Z | X)}{q(Z)} + \sum_{Y_{j}}\frac{p(Y_{j} | X)}{q(Y_{j})}}
>\end{align*}
>$$
>
>Note that it is commonly to choose *proposal distribution* for negative samples as the *marginal distribution of representation* $$q(z) = p(z)$$ 
>
>The **InfoNCE loss** is *bounded below* according to the following 
>$$
>\begin{align*}
>L_{\text{InfoNCE}}&=\mathbb{E}_{ X, Z, Y_{1:n-1} }\left[- \log p(X_{i} = Z \,|\, X, \mathcal{K})\right] \\[5pt] 
>&= \mathbb{E}_{ X, Z, Y_{1:n-1} }\left[\log \left\{ 1 +  \frac{q(Z)}{p(X_{i} = Z | X)}\sum_{Y_{j}}\frac{p(Y_{j} | X)}{q(Y_{j})} \right\} \right] \\[5pt]
>&\approx \mathbb{E}_{ X, Z }\left[\log \left\{ 1 +  \frac{q(Z)}{p(X_{i} = Z | X)} (n-1) \mathbb{E}_{ Y_{j} }\left[  \frac{p(Y_{j} | X)}{q(Y_{j})}\right] \right\} \right] \\[5pt]
>&\ge \mathbb{E}_{ X, Z }\left[\log \left\{\frac{q(Z)}{p(Z | X)} n  \right\} \right]  \\[5pt]
>&= \mathbb{E}_{ X, Z }\left[\log \left\{\frac{p(Z)}{p(Z | X)} n  \right\} \right] \\[5pt]
>&= \log(n) - I(X; Z)
>\end{align*}
>$$
>And the optimal similarity measure is given by $$f(x, z) = \frac{p(z|x)}{p(z)}$$
>
>In other word, the **InfoNCE loss** minimization is equivalent to the *maximization* of **mutual information** between *data* and *representation*.

- [[Mutual Information]]



## Multi-view Learning

>[!important] Definition
>Consider the **multi-view learning** case when the anchor point (query) $X\in \mathcal{X}$ but the positive and negative samples (keys) $\mathcal{K} \subset \mathcal{Y}$.
>- Define $f_{\theta}: \mathcal{X} \to \mathbb{R}^{d}$ as embedding for *query point*
>- Define $g_{\phi}: \mathcal{Y} \to \mathbb{R}^{d}$ as embedding for *keys*
>
>The **InfoNCE loss** for **multi-view learning** is given by 
>$$
>\begin{align*}
> &L_{\text{infoNCE}}(\theta, \phi)  \\[5pt]
> &= \mathbb{E}_{X, \mathcal{K}  }\left[ - \log \left\{ \frac{\exp \left( \left\langle f_{\theta}(X) , g_{\phi}(X^{+}) \right\rangle \right)}{\exp \left( \left\langle f_{\theta}(X) , g_{\phi}(X^{+}) \right\rangle \right) + \sum_{j=1}^{n-1}\exp \left( \left\langle f_{\theta}(X) , g_{\phi}(X_{j}^{-}) \right\rangle \right)} \right\}   \right]
>\end{align*}
>$$   
>
>- When applying the InfoNCE loss to parallel views that are the *same modality and dimension*, the *encoder* $f_{\theta}$ for the anchor $x$ and the positive and negative examples $g_{\phi}$ can be **shared**. $$f_{\theta} \equiv g_{\phi}$$

^56fa08

- [[Multi-view Learning]]








-----------
##  Recommended Notes and References


- [[Mutual Information]]
- [[Contrastive Learning]]
- [[Noise Contrastive Estimation]]

- [[Gibbs Measure and Energy-based Model]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Score Matching and Denoising Score Matching]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 243, 1054 - 1055
- [[Deep Learning Foundations and Concepts by Bishop]] pp 191
- Oord, A. V. D., Li, Y., & Vinyals, O. (2018). Representation learning with contrastive predictive coding. _arXiv preprint arXiv:1807.03748_.
- Poole, B., Ozair, S., Van Den Oord, A., Alemi, A., & Tucker, G. (2019, May). On variational bounds of mutual information. In _International Conference on Machine Learning_ (pp. 5171-5180). PMLR.
