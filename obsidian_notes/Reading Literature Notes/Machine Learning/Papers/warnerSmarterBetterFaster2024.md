---
tags:
- '#paper'
aliases: "warnerSmarterBetterFaster2024"
year: 2024
name: "Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference"
authors: "Benjamin Warner, Antoine Chaffin, Benjamin Clavié, Orion Weller, Oskar Hallström, Said Taghadouini, Alexis Gallagher, Raja Biswas, Faisal Ladhak, Tom Aarsen, Nathan Cooper, Griffin Adams, Jeremy Howard, Iacopo Poli"
publication: ""
type: "preprint"
DOI: "10.48550/arXiv.2412.13663"
date of note: 2025-01-31 
---
# Descriptions

## Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference 

> [!info] 
> - **Abstract:** Encoder-only transformer models such as BERT offer a great performance-size tradeoff for retrieval and classification tasks with respect to larger decoder-only models. Despite being the workhorse of numerous production pipelines, there have been limited Pareto improvements to BERT since its release. In this paper, we introduce ModernBERT, bringing modern model optimizations to encoder-only models and representing a major Pareto improvement over older encoders. Trained on 2 trillion tokens with a native 8192 sequence length, ModernBERT models exhibit state-of-the-art results on a large pool of evaluations encompassing diverse classification tasks and both single and multi-vector retrieval on different domains (including code). In addition to strong downstream performance, ModernBERT is also the most speed and memory efficient encoder and is designed for inference on common GPUs. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/4NCZEK23) [local](zotero://select/library/items/4NCZEK23) [pdf](file:////Users/lukexie/Zotero/storage/SY74EBUC/Warner%20et%20al.%20-%202024%20-%20Smarter,%20Better,%20Faster,%20Longer%20A%20Modern%20Bidirectional%20Encoder%20for%20Fast,%20Memory%20Efficient,%20and%20Long.pdf) 
> - **Bibliography**: Warner, B., Chaffin, A., Clavié, B., Weller, O., Hallström, O., Taghadouini, S., Gallagher, A., Biswas, R., Ladhak, F., Aarsen, T., Cooper, N., Adams, G., Howard, J., & Poli, I. (2024). _Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference_ (arXiv:2412.13663). arXiv. [https://doi.org/10.48550/arXiv.2412.13663](https://doi.org/10.48550/arXiv.2412.13663)
> - **Cite Key:** @warnerSmarterBetterFaster2024
> - **Conclusion**:
> - **Tags:** #Computer-Science---Artificial-Intelligence, #Computer-Science---Computation-and-Language


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

- **ModernBERT**, a new BERT class model as encoder-only transformer architecture
- ModernBERT stands out as the *best-in-class model* within the BERT family due to its superior performance across various tasks and benchmarks, as evidenced by the provided table:
- ModernBERT sets a new benchmark for encoder-only models, combining speed, efficiency, and versatility. 
	- It outperforms DeBERTaV3 on the GLUE benchmark while using a fraction of the memory and is up to *4x* faster in mixed-length inputs. 
	- With an unmatched *8,192-token context length*, ModernBERT excels in long-context tasks like retrieval and RAG pipelines, outperforming specialized models like GTE-en-MLM. 
	- It also revolutionizes *code retrieval*, scoring over 80 on the SQA dataset and enabling applications like AI-powered IDEs and enterprise-wide code indexing.
	- ModernBERT’s performance across retrieval, NLU, and code tasks makes it a game-changer for diverse NLP applications.

## Highlight of Technical Details


>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.

- **ModernBERT**, a new BERT class model as encoder-only transformer architecture
- **Updates to Transformers architecture**: 
	- ModernBERT refines the Transformer architecture with upgrades like **rotary positional embeddings** and **GeGLU layers**, improving efficiency, scalability, and training stability.
- **Faster processing using Flash Attention**: 
	- By leveraging **Flash Attention 2** and efficient techniques like **alternating attention** and **unpadding**, ModernBERT ensures faster processing while staying practical for real-world applications.
- **Global and Local Attention**: 
	- ModernBERT alternates between **local** and **global attention**, balancing computational efficiency with contextual understanding, enabling faster long-sequence processing.
- **Unpadding and Sequence Packing**: 
	- ModernBERT eliminates computational waste through *unpadding* and *sequence packing*, streamlining batch processing for significant speed gains. 
	- **In unpadding**, rather than keeping these padding tokens, we remove them all, and concatenate them into *mini-batches* with a batch size of one, avoiding all unnecessary computations.
- **Paying Attention to Hardware**: 
	- ModernBERT is optimized for common GPUs with carefully tuned layer dimensions and depths, balancing performance with compatibility across devices.
- **Training**: 
	- ModernBERT is trained on diverse data (text, code, and scientific articles) with a *three-phase approach*, ensuring broad capabilities across tasks, including *long-context processing*.
- **Process**: 
	- By *simplifying objectives*, *increasing masking rates*, and providing *intermediate checkpoints*, ModernBERT enhances training efficiency and supports further research.
- **Some other tricks**: 
	- ModernBERT accelerates training using **batch-size warmup** and **innovative weight initialization**, boosting early learning and scalability.


- [[Rotary Positional Embedding for Large Language Models]]
- [[Flash Attention Mechanism for Large Language Model]]



## Benchmark Performance

1. **Information Retrieval (IR) Performance**:

> **BEIR (DPR)**: ModernBERT achieves the highest score in both Base (41.6) and Large (44.0) categories, outperforming other BERT-based models like GTE-en-MLM and RoBERTa.
> 
> **MLDR_OOD and MLDR_ID**: ModernBERT demonstrates consistent leadership in handling out-of-distribution (OOD) and in-distribution (ID) datasets for information retrieval. Its Large model scores are particularly impressive at 48.6 (MLDR_OOD) and 52.4 (MLDR_ID), indicating robustness and adaptability.

**2. Natural Language Understanding (NLU)**:

> On the GLUE benchmark, ModernBERT delivers top-tier results: 88.5 (Base) and 90.4 (Large). These scores are higher than competitors like RoBERTa and GTE-en-MLM, showcasing its ability to grasp complex language semantics.

**3. Code Understanding Tasks**:

> ModernBERT excels in programming-related benchmarks such as CSN and SQA. Its Base model leads with 56.4 (CSN) and 73.6 (SQA), while the Large model achieves 59.5 and 83.9, respectively. This underscores its suitability for code-related tasks.

**4. Consistent Top Performer**:

> Across all tested domains — IR, NLU, and Code — ModernBERT consistently ranks at or near the top. This highlights its versatility and cutting-edge advancements.

## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?

- Yes. BERT is used in several project and is critical as classification

> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes

- [[devlinBERTPretrainingDeep2019]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Multi-modal BERT Classification Model v1 for BSM]]
- [[Sentence-BERT for Sentence Embedding]]
- [[ColBERT as Multi-Representation Bi-Encoder Structure for Dense Information Retrieval]]
- Medium
	- [ModernBERT: A new improved BERT for text embeddings](https://medium.com/data-science-in-your-pocket/modernbert-a-new-improved-bert-for-text-embeddings-538239202527)