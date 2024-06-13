---
tags:
  - concept
  - machine_learning/metrics
keywords: 
topics:
  - machine_learning_theory
name: Perplexity
date of note: 2024-04-30
---

## Concept Definition

>[!important]
>**Name**: Perplexity (PPL)
>
>Perplexity is defined as the exponentiated average negative log-likelihood of a sequence. If we have a tokenized sequence $X = (x_0, x_1, \ldots , x_t)$, then the **perplexity** of $X$ is defined as 
>$$
>PPL(X) = \exp\left\{ -\frac{1}{t} \sum_{i=1}^{t}\log p_{\theta}(x_i | x_{<i}) \right\} 
>$$ 
>where $p_{\theta}(x_i | x_{<i})$ is the *log-likelihood* of the $i$-th token *conditioned on the preceding tokens* $x_{<i}$ according to our model.


>[!important]
>In [information theory](https://en.wikipedia.org/wiki/Information_theory "Information theory"), **perplexity** is a *measure of uncertainty* in the value of a sample from a discrete probability distribution. The *larger* the perplexity, the *less likely* it is that an observer can *guess the value* which will be drawn from the distribution.


## Explanation

>[!info]
>Intuitively, it can be thought of as an evaluation of the model’s ability to *predict uniformly* among the set of *specified tokens in a corpus*.

>[!important]
>the **tokenization procedure** has a direct impact on a model’s perplexity which should always be taken into consideration when comparing different models.

>[!info]
>This is also equivalent to the *exponentiation* of *the cross-entropy* between the data and model predictions.
>$$
>\begin{align}
>\mathbf{KL}( \hat{p} || p_{\theta}) &= \sum_{X} \hat{p} \log\frac{\hat{p}}{p_{\theta}} \\
>&= - H(\hat{p}) - \sum_{x}\hat{p} \log(p_{\theta}) \\
>&\equiv - H(\hat{p}) + CE(\hat{p} || p_{\theta}) \\[15pt]
>CE(\hat{p} || p_{\theta}) &= \mathbf{KL}( \hat{p} || p_{\theta}) + H(\hat{p}) \\[5pt]
>PPL(X) &= \exp\left(CE(\hat{p} || p_{\theta}) \right)
>\end{align}
>$$

### I.I.D sample

>[!info]
>Given i.i.d samples $(x_1, \ldots, x_n)$  drawn from *unknown distribution* $p$, the *perplexity* of a *proposed model* $q$ is defined by asking how well $q$ predicts $x_i$ as
>$$
>\exp\left\{-\frac{1}{n}\sum_{i=1}^{n}\ln(q(x_i))\right\} = \left(\prod_{i=1}^{n}q(x_i)\right)^{-\frac{1}{n}}
>$$

### Standard Metric for Language Models




-----------
##  Recommended Notes and References

- [Hugging Face Perplexity](https://huggingface.co/docs/transformers/en/perplexity)
- Wikipedia [Perplexity](https://en.wikipedia.org/wiki/Perplexity)


- Jelinek, F.; Mercer, R. L.; Bahl, L. R.; Baker, J. K. (1977). ["Perplexity—a measure of the difficulty of speech recognition tasks"](https://doi.org/10.1121/1.2016299). _The Journal of the Acoustical Society of America_. **62** (S1): S63–S63. [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1121/1.2016299](https://doi.org/10.1121%2F1.2016299). [ISSN](https://en.wikipedia.org/wiki/ISSN_(identifier) "ISSN (identifier)") [0001-4966](https://www.worldcat.org/issn/0001-4966).
  
- Chen, Stanley F; Beeferman, Douglas; Rosenfeld, Roni (2018). ["Evaluation Metrics For Language Models"](https://doi.org/10.1184/R1/6605324.v1). _Carnegie Mellon University_.