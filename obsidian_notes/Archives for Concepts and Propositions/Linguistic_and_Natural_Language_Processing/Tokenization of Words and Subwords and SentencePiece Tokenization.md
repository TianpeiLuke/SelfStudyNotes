---
tags:
  - concept
  - natural_language_processing/tokenization
keywords:
  - word_tokenization
  - subword_tokenization
topics:
  - natural_language_processing/tokenization
name: Tokenization of Words and Subwords and SentencePiece Tokenization
date of note: 2024-11-17
---

## Concept Definition

>[!important]
>**Name**: Tokenization of Words and Subwords and SentencePiece Tokenization

>[!important] Definition
>The **tokenization** refers to the task of *segmenting* running text into words.

>[!important]
>There are two classes of *tokenization*
>- **top-down tokenization** or  **rule-based tokenization**: 
>	- we define a *standard* and implement *rules* to implement the tokenization
>- **bottom-up tokenization** includes
>	- **subword tokenization**
>	- **byte-pair encoding**

### Top-down Tokenization via Rules

>[!important] Definition
>The **top-down tokenization** used *predefined rules* to segment text. 
>- It covert *punctuations* (e.g. `\s`) to a new line `\n` to break off punctuation into separate tokens.
>	- We often want to keep punctuations *within word* e.g. `m.p.h`, `Ph.D`, `AT&T`
>	- Some punctuation marks are used as *units* for *prices*, *numbers* etc. `$120`, `01/02/06`
>	- Some regular expression such as *emails*, *URLs*, *hashtags* contains punctuations not separable. 
>- Collapse all *upper cases* to *lower cases*
>- The **number expressions** introduce complexities. 
>	- *comma* may appear inside numbers such as `120,000`
>- The *tokenization rule* is **language dependent**.
>	- German, Spanish, French use a *comma* to mark the *decimal point* 
>	- It uses *spaces* where the English uses *commas*.
>	- It is more complex for Chinese, Japanese and Thai etc as they do not use spaces to mark potential word boundaries
>	- Japanese and Thai need additional **word segmentation**. 
>- The tokenization rule need to expand the **clitic contractions** that are marked by apostrophes, e.g. `what're`, `you'd` 
>	- A **clitic** is a part of a word that *can’t stand on its own*, and can only occur when it is *attached* to another word.
>	- Such contractions occur in other alphabetic languages, including *French pronouns* `j'ai`, or `l'homme`
>- In some applications, tokenization algorithm would group a *multi-word expression* into a single token., e.g. `New York`, `rock 'n' roll`
>	- This requires additional **name entity recognition.**

- [[Regular Expression Pattern Basics]]
- [[Regular Expression Advanced Operations]]

>[!important] Definition
>One commonly used tokenization standard is known as the **Penn Treebank tokenization** standard.

>[!quote]
>In practice, since tokenization is run *before* any other language processing, it needs to be very **fast**. 
>
>For word tokenziation we generally use **deterministic algorithms** based on *regular expressions* compiled into efficient *finite state automata*.
>
>Carefully designed *deterministic algorithms* can deal with the ambiguities that arise.
>
>-- [[Speech and Language Processing by Jurafsky]] pp 19

- [[Regular Expression Pattern Basics]]
- [[Regular Expression Advanced Operations]]

### Bottom-Up Tokenization via Learning

>[!important] Definition
>The **bottom-up tokenization** uses the data to learn how to define the token.
>- It mitigates the **unknown word problem**, i.e. a word appears in *test corpus* but not appear in *training corpus*.
>- It *trains* a **tokenizer** that learns the *merge rule / remove rule* from data, as well as a **vocabulary.**

^bc8d95

>[!important] Definition
>The modern tokenizer automatically induce sets of tokens that include tokens *smaller than words*, called **subwords**.
>- Subwords can be arbitrary *substrings*, 
>- or they can be *meaning-bearing units* like the **morphemes**. e.g. `-est`, `-er`, `-able`, `un-`

- [[Morphology]]

