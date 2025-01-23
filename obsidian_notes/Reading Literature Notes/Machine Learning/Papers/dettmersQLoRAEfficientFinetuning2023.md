---
tags:
- '#paper'
aliases: "dettmersQLoRAEfficientFinetuning2023"
year: 2023
name: "QLoRA: Efficient Finetuning of Quantized LLMs"
authors: "Tim Dettmers, Artidoro Pagnoni, Ari Holtzman, Luke Zettlemoyer"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 
---
# Descriptions

## QLoRA: Efficient Finetuning of Quantized LLMs 
> [!info] 
> - **Abstract:** We present QLoRA, an efficient finetuning approach that reduces memory usage enough to finetune a 65B parameter model on a single 48GB GPU while preserving full 16-bit finetuning task performance. QLoRA backpropagates gradients through a frozen, 4-bit quantized pretrained language model into Low Rank Adapters~(LoRA). Our best model family, which we name Guanaco, outperforms all previous openly released models on the Vicuna benchmark, reaching 99.3% of the performance level of ChatGPT while only requiring 24 hours of finetuning on a single GPU. QLoRA introduces a number of innovations to save memory without sacrificing performance: (a) 4-bit NormalFloat (NF4), a new data type that is information-theoretically optimal for normally distributed weights (b) Double Quantization to reduce the average memory footprint by quantizing the quantization constants, and (c) Paged Optimziers to manage memory spikes. We use QLoRA to finetune more than 1,000 models, providing a detailed analysis of instruction following and chatbot performance across 8 instruction datasets, multiple model types (LLaMA, T5), and model scales that would be infeasible to run with regular finetuning (e.g. 33B and 65B parameter models). Our results show that QLoRA finetuning on a small, high-quality dataset leads to state-of-the-art results, even when using smaller models than the previous SoTA. We provide a detailed analysis of chatbot performance based on both human and GPT-4 evaluations, showing that GPT-4 evaluations are a cheap and reasonable alternative to human evaluation. Furthermore, we find that current chatbot benchmarks are not trustworthy to accurately evaluate the performance levels of chatbots. A lemon-picked analysis demonstrates where Guanaco fails compared to ChatGPT. We release all of our models and code, including CUDA kernels for 4-bit training. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/HXR4JEWG) [local](zotero://select/library/items/HXR4JEWG) [pdf](file:////home/lukexie/Documents/Papers/storage/MYPCPESY/Dettmers%20et%20al.%20-%202023%20-%20QLoRA%20Efficient%20Finetuning%20of%20Quantized%20LLMs.pdf)  [pdf](file:////home/lukexie/Documents/Papers/storage/TCX4GFBU/NeurIPS-2023-qlora-efficient-finetuning-of-quantized-llms-Supplemental-Conference.pdf) 
> - **Bibliography**: Dettmers, T., Pagnoni, A., Holtzman, A., & Zettlemoyer, L. (2023). QLoRA: Efficient Finetuning of Quantized LLMs. _Advances in Neural Information Processing Systems_, _36_, 10088–10115. [https://proceedings.neurips.cc/paper_files/paper/2023/hash/1feb87871436031bdc0f2beaa62a049b-Abstract-Conference.html](https://proceedings.neurips.cc/paper_files/paper/2023/hash/1feb87871436031bdc0f2beaa62a049b-Abstract-Conference.html)
> - **Cite Key:** @dettmersQLoRAEfficientFinetuning2023 
> - **Conclusion**:
> - **Tags:** #QLoRA


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




>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.



## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes

- [[Large Language Model and Pretrained Language Models]]