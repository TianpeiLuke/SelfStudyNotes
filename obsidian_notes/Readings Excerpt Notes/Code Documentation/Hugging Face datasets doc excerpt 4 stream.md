---
tags:
  - excerpt
  - documentation
  - code_package
  - python
  - huggingface
  - package/huggingface/datasets
aliases: 
keywords:
  - huggingface/datasets
topics:
  - code/doc
language: python
date of note: 2024-03-23
name: Hugging Face `dataset` package official doc
version: 2.18.0
year: 2024
---

# Stream

> [!quote]
>**Dataset streaming** lets you work with a dataset **without downloading** it. The data is streamed as you **iterate** over the dataset. This is especially helpful when:
> 
> - You don’t want to **wait** for an **extremely large** dataset to **download**.
> - The dataset size **exceeds** the amount of available **disk space** on your computer.
> - You want to **quickly explore** just a few samples of a dataset.

> [!quote]
> Dataset streaming also lets you work with a dataset made of **local** files **without doing any conversion**. In this case, the data is streamed from the local files as you iterate over the dataset. This is especially helpful when:
> 
> - You don’t want to wait for an **extremely large local dataset** to be converted to Arrow.
> - The converted files size would **exceed** the amount of available **disk space** on your computer.
> - You want to **quickly explore** just a few samples of a dataset.

- [original doc link](https://huggingface.co/docs/datasets/stream)
- We can get streaming data by adding `streaming=True` to `load_dataset`
  
```python
from datasets import load_dataset
dataset = load_dataset('oscar-corpus/OSCAR-2201', 'en', split='train', streaming=True)
```

-  It will return `Iterator` object. We can obtain one sample/batch by

```python
print(next(iter(dataset)))
```

## `IterableDataset`

- Loading a dataset in streaming mode creates a **new dataset type instance** (instead of the classic [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) object), known as an [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset). This special type of dataset has its own set of processing methods shown below.


>[!important]
An [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) is useful for iterative jobs like training a model. You shouldn’t use a [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) for jobs that require random access to examples because you have to iterate all over it using a for loop. Getting the **last** example in an iterable dataset would require you to **iterate over all the previous examples**.

## Convert from a Dataset

>If you have an existing [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) object, you can convert it to an [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) with the [to_iterable_dataset()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.to_iterable_dataset) function. This is actually **faster** than setting the `streaming=True` argument in [load_dataset()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/loading_methods#datasets.load_dataset) because the data is streamed from local files.

>[!example]
>```python
>from datasets import load_dataset
>
># faster
>dataset = load_dataset("food101")
>iterable_dataset = dataset.to_iterable_dataset()
>
># slower
>iterable_dataset = load_dataset("food101", streaming=True)
>```

- The [to_iterable_dataset()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.to_iterable_dataset) function supports sharding when the [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) is instantiated. This is useful when working with big datasets, and you’d like to shuffle the dataset or to enable *fast parallel loading* with a **PyTorch DataLoader**.


## Highlights

>[!Important] Highlights
>- Compared to original `Dataset` object. `IterableDataset` object has no row operations (such as **Sort**) since the streaming data can only access to immediate next sample. 
>- We can only download samples in a **buffer** to do *row operations* such as **Shuffle**. 
>- No dataset operations such as **Concatenate**, **Format** etc. 
>- No **Save** or **Export** since we cannot download entire dataset.
>- **Interleave** operation exists to merge two datastreams
>
>Common operations on `IterableDataset` are
>- **Split**, **Shuffle**, **Reshuffle**
>- **Filter**
>- Rename, Remove, Cast
>- **Map**
>- **Interleave**


## Some Functions

- **Shuffle**: Like a regular [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) object, you can also shuffle a [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) with [IterableDataset.shuffle()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.shuffle). 
	- The `buffer_size` argument controls the size of the **buffer** to randomly sample examples from. Let’s say your dataset has one million examples, and you set the `buffer_size` to ten thousand. [IterableDataset.shuffle()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.shuffle) will randomly select examples from the first ten thousand examples in the buffer. Selected examples in the buffer are *replaced with new examples*. By default, the buffer size is 1,000.
	  
- **Reshuffle**: Sometimes you may want to reshuffle the dataset after each epoch. This will require you to set a different seed for each epoch. Use `IterableDataset.set_epoch()` in between epochs to tell the dataset what epoch you’re on.
  
- **Split**: 
	- [IterableDataset.take()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.take) returns the first `n` examples in a dataset:
	- [IterableDataset.skip()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.skip) **omits** the first `n` examples in a dataset and returns the remaining examples

- **Interleave**: [interleave_datasets()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.interleave_datasets) can combine an [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) with other datasets. The combined dataset returns alternating examples from each of the original datasets.
  
- **Map**: Similar to the [Dataset.map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) function for a regular [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset), 🤗 Datasets features [IterableDataset.map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.map) for processing an [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset).

- **Filter**: You can filter rows in the dataset based on a predicate function using [Dataset.filter()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.filter).


-----------
##  Recommended Notes

[^1]: Many functions use the same syntax as the **Pandas Dataframe**.  
- `Dataset` and `IterableDataset` [doc](https://huggingface.co/docs/datasets/about_mapstyle_vs_iterable)
- **Dataset Features** [doc](https://huggingface.co/docs/datasets/about_dataset_features)




----------
##  Citations

**Hugging face** `datasets` package documentation
- Home page [link](https://huggingface.co/docs/datasets/index)
- overview [doc](https://huggingface.co/docs/datasets/how_to)



