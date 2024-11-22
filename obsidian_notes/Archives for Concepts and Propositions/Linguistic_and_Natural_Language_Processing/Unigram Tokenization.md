---
tags:
  - concept
  - natural_language_processing/tokenization
keywords:
  - word_tokenization
  - subword_tokenization
  - sentence_piece_tokenization_unigram
  - unigram_tokenization
topics:
  - natural_language_processing/tokenization
name: Unigram Tokenization and SentencePiece Tokenization
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Unigram Tokenization and SentencePiece Tokenization

### Overview

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^e9eebb]]

- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]


>[!quote]  
>Compared to BPE and WordPiece, **Unigram** works in the other direction: 
>- it starts from a *big vocabulary* 
>- and *removes* tokens from it until it reaches the desired vocabulary size.
>  
>- At each step of the training, the Unigram algorithm computes a **loss** over the corpus given the current vocabulary. 
>- Then, for *each symbol* in the *vocabulary*, the algorithm computes how much the **overall loss** would *increase* if the symbol was *removed*, 
>- and looks for the symbols that would **increase it the least**. 
>	- Those symbols have a *lower effect* on the overall loss over the corpus, so in a sense they are “*less needed*” and are the *best candidates for removal*.  
>	- Since this is expensive, we will remove $p$ percent of the symbols associated with **lowest loss increase**
>
>-- https://huggingface.co/learn/nlp-course/en/chapter6/7

>[!important] 
>- The **unigram** assume that all tokens as *independent* so $$p(w_{1}, w_{2}, w_{3}) = p(w_{1})p(w_{2})p(w_{3})$$
>	- We use the *negative log-likelihood* $$-\log p(w_{1} \,{,}\ldots{,}\,w_{n}) = -\sum_{i=1}^{n}\log p(w_{i})$$
>- tokenizations with the *least tokens possible* will have the *highest probabilities*
>	- this corresponds to what we want intuitively: to *split* a *word* into the *least number of tokens* possible.
>- The tokenization of a word with the Unigram model is then the tokenization with the *highest probability*.
>

- [[n-Gram Model and Language Model]]
- [[Multinomial Distribution]]
- [[Log-Likelihood Score Function and Fisher Score]]

>[!info]
>There are several options to use to build that **base vocabulary**: 
>- we can take the *most common substrings* in *pre-tokenized words*, for instance, 
>- or apply *BPE* on the initial corpus with a large vocabulary size.

- [[Byte-Pair Encoding or BPE Tokenization]]

>[!important]
>It is challenging to find *all possible segmentations* and *compute their probabilities* in general.
>
>One way is to via the **Viterbi algorithm**
>- build a **graph** to detect all possible segmentations of a given word
>	- a character $a \to b$ if the subword `axxxb` is *in the vocabulary*
>	- assign the *weight* $w_{a,b}$ as the *subword probability*
>- The *Viterbi algorithm* find the **path** in that graph that is going to have the *best score*

- [[Graph]]
- [[Paths in Graph and Length of Path]]

### Subword Tokenization via Iterative Algorithm

>[!important] Definition
>Consider a sequence of *subwords* $x = (x_{1} \,{,}\ldots{,}\,x_{M})$ where $x_{i}$ are statistically independent.
>- The *probability* of sequence is formulated as the product of marginal probabilies $$p(x_{1} \,{,}\ldots{,}\,x_{M}) = \prod_{i=1}^{M}p(x_{i}), \quad x_{i}\in \mathcal{V}, \forall i$$
>  
>The **most probable segmentation** $x^{*}$ is given by maximizing the joint probability of all possible segmentation 
>$$
>x^{*} = \arg\max_{x\in \mathcal{S}(C)} p(x)
>$$   
>where 
>- $\mathcal{S}(C)$ is the set of *all possible segmentation candidates* from input sentence $C$. 
>- This can be seen as a **max-product decoding problem.** We can solve it via the **Viterbi decoding.**