>[!important] Definition
>Most *tokenization schemes* have two parts: 
>- **Token learner**
>	- It takes a raw *training corpus* (sometimes roughly *pre-separated* into words, for example by whitespace) 
>	- and induces a **vocabulary**, a set of *tokens*. 
>- **Token segmenter** 
>	- takes a raw *test sentence* 
>	- and *segments* it into the tokens *in the vocabulary*.

^e9eebb

## Explanation

![[tokenization_word_subword.png]]


## Algorithm overview

>[!important]
> In the following sections, we’ll dive into the three main subword tokenization algorithms: 
> - **BPE** (used by GPT-2 and others), 
> - **WordPiece** (used for example by BERT), 
> - and **Unigram** (used by T5 and others).
> 
> 

|     Model     |                                    **BPE**                                     |                                                                              **WordPiece**                                                                               |                                               **Unigram**                                               |
| :-----------: | :----------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------: |
| **Training**  |     Starts from a *small vocabulary* and learns rules to **merge tokens**      |                                                  Starts from a *small vocabulary* and learns rules to **merge tokens**                                                   |                 Starts from a *large vocabulary* and learns rules to **remove tokens**                  |
| Training step |         **Merges** the tokens corresponding to the *most common pair*          | **Merges** the tokens corresponding to the pair with the *best score* based on the frequency of the pair, privileging pairs where each individual token is less frequent | **Removes** all the tokens in the vocabulary that will *minimize the loss* computed on the whole corpus |
|  **Learns**   |                      **Merge rules** and a **vocabulary**                      |                                                                          Just a **vocabulary**                                                                           |                            A **vocabulary** with a **score** for each token                             |
| **Encoding**  | Splits a word into *characters* and applies the merges learned during training |                     Finds the **longest subword** starting from the beginning that is in the vocabulary, then does the same for the rest of the word                     |          Finds the **most likely split** into tokens, using the scores learned during training          |
| Example Model |                 [[Generative Pre-trained Transformer or GPT]]                  |                                                    [[Bidirectional Encoder Representation from Transformer or BERT]]                                                     |                       [[Text-to-Text Transfer Transformer or T5 for Translation]]                       |

^217c38

- [[Byte-Pair Encoding or BPE Tokenization]]
- [[WordPiece Tokenization]]
- [[Unigram Tokenization]]

![[tokenization_subwords.png]]


## SentencePiece Tokenization by Google

>[!quote]
>SentencePiece is a re-implementation of **sub-word units**, an effective way to alleviate the open vocabulary problems in neural machine translation. SentencePiece supports two segmentation algorithms, **byte-pair-encoding (BPE)** [Sennrich et al.](http://www.aclweb.org/anthology/P16-1162) and **unigram language model** [Kudo.](https://arxiv.org/abs/1804.10959). Here are the high level differences from other implementations.
>- **The number of unique tokens is predetermined**
>- **Trains from raw sentences** without pre-tokenization
>- **Whitespace is treated as a basic symbol** 
>- **Subword regularization and BPE-dropout**
>	- **Subword regularization** [Kudo.](https://arxiv.org/abs/1804.10959) and 
>	- **BPE-dropout** [Provilkov et al](https://arxiv.org/abs/1910.13267) are simple regularization methods that virtually augment training data with on-the-fly subword sampling, which helps to improve the accuracy as well as robustness of NMT models.
>
>-- GIthub [Google sentencepiece](https://github.com/google/sentencepiece)

- Kudo, T. (2018). Sentencepiece: A simple and language independent subword tokenizer and detokenizer for neural text processing. _arXiv preprint arXiv:1808.06226_.





-----------
##  Recommended Notes and References


- [[Text Normalization]]
- [[Word Embedding]]
- [[Vector Space Model in Information Retrieval]]
- [[Alphabets and Strings Abstract Definition]]


- [[Speech and Language Processing by Jurafsky]] pp 17
- [[Artificial Intelligence Modern Approach by Russell]] pp 875

- Youtube [LLM Tokenizers Explained: BPE Encoding, WordPiece and SentencePiece](https://www.youtube.com/watch?v=hL4ZnAWSyuU)