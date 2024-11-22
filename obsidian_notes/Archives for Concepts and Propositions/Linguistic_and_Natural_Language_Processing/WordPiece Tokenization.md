---
tags:
  - concept
  - natural_language_processing/tokenization
keywords:
  - word_tokenization
  - subword_tokenization
  - wordpiece_tokenization
topics:
  - natural_language_processing/tokenization
name: WordPiece Tokenization
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: WordPiece Tokenization

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^bc8d95]]

![[Tokenization of Words and Subwords and SentencePiece Tokenization#^e9eebb]]

![[Byte-Pair Encoding or BPE Tokenization#^b47474]]

![[Byte-Pair Encoding or BPE Tokenization#^98ba57]]

- [[Byte-Pair Encoding or BPE Tokenization]]
- [[Tokenization of Words and Subwords and SentencePiece Tokenization]]
- [[n-Gram Model and Language Model]]

>[!important] Definition
>The **WordPiece tokenization** is a *subword-based tokenization* algorithm. 
>- Like BPE, it starts with *small vocabulary* including *special tokens*, and **initial alphabet**
>	- It identifies *subwords* by adding a *prefix* (e.g. for *BERT*, `##`)
>	- Each word is initially split by adding that prefix to each character.
>	- Only the first character in the word is without prefix.
>	- the *initial alphabet* contains all the characters present at the *beginning* of a word and the characters present inside a word preceded by the **WordPiece prefix**.
>- Like BPE, **WordPiece** learns **merge rules**
>	- The *main difference* is that the merge pair is selected based on a *score*
>	- The **score** is defined as $$score = \frac{p(s_{L}, s_{R})}{p(s_{L})\,p(s_{R})}$$
>		- The algorithm *prioritize* the merging of pairs where the *individual parts* are *less frequent* in the vocabulary 
>	- When merging two subwords, we remove `##` between two tokens

^7acc64

- [[n-Gram Model and Language Model]]
- [[Multinomial Distribution]]
- [[Mutual Information]]
- [[Likelihood Function]]

>[!important] Definition
>The **training** algorithm for **WordPiece** tokenization is described as below
>- *require*: string $C$
>- *require*: number of *merges* $k$
>- **Pre-tokenization**: initialize the vocabulary $V$ with all *unique single characters* in $C$ $$V \leftarrow \text{unique}(\text{char}(C))$$
>	- Add **special symbols** in front of vocabulary
>		- `["[PAD]", "[UNK]", "[CLS]", "[SEP]", "[MASK]"]`
>	- Add **WordPiece prefix** to characters inside the word $$V = \left\{ \# + s: \; s\in C[2:], s\in V  \right\}$$
>- For $i=1\,{,}\ldots{,}\,k$:
>	- Find the **adjacent tokens** in $C$ with the *highest* **score** based on token and pair *frequency* $$(t_{L}, t_{R})  = \arg\max\left\{\, \frac{p(s_{L},s_{R})}{p(s_{L})\,p(s_{R})}:\; (s_{L} + s_{R}) \in C,\; (s_{L},s_{R})\in V\times V\;  \right\}$$
>		- where $+$ means the string concatenation.
>	- Make a *new token* by **concatenation** $$t_{new} = t_{L} + t_{R}$$ 
>	- Add new token to the *vocabulary* $$V \leftarrow V \cup \left\{ t_{new} \right\}$$
>	- Replace the *occurrence* of each of $t_{L}$ and $t_{R}$ in $C$ with *occurrence* of  *new token* $t_{new}$
>	- Update the corpus with new token
>		- This update is *greedy.*
>- *Return*: 
>	- **vocabulary** $V$

>[!important] Definition
>The **segmentation** algorithm for  **WordPiece** tokenization is described as below
>- *require*: string $C$
>- *require*: **vocabulary** $V$
>- $T = \emptyset$
>- $w = C$
>- While word $w$ not empty
>	- For $i=len(w) \,{,}\ldots{,}\,1$:
>		- *Split* word $w$ into two parts $$w[:i], \quad w[i:]$$
>		- If the *first part subword* is in *vocabulary* $w[:i]\in V$:
>			- $$T \leftarrow T \cup \left\{ w[:i] \right\}$$
>			- focus on second part $$w \leftarrow w[i:]$$
>			- add **WordPiece prefix** $$w \leftarrow \#\# + w[i:] $$
>- Return
>	- Token list $T$


>[!info]
>Segmentation via **divide-and-conquer** 

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

tokenizer = AutoTokenizer.from_pretrained("bert-base-cased")
```

- Then we compute the frequencies of each word in the corpus as we do the pre-tokenization:

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

```python
defaultdict(
    int, {'This': 3, 'is': 2, 'the': 1, 'Hugging': 1, 'Face': 1, 'Course': 1, '.': 4, 'chapter': 1, 'about': 1,
    'tokenization': 1, 'section': 1, 'shows': 1, 'several': 1, 'tokenizer': 1, 'algorithms': 1, 'Hopefully': 1,
    ',': 1, 'you': 1, 'will': 1, 'be': 1, 'able': 1, 'to': 1, 'understand': 1, 'how': 1, 'they': 1, 'are': 1,
    'trained': 1, 'and': 1, 'generate': 1, 'tokens': 1})
```

- the alphabet is the unique set composed of all the first letters of words, and all the other letters that appear in words prefixed by `##`:

```python
alphabet = []
for word in word_freqs.keys():
    if word[0] not in alphabet:
        alphabet.append(word[0])
    for letter in word[1:]:
        if f"##{letter}" not in alphabet:
            alphabet.append(f"##{letter}")

alphabet.sort()
alphabet

print(alphabet)
```

```python
['##a', '##b', '##c', '##d', '##e', '##f', '##g', '##h', '##i', '##k', '##l', '##m', '##n', '##o', '##p', '##r', '##s',
 '##t', '##u', '##v', '##w', '##y', '##z', ',', '.', 'C', 'F', 'H', 'T', 'a', 'b', 'c', 'g', 'h', 'i', 's', 't', 'u',
 'w', 'y']
```

- We also add the special tokens used by the model at the beginning of that vocabulary. In the case of BERT, it’s the list `["[PAD]", "[UNK]", "[CLS]", "[SEP]", "[MASK]"]`:

```python
vocab = ["[PAD]", "[UNK]", "[CLS]", "[SEP]", "[MASK]"] + alphabet.copy()
```

- Next we need to split each word, with all the letters that are not the first prefixed by `##`:

```python
splits = {
    word: [c if i == 0 else f"##{c}" for i, c in enumerate(word)]
    for word in word_freqs.keys()
}
```

- compute the score 

```python
def compute_pair_scores(splits):
    letter_freqs = defaultdict(int)
    pair_freqs = defaultdict(int)
    for word, freq in word_freqs.items():
        split = splits[word]
        if len(split) == 1:
            letter_freqs[split[0]] += freq
            continue
        for i in range(len(split) - 1):
            pair = (split[i], split[i + 1])
            letter_freqs[split[i]] += freq
            pair_freqs[pair] += freq
        letter_freqs[split[-1]] += freq

    scores = {
        pair: freq / (letter_freqs[pair[0]] * letter_freqs[pair[1]])
        for pair, freq in pair_freqs.items()
    }
    return scores
```

```python
('T', '##h'): 0.125
('##h', '##i'): 0.03409090909090909
('##i', '##s'): 0.02727272727272727
('i', '##s'): 0.1
('t', '##h'): 0.03571428571428571
('##h', '##e'): 0.011904761904761904
```

- Now, finding the pair with the best score only takes a quick loop:

```python
best_pair = ""
max_score = None
for pair, score in pair_scores.items():
    if max_score is None or max_score < score:
        best_pair = pair
        max_score = score

print(best_pair, max_score)
```

- So the first merge to learn is `('a', '##b') -> 'ab'`, and we add `'ab'` to the vocabulary:

```python
vocab.append("ab")
```

- apply the merge in the `splits` dictionary

```python
def merge_pair(a, b, splits):
    for word in word_freqs:
        split = splits[word]
        if len(split) == 1:
            continue
        i = 0
        while i < len(split) - 1:
            if split[i] == a and split[i + 1] == b:
                merge = a + b[2:] if b.startswith("##") else a + b
                split = split[:i] + [merge] + split[i + 2 :]
            else:
                i += 1
        splits[word] = split
    return splits
```

```python
['ab', '##o', '##u', '##t']
```

- Now we have everything we need to loop until we have learned all the merges we want. Let’s aim for a vocab size of 70:

```python
vocab_size = 70
while len(vocab) < vocab_size:
    scores = compute_pair_scores(splits)
    best_pair, max_score = "", None
    for pair, score in scores.items():
        if max_score is None or max_score < score:
            best_pair = pair
            max_score = score
    splits = merge_pair(*best_pair, splits)
    new_token = (
        best_pair[0] + best_pair[1][2:]
        if best_pair[1].startswith("##")
        else best_pair[0] + best_pair[1]
    )
    vocab.append(new_token)
```

```python
['[PAD]', '[UNK]', '[CLS]', '[SEP]', '[MASK]', '##a', '##b', '##c', '##d', '##e', '##f', '##g', '##h', '##i', '##k',
 '##l', '##m', '##n', '##o', '##p', '##r', '##s', '##t', '##u', '##v', '##w', '##y', '##z', ',', '.', 'C', 'F', 'H',
 'T', 'a', 'b', 'c', 'g', 'h', 'i', 's', 't', 'u', 'w', 'y', 'ab', '##fu', 'Fa', 'Fac', '##ct', '##ful', '##full', '##fully',
 'Th', 'ch', '##hm', 'cha', 'chap', 'chapt', '##thm', 'Hu', 'Hug', 'Hugg', 'sh', 'th', 'is', '##thms', '##za', '##zat',
 '##ut']
```

>[!info]
> - To tokenize a new text, we 
> 	- *pre-tokenize* it, 
> 	- *split it*, 
> 	- then apply the tokenization algorithm on *each word*. 
> 		- That is, we look for the *biggest subword* starting at the *beginning* of the first *word* and split it, 
> 		- then we repeat the process on the *second part*, and so on for the rest of that word and the following words in the text:

```python
def encode_word(word):
    tokens = []
    while len(word) > 0:
        i = len(word)
        while i > 0 and word[:i] not in vocab:
            i -= 1
        if i == 0:
            return ["[UNK]"]
        tokens.append(word[:i])
        word = word[i:]
        if len(word) > 0:
            word = f"##{word}"
    return tokens
```


## Explanation

>[!info]
>WordPiece is the tokenization algorithm *Google* developed to pretrain **BERT**. 
>
>It has since been reused in quite a few Transformer models based on BERT, such as 
>- **DistilBERT**, 
>- **MobileBERT**, 
>- **Funnel Transformers**, 
>- and **MPNET**. 
>  
>It’s very similar to BPE in terms of the training, but the actual tokenization is done differently.

>[!info]
>Tokenization differs in **WordPiece** and **BPE** in that 
>- WordPiece only saves the **final vocabulary**, 
>- not the *merge rules* learned.
> 
>Starting from the word to tokenize, WordPiece finds the **longest subword** that is in the *vocabulary*, then splits on it.


![[Tokenization of Words and Subwords and SentencePiece Tokenization#^217c38]]







-----------
##  Recommended Notes and References


- [[Text-to-Text Transfer Transformer or T5 for Translation]]
- [[Word Embedding]]
- [[Vector Space Model in Information Retrieval]]



- [[Speech and Language Processing by Jurafsky]] pp 21
- Hugging Face Tutorial [WordPiece tokenization](https://huggingface.co/learn/nlp-course/en/chapter6/6)
- Medium blog  [WordPiece: Subword-based tokenization algorithm](https://towardsdatascience.com/wordpiece-subword-based-tokenization-algorithm-1fbd14394ed7)