>[!important] Definition
>Given $\mathcal{V}$, we can estimate $p(x_{i})$ via maximizing the marginal likelihood $$\max L := \max\sum_{s=1}^{|\mathcal{D}|}\log \left(\sum_{x \in \mathcal{S}(C_{s})}p(x)\right)$$ where $\mathcal{D} = \{ C_{s}: s=1\,{,}\ldots{,}\, \}$ is the corpus with $|\mathcal{D}|$ sentences.
>
>The **unigram tokenization** estimates the *vocabulary* $\mathcal{V}$ as well as the probability $p(x)$ *iteratively* as follows 
>- Heuristically make a *reasonably big seed vocabulary* from the training corpus.
>- Repeat the following steps *until* $|\mathcal{V}|$ reaches a *desired vocabulary size*.
>	- Fixing the **vocabulary**, optimize the **joint probability** via EM algorithm $$\max L := \max\sum_{s=1}^{|\mathcal{D}|}\log \left(\sum_{x \in \mathcal{S}(C_{s})}p(x)\right)$$
>		- **M-step**: compute the *most probable segmentation* $$x^{*} = \arg\max_{x\in \mathcal{S}(C)} p(x)$$  via **Viterbi algorithm**
>		- **E-step**: given the current tokenization, *recompute* the *unigram probabilities* by counting the occurrence of all subwords in the tokenization. 
>			- Consider the *Bayesian setting* with *Directlet prior*
>	- Compute the likelihood of **reduction** of $L$ for each subword $x_{i}$ when $x_{i}$ is **removed** from $\mathcal{V}$ $$\Delta L(x_{i}) := L(\mathcal{V}) - L(\mathcal{V} - \{ x_{i} \})$$
>	- **Sort** the symbols $x_{i}$ according to $\Delta L(x_{i})$
>	- Keep **top** $\eta \%$ of *subwords*
>		- Note that we always keep the subwords consisting of a single character to avoid out-of-vocabulary.
>	 


