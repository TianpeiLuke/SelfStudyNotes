---
tags:
  - concept
  - natural_language_processing/tokenization
keywords:
  - word_tokenization
  - subword_tokenization
  - byte_pair_encoding_tokenization
topics:
  - natural_language_processing/tokenization
name: Byte-Pair Encoding Tokenization
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Byte-Pair Encoding Tokenization

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^e9eebb]]

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^e9eebb]]

- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]

>[!important]
> **Byte-Pari Encoding (BPE)**
>- The BPE token learner begins BPE with a vocabulary that is just the set of all *individual characters*.
>- It then examines the training corpus, chooses the *two symbols* that are *most frequently adjacent*
>- and adds a new merged symbol into the *vocabulary*
>- and *replaces* every adjacent given symbols in the corpus with the new merged symbol.
>- It continues to *count and merge*, creating new longer and longer character strings, *until* $k$ merges have been done creating $k$ novel tokens.
>- The resulting vocabulary consists of the *original set* of characters *plus* $k$ *new symbols*.
>- This algorithm usually run *inside words*, i.e. not merging word boundaries.
>- The *token segmenter* just runs on the merges we have learned from the training data on the test data. 
>	- It runs them *greedily*, in the order we learned them.

^b47474


>[!important] Definition
>The **training** algorithm for  **Byte-Pair Encoding (BPE)** tokenization is described as below
>- *require*: string $C$
>- *require*: number of *merges* $k$
>- **Pre-tokenization**:  initialize the vocabulary $V$ with all *unique single characters* in $C$ $$V \leftarrow \text{unique}(\text{char}(C))$$
>	- Add **special symbols** in front of vocabulary.
>		-  `"<|endoftext|>"`
>- For $i=1\,{,}\ldots{,}\,k$:
>	- Find the *most frequent* **adjacent tokens** in $C$ $$(t_{L}, t_{R})  = \arg\max\left\{\, p(s_{L},s_{R}):\; (s_{L} + s_{R}) \in C,\; (s_{L},s_{R})\in V\times V\;  \right\}$$
>		- where $+$ means the string concatenation.
>	- Make a *new token* by **concatenation** $$t_{new} = t_{L} + t_{R}$$ 
>	- Add new token to the *vocabulary* $$V \leftarrow V \cup \left\{ t_{new} \right\}$$
>	- Replace the *occurrence* of each of $t_{L}$ and $t_{R}$ in $C$ with *occurrence* of  *new token* $t_{new}$
>	- Update the corpus with new token
>		- This update is *greedy.*
>- *Return*: 
>	- **vocabulary** $V$
>	- the **merge rule** $$R := \left\{ (s_{L},s_{R}) \to s_{L} + s_{R} \,{,}\ldots{,}\, \right\}$$

^98ba57

- [[n-Gram Model and Language Model]]

>[!important] Definition
>The **segmentation** algorithm for  **Byte-Pair Encoding (BPE)** tokenization is described as below
>- *require*: a string $C$
>- *require*: **vocabulary** $V$
>- *require*: **merge rule** $R$
>- **Pre-Tokenization**: initialize the vocabulary $V$ with all *unique single characters* in $C$ $$T  \leftarrow \text{unique}(\text{char}(C))$$
>- For all *merge rule* $r \in R$
>	- $(s_{L}, s_{R})$ be the adjacent pair for $r$
>	- For all *tokens* $i=1\,{,}\ldots{,}\,|T|-1$
>		- If $s[i] = s_{L}$ and $s[i+1] = s_{R}$
>			- **Merge** $s[i]$ and $s[i+1]$, $$s[i] + s[i+1] = r(s[i], s[i+1])$$ 
>			- Replace the token list $$T \leftarrow \left\{ s[1] \,{,}\ldots{,}\,s[i-1]\right\} \cup  \left\{s[i]+s[i+1]\right\} \cup \left\{ s[i+2] \,{,}\ldots{,}\,s[-1]\right\} $$
>- *Return*: 
>	- **tokenized list** $T$


