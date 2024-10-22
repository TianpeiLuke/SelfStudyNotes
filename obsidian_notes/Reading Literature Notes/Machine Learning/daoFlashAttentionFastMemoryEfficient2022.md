---
tags:
  - "#paper"
  - deep_learning/architecture
aliases:
  - daoFlashAttentionFastMemoryEfficient2022
year: 2022
name: "FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness"
authors: Tri Dao, Dan Fu, Stefano Ermon, Atri Rudra, Christopher Ré
publication: ""
type: conferencePaper
DOI: ""
date of note: 2024-10-21
---
# Descriptions

## FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness 
> [!info] 
> - **Abstract:** Transformers are slow and memory-hungry on long sequences, since the time and memory complexity of self-attention are quadratic in sequence length. Approximate attention methods have attempted to address this problem by trading off model quality to reduce the compute complexity, but often do not achieve wall-clock speedup. We argue that a missing principle is making attention algorithms IO-aware---accounting for reads and writes between levels of GPU memory. We propose FlashAttention, an IO-aware exact attention algorithm that uses tiling to reduce the number of memory reads/writes between GPU high bandwidth memory (HBM) and GPU on-chip SRAM. We analyze the IO complexity of FlashAttention, showing that it requires fewer HBM accesses than standard attention, and is optimal for a range of SRAM sizes. We also extend FlashAttention, yielding an approximate attention algorithm that is faster than any existing approximate attention method. FlashAttention, 3x speedup on GPT-2 (seq. length 1K), and 2.4x speedup on long-range arena (seq. length 1K-4K). FlashAttention, yielding higher quality models (0.7 better perplexity on GPT-2 and 6.4 points of lift on long-document classification) and entirely new capabilities: the first Transformers to achieve better-than-chance performance on the Path-X challenge (seq. length 16K, 61.4% accuracy) and Path-256 (seq. length 64K, 63.1% accuracy). 
> - **Sources**: [online](http://zotero.org/users/13492210/items/9UZXDXZM) [local](zotero://select/library/items/9UZXDXZM) [pdf](file:////home/lukexie/Documents/Papers/storage/WRVFH3X9/Dao%20et%20al.%20-%202022%20-%20FlashAttention%20Fast%20and%20Memory-Efficient%20Exact%20At.pdf)  [pdf](file:////home/lukexie/Documents/Papers/storage/WEVL5U37/NeurIPS-2022-flashattention-fast-and-memory-efficient-exact-attention-with-io-awareness-Supplemental-Conference.pdf) 
> - **Bibliography**: Dao, T., Fu, D., Ermon, S., Rudra, A., & Ré, C. (2022). FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness. _Advances in Neural Information Processing Systems_, _35_, 16344–16359. [https://proceedings.neurips.cc/paper_files/paper/2022/hash/67d57c32e20fd0a7a302cb81d36e40d5-Abstract-Conference.html](https://proceedings.neurips.cc/paper_files/paper/2022/hash/67d57c32e20fd0a7a302cb81d36e40d5-Abstract-Conference.html)
> - **Cite Key:** [[@daoFlashAttentionFastMemoryEfficient2022]] 
> - **Conclusion**:


>[!note] Highlights:
>
>-
>-
>-



# Questions
## Questions Regarding to This Paper


>[!question] 
>What are the *primary assumptions* behind this paper?



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 




>[!question]
>What are *the main contributions* of the paper?



## Highlight of Technical Details


>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.



## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes

- [[touvronLlamaOpenFoundation2023]]
- [[vaswaniAttentionAllYou2017]]