- Kudo, T. (2018). Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates. In I. Gurevych & Y. Miyao (Eds.), _Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_ (pp. 66–75). Association for Computational Linguistics. [https://doi.org/10.18653/v1/P18-1007](https://doi.org/10.18653/v1/P18-1007)
- [[Max-Product Variable Elimination]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]
- [[Expectation-Maximization Algorithm]]
- [[Dynamic Programming Algorithms]]

### Decoding 

>[!quote]
>If all of the subwords were of the same length, this would be a classic application of the Viterbi algorithm [13]. But alas, life is not so simple. The Viterbi algorithm applies to the following problem
>> You have some hidden states $z_1 \,{,}\ldots{,}\, z_n$, and you want to transition from $z_{1} \,{\to}\ldots{\to}\,z_{n}$, and you know the _transition matrix_ $A_{i,j}$, giving the probability to go from $z_i^{(1)} \to z_j^{(2)}$, where $i$ and $j$ are the hidden state dimension, and the superscript is the sequence order. All transitions get the same $A$ matrix. You can use **Viterbi** to construct _an_ optimal path
>
>The issue is that $A$ is *not between adjacent states*. To understand how this may be a problem, let us represent a simple tokenization procedure diagrammatically.
>
>
>-- Medium blog  [SentencePiece Tokenizer Demystified](https://towardsdatascience.com/sentencepiece-tokenizer-demystified-d0a3aac19b15)

![[tokenization_trie_data_structure_sentencepiece.png]]

>[!quote]
>- The root node is the *start-of-sequence token* `<sos>`. 
>- Any time we encounter and `<end>` node, it signifies that everything in the path from `<sos>` to `<end>` is a *valid subword*. 
>- The root `<sos>` will begin with exactly *one branch for every unique character* in our subword list. 
>- As we grow the available subwords, we create *more branches* in our trie. 
>- The **Trie** is going to be the fundamental data structure that our tokenizer uses to store and retrieve subwords.
>
>-- Medium blog  [SentencePiece Tokenizer Demystified](https://towardsdatascience.com/sentencepiece-tokenizer-demystified-d0a3aac19b15)

>[!info]
>More sophisticated algorithms include 
>- the **Forward-DP Backward-A* algorithm** [15] 
>- and **Forward-Filtering and Backward-Sampling** algorithm (**FFBS**) [16].
>  
>This dynamic programming algorithm is a subset of the **sum-product message passing algorithm** in graphical model.  

- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]

- [15] Masaaki Nagata. “A stochastic japanese morphological analyzer using a forward-dp backward-a* nbest search algorithm.” In Proc. of COLING (1994).

- [16] Steven L Scott. “Bayesian methods for hidden markov models: Recursive computing in the 21st century.” Journal of the American Statistical Association (2002).


### Example Codes

```python
corpus = [
    "This is the Hugging Face Course.",
    "This chapter is about tokenization.",
    "This section shows several tokenizer algorithms.",
    "Hopefully, you will be able to understand how they are trained and generate tokens.",
]
```

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("xlnet-base-cased")
```

- Like for BPE and WordPiece, we begin by counting the number of occurrences of each word in the corpus:

```python
from collections import defaultdict

word_freqs = defaultdict(int)
for text in corpus:
    words_with_offsets = tokenizer.backend_tokenizer.pre_tokenizer.pre_tokenize_str(text)
    new_words = [word for word, offset in words_with_offsets]
    for word in new_words:
        word_freqs[word] += 1

word_freqs
```

- Then, we need to *initialize our vocabulary* to something larger than the vocab size we will want at the end. 
- We have to include all the basic characters (otherwise we won’t be able to tokenize every word), but for the bigger substrings we’ll only keep the most common ones, so we sort them by frequency:

```python
char_freqs = defaultdict(int)
subwords_freqs = defaultdict(int)
for word, freq in word_freqs.items():
    for i in range(len(word)):
        char_freqs[word[i]] += freq
        # Loop through the subwords of length at least 2
        for j in range(i + 2, len(word) + 1):
            subwords_freqs[word[i:j]] += freq

# Sort subwords by frequency
sorted_subwords = sorted(subwords_freqs.items(), key=lambda x: x[1], reverse=True)
sorted_subwords[:10]
```

```python
[('▁t', 7), ('is', 5), ('er', 5), ('▁a', 5), ('▁to', 4), ('to', 4), ('en', 4), ('▁T', 3), ('▁Th', 3), ('▁Thi', 3)]
```

- We *group* the characters with the *best subwords* to arrive at an initial vocabulary of size 300:

```python
token_freqs = list(char_freqs.items()) + sorted_subwords[: 300 - len(char_freqs)]
token_freqs = {token: freq for token, freq in token_freqs}
```

- Next, we compute the *sum of all frequencies*, to convert the frequencies into *probabilities*. 
	- For our model we will store the *logarithms of the probabilities*, because it’s more numerically stable to add logarithms than to multiply small numbers, and this will simplify the computation of the loss of the model:

```python
from math import log

total_sum = sum([freq for token, freq in token_freqs.items()])
model = {token: -log(freq / total_sum) for token, freq in token_freqs.items()}
```

>[!important]
> Now the main function is the one that tokenizes words using the **Viterbi algorithm**.
> - This algorithm computes the *best segmentation* of each *substring* of the word, which we will store in a variable named `best_segmentations`.
> - store *one dictionary per position* in the word (from 0 to its total length), with two keys: 
> 	- the index of the *start* of the *last token* in the *best segmentation*, 
> 	- and the *score* of the *best segmentation*. $$\text{BestSegmentation}[\text{start}(w_{t-1}^{*})][\text{score}]$$
> - With the index of the start of the last token, we will be able to retrieve the full segmentation once the list is completely populated.
> - Populating the list is done with just two loops: 
> 	- the *main loop* goes over *each start position*, 
> 	- and the second loop tries all *substrings beginning at that start position*. 
> - If the substring is *in the vocabulary*, we have a *new segmentation* of the word up *until that end position*, which we compare to what is in `best_segmentations`.
> - Once the *main loop* is finished, 
> 	- we just start from the end 
> 	- and *hop* from one start position to the next, 
> 	- *recording the tokens* as we go, 
> 	- until we reach the *start* of the word:


```python
def encode_word(word, model):
    best_segmentations = [{"start": 0, "score": 1}] + [
        {"start": None, "score": None} for _ in range(len(word))
    ]
    for start_idx in range(len(word)):
        # This should be properly filled by the previous steps of the loop
        best_score_at_start = best_segmentations[start_idx]["score"]
        for end_idx in range(start_idx + 1, len(word) + 1):
            token = word[start_idx:end_idx]
            if token in model and best_score_at_start is not None:
                score = model[token] + best_score_at_start
                # If we have found a better segmentation ending at end_idx, we update
                if (
                    best_segmentations[end_idx]["score"] is None
                    or best_segmentations[end_idx]["score"] > score
                ):
                    best_segmentations[end_idx] = {"start": start_idx, "score": score}

    segmentation = best_segmentations[-1]
    if segmentation["score"] is None:
        # We did not find a tokenization of the word -> unknown
        return ["<unk>"], None

    score = segmentation["score"]
    start = segmentation["start"]
    end = len(word)
    tokens = []
    while start != 0:
        tokens.insert(0, word[start:end])
        next_start = best_segmentations[start]["start"]
        end = start
        start = next_start
    tokens.insert(0, word[start:end])
    return tokens, score
```

- compute the loss

```python
def compute_loss(model):
    loss = 0
    for word, freq in word_freqs.items():
        _, word_loss = encode_word(word, model)
        loss += freq * word_loss
    return loss
```

- Computing the *scores for each token* is not very hard either; we just have to compute the loss for the models obtained by *deleting* each token:

```python
import copy


def compute_scores(model):
    scores = {}
    model_loss = compute_loss(model)
    for token, score in model.items():
        # We always keep tokens of length 1
        if len(token) == 1:
            continue
        model_without_token = copy.deepcopy(model)
        _ = model_without_token.pop(token)
        scores[token] = compute_loss(model_without_token) - model_loss
    return scores
```

- With all of this in place, the last thing we need to do is *add the special tokens* used by the model to the vocabulary, 
- then loop until we have *pruned* enough tokens from the vocabulary to reach our desired size:

```python
percent_to_remove = 0.1
while len(model) > 100:
    scores = compute_scores(model)
    sorted_scores = sorted(scores.items(), key=lambda x: x[1])
    # Remove percent_to_remove tokens with the lowest scores.
    for i in range(int(len(model) * percent_to_remove)):
        _ = token_freqs.pop(sorted_scores[i][0])

    total_sum = sum([freq for token, freq in token_freqs.items()])
    model = {token: -log(freq / total_sum) for token, freq in token_freqs.items()}
```

- Then, to *tokenize some text*, we just need to apply the pre-tokenization and then use our `encode_word()` function:

```python
def tokenize(text, model):
    words_with_offsets = tokenizer.backend_tokenizer.pre_tokenizer.pre_tokenize_str(text)
    pre_tokenized_text = [word for word, offset in words_with_offsets]
    encoded_words = [encode_word(word, model)[0] for word in pre_tokenized_text]
    return sum(encoded_words, [])


tokenize("This is the Hugging Face course.", model)
```



## Explanation

>[!info]
>The **Unigram** algorithm is often used in **SentencePiece**, which is the tokenization algorithm used by models like 
>- **AlBERT**, 
>- **T5**, 
>- **mBART**, 
>- **Big Bird**, and 
>- **XLNet**.

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^217c38]]






-----------
##  Recommended Notes and References


- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Word Embedding]]
- [[Vector Space Model in Information Retrieval]]



- [[Speech and Language Processing by Jurafsky]] pp 21
- Kudo, T. (2018). Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates. In I. Gurevych & Y. Miyao (Eds.), _Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_ (pp. 66–75). Association for Computational Linguistics. [https://doi.org/10.18653/v1/P18-1007](https://doi.org/10.18653/v1/P18-1007)
- Medium blog  [SentencePiece Tokenizer Demystified](https://towardsdatascience.com/sentencepiece-tokenizer-demystified-d0a3aac19b15)
- GIthub [Google sentencepiece](https://github.com/google/sentencepiece)