---
tags:
  - concept
  - natural_language_processing/tokenization
keywords:
  - word_tokenization
  - subword_tokenization
topics:
  - natural_language_processing/tokenization
name: Unigram Language Modeling as Tokenization and SentencePiece
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Unigram Language Modeling as Tokenization and SentencePiece

### Overview

![[Tokenization of Words and Subwords#^e9eebb]]

- [[Tokenization of Words and Subwords]]
- [[n-Gram Model and Language Model]]

>[!important] Definition 
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
>	- this corresponds to what we want intuitively: to *split* a *word* into the *least number of tokens* possible. $$\min\left\{ |T|:  \bigcup_{s_{i} \in T}s_{i} = C \right\}$$
>- The tokenization of a word with the Unigram model is then the tokenization with the *highest probability*.
>

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


- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]
- [[Dynamic Programming Algorithms]]
- [[Graph]]
- [[Paths in Graph and Length of Path]]

### Problem Formulation and Decoding




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
> 	- and the *score* of the *best segmentation*.
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

![[Tokenization of Words and Subwords#^217c38]]





-----------
##  Recommended Notes and References


- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Word Embedding]]
- [[Vector Space Model for Text Representation]]



- [[Speech and Language Processing by Jurafsky]] pp 21
- Kudo, T. (2018). Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates. In I. Gurevych & Y. Miyao (Eds.), _Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_ (pp. 66–75). Association for Computational Linguistics. [https://doi.org/10.18653/v1/P18-1007](https://doi.org/10.18653/v1/P18-1007)