`
### Example Codes

>[!example]
>For example, assume that we have a corpus with following words
>`"hug", "pug", "pun", "bun", "hugs"` with frequency `("hug", 10), ("pug", 5), ("pun", 12), ("bun", 4), ("hugs", 5)`
>
>
>- The *base vocabulary* is given by `["b", "g", "h", "n", "p", "s", "u"]`
>	- The frequency for each characters is
>	- `("h" "u" "g", 10), ("p" "u" "g", 5), ("p" "u" "n", 12), ("b" "u" "n", 4), ("h" "u" "g" "s", 5)`
>- We see that the most frequent adjacent characters is `ug`, which appears 20 times
>- Merge `u` and `g` in adjacent position into `ug` and add it into the vocabulary
>- We now have 
>	- vocabulary `["b", "g", "h", "n", "p", "s", "u", "ug"]`
>	- The frequency for corpus: `("h" "ug", 10), ("p" "ug", 5), ("p" "u" "n", 12), ("b" "u" "n", 4), ("h" "ug" "s", 5)`
>- The most frequent pair is `u` and `n`, which appears 16 times; so add `un` into the vocabulary
>	- vocabulary `["b", "g", "h", "n", "p", "s", "u", "ug", "un"]`
>	- The frequency for corpus: `("h" "ug", 10), ("p" "ug", 5), ("p" "un", 12), ("b" "un", 4), ("h" "ug" "s", 5)`
>- The most frequent pair is `h` and `ug`; so add `un` into the vocabulary
>	- vocabulary `["b", "g", "h", "n", "p", "s", "u", "ug", "un", "hug"]`
>	- The frequency for corpus: `("hug", 10), ("p" "ug", 5), ("p" "un", 12), ("b" "un", 4), ("hug" "s", 5)


- Hugging Face tutorial [link](https://huggingface.co/learn/nlp-course/en/chapter6/5)

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

tokenizer = AutoTokenizer.from_pretrained("gpt2")
```

- split sentences into words

```python
from collections import defaultdict

word_freqs = defaultdict(int) # count frequency of each words

for text in corpus:
    words_with_offsets = tokenizer.backend_tokenizer.pre_tokenizer.pre_tokenize_str(text)
    new_words = [word for word, offset in words_with_offsets]
    for word in new_words:
        word_freqs[word] += 1

print(word_freqs)
```

- result

```python
defaultdict(int, {'This': 3, 'Ġis': 2, 'Ġthe': 1, 'ĠHugging': 1, 'ĠFace': 1, 'ĠCourse': 1, '.': 4, 'Ġchapter': 1,
    'Ġabout': 1, 'Ġtokenization': 1, 'Ġsection': 1, 'Ġshows': 1, 'Ġseveral': 1, 'Ġtokenizer': 1, 'Ġalgorithms': 1,
    'Hopefully': 1, ',': 1, 'Ġyou': 1, 'Ġwill': 1, 'Ġbe': 1, 'Ġable': 1, 'Ġto': 1, 'Ġunderstand': 1, 'Ġhow': 1,
    'Ġthey': 1, 'Ġare': 1, 'Ġtrained': 1, 'Ġand': 1, 'Ġgenerate': 1, 'Ġtokens': 1})
```

- convert to characters

```python
alphabet = []

for word in word_freqs.keys():
    for letter in word:
        if letter not in alphabet:
            alphabet.append(letter)
alphabet.sort()

print(alphabet)
```

- We also add the *special tokens* used by the model at the beginning of that vocabulary. In the case of GPT-2, the only special token is `"<|endoftext|>"`:

```python
vocab = ["<|endoftext|>"] + alphabet.copy()
```

- We now need to split each word into individual characters, to be able to start training:

```python
splits = {word: [c for c in word] for word in word_freqs.keys()}
```

- Now that we are ready for training, let’s write a function that *computes the frequency of each pair*. We’ll need to use this at each step of the training:

```python
def compute_pair_freqs(splits):
    pair_freqs = defaultdict(int)
    for word, freq in word_freqs.items():
        split = splits[word]
        if len(split) == 1:
            continue
        for i in range(len(split) - 1):
            pair = (split[i], split[i + 1])
            pair_freqs[pair] += freq
    return pair_freqs
```

- Now, finding the *most frequent pair* only takes a quick loop:

```python
best_pair = ""
max_freq = None

for pair, freq in pair_freqs.items():
    if max_freq is None or max_freq < freq:
        best_pair = pair
        max_freq = freq

print(best_pair, max_freq)
```

- result

```python
('Ġ', 't') 7
```

- So the first merge to learn is `('Ġ', 't') -> 'Ġt'`, and we add `'Ġt'` to the vocabulary:

```python
merges = {("Ġ", "t"): "Ġt"}
vocab.append("Ġt")
```

- To continue, we need to *apply that merge* in our `splits` dictionary. Let’s write another function for this:

```python
def merge_pair(a, b, splits):
    for word in word_freqs:
        split = splits[word]
        if len(split) == 1:
            continue

        i = 0
        while i < len(split) - 1:
            if split[i] == a and split[i + 1] == b:
                split = split[:i] + [a + b] + split[i + 2 :]
            else:
                i += 1
        splits[word] = split
    return splits
```

- Now we have everything we need to loop until we have learned all the merges we want. Let’s aim for a vocab size of 50:

```python
vocab_size = 50

while len(vocab) < vocab_size:
    pair_freqs = compute_pair_freqs(splits)
    best_pair = ""
    max_freq = None
    for pair, freq in pair_freqs.items():
        if max_freq is None or max_freq < freq:
            best_pair = pair
            max_freq = freq
    splits = merge_pair(*best_pair, splits)
    merges[best_pair] = best_pair[0] + best_pair[1]
    vocab.append(best_pair[0] + best_pair[1])
```

- To tokenize a *new text*, we pre-tokenize it, split it, then apply all the merge rules learned:

```python
def tokenize(text):
    pre_tokenize_result = tokenizer._tokenizer.pre_tokenizer.pre_tokenize_str(text)
    pre_tokenized_text = [word for word, offset in pre_tokenize_result]
    splits = [[l for l in word] for word in pre_tokenized_text]
    for pair, merge in merges.items():
        for idx, split in enumerate(splits):
            i = 0
            while i < len(split) - 1:
                if split[i] == pair[0] and split[i + 1] == pair[1]:
                    split = split[:i] + [merge] + split[i + 2 :]
                else:
                    i += 1
            splits[idx] = split

    return sum(splits, [])
```


## Explanation

>[!important]
>Before the **BPE tokenization**, we need to prepare a training dataset, and complete
>- **text normalization**
>- and **pre-tokenization** such as 
>	- split the sentences into *words* based on *white spaces* and/or *punctuations*
>	- some pre-tokenizer such as GPT2, T5 etc. would *not ignore white space* but use a *special symbol*. 
>		- This enables us to *decode white space.*

- [[Text Normalization]]

>[!important]
>Most tokenizers have **special tokens** such as
>- `"<|endoftext|>"` is used by GPT tokenizer as the end of text.

>[!quote]
>An **advantage** of *BPE segmentation* is that it can effectively *balance the vocabulary size* and the *step size* (the number of tokens required to encode the sentence). 
>- BPE trains the *merged operations* only with a frequency of characters. 
>	- **Frequent substrings** will be *joined early*, resulting in *common words* remaining as **one unique symbol**. 
>	- Words consisting of **rare character combinations** will be *split into smaller units*, e.g., substrings or characters. 
>	- Therefore, only with a small fixed size of vocabulary (usually 16k to 32k), the number of required symbols to encode a sentence will *not significantly increase*, which is an important feature for an efficient decoding. 
>
>One **downside** is, however, that *BPE* is based on a **greedy** and **deterministic symbol replacement**, which can not provide multiple segmentations with probabilities. 
>- It is not trivial to apply BPE to the *subword regularization* that depends on segmentation probabilities $P(x|X)$.
>  
>-- Kudo, T. (2018). Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates. In I. Gurevych & Y. Miyao (Eds.), _Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_ (pp. 66–75). Association for Computational Linguistics. [https://doi.org/10.18653/v1/P18-1007](https://doi.org/10.18653/v1/P18-1007)  



## Other Tricks

>[!info]
>The **GPT-2** and **RoBERTa tokenizers** (which are pretty similar) have a clever way to deal with this: 
>- they don’t look at words as being written with *Unicode characters*, but with **bytes**. 
>- This way the base vocabulary has a small size (*256*), but every character you can think of will still be included and *not end up being converted to the unknown token*. 
>- This trick is called **byte-level BPE**.

- [[Generative Pre-trained Transformer or GPT]]

>[!info]
>The **BPE tokenization** is a *greedy algorithm*.



## Other Tokenization

- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]
- [[Unigram Tokenization]]
- [[WordPiece Tokenization]]


![[Tokenization of Words and Subwords and SentencePiece Tokenization#^217c38]]




-----------
##  Recommended Notes and References



- [[Word Embedding]]
- [[Vector Space Model for Text Representation]]


- [[Speech and Language Processing by Jurafsky]] pp 21
- Sennrich, R., Haddow, B., & Birch, A. (2016). Neural Machine Translation of Rare Words with Subword Units. In K. Erk & N. A. Smith (Eds.), _Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_ (pp. 1715–1725). Association for Computational Linguistics. [https://doi.org/10.18653/v1/P16-1162](https://doi.org/10.18653/v1/P16-1162)
- Hugging Face tutorial [link](https://huggingface.co/learn/nlp-course/en/chapter6/5)