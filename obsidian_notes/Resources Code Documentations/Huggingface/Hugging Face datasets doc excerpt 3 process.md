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

# Process

> [!quote]
> This guide will show you how to:
> 
> - **Reorder** rows and **split** the dataset.
> - **Rename** and **remove** columns, and other common **column operations**.
> - **Apply processing functions to each example** in a dataset.
> - **Concatenate** datasets.
> - Apply a **custom formatting** transform.
> - **Save and export** processed datasets.

- [original doc link](https://huggingface.co/docs/datasets/process#process)

The following data is used in examples below:
>[!example]
>```python
>from datasets import load_dataset
>dataset = load_dataset("glue", "mrpc", split="train")
>```

## Methods for `Datasets` object [^1]

- **Sort**:  Use [sort()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.sort) to sort column values according to their numerical values. This method creates **indices mapping** from sorted indices to original indices.
  
- **Shuffle**: The [shuffle()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.shuffle) function randomly rearranges the column values. You can specify the `generator` parameter in this function to use a different `numpy.random.Generator` if you want more control over the algorithm used to shuffle the dataset.
	- If [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) has an **indices mapping**, the speed can become 10x slower.
	- To restore speed, rewrite the entire dataset on your disk again using [Dataset.flatten_indices()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.flatten_indices) to remove indices mapping;
	- lternatively, you can switch to an [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) and leverage its fast approximate shuffling [IterableDataset.shuffle()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset.shuffle)
	  
- **Select**:  [select()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.select) returns rows according to a list of **indices**
- **Filter**:  [filter()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.filter) returns rows that **match** a specified condition
	- [filter()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.filter) can also filter by indices if you set `with_indices=True`
	- Unless the list of indices to keep is contiguous, those methods also create an **indices mapping** under the hood.
	  
- **Split**: The [train_test_split()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.train_test_split) function creates train and test splits if your dataset doesn’t already have them. use the `test_size` parameter.
  
- **Shard**: Datasets supports **sharding** to divide a very large dataset into a predefined number of chunks. Specify the `num_shards` parameter in [shard()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.shard) to determine the number of shards to split the dataset into. You’ll also need to provide the shard you want to return with the `index` parameter.
  
- **Rename**: Use [rename_column()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.rename_column) when you need to rename a column in your dataset.
  
- **Remove**: When you need to remove one or more columns, provide the column name to remove to the [remove_columns()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.remove_columns) function.
  
- **Select Columns**: [select_columns()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.select_columns) selects one or more columns to keep and removes the rest.

- **Cast**: The [cast()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.cast) function transforms the **feature type** of one or more columns. This function accepts your new [Features](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Features) as its argument, e.g. the [ClassLabel](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.ClassLabel) and [Value](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Value) features.
  
- **Cast one Column**: Use the [cast_column()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.cast_column) function to change the feature type of a single column.

- **Flatten**: Sometimes a column can be a nested structure of several types. Use the [flatten()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.flatten) function to extract the **subfields** into **their own separate columns**

- **Map**: The primary purpose of [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) is to **speed up processing functions.** It allows you to **apply a processing function to each example** in a dataset, **independently** or **in batches.** 
	- This function can even **create new rows and columns**.
	- Specify the column to remove with the `remove_columns` parameter in [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map)
	- You can also use [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) with indices if you set `with_indices=True`.
	- **Multiprocessing** significantly speeds up processing by parallelizing processes on the CPU. Set the `num_proc` parameter in [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) to set the number of processes to use.
	- **Batch processing**: The [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) function supports working with batches of examples. Operate on batches by setting `batched=True`. The default batch size is 1000, but you can adjust it with the `batch_size` parameter.
	- The [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) function could also be used for **data augmentation**. 
	- **Process multiple splits**: Many datasets have splits that can be processed simultaneously with [DatasetDict.map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.DatasetDict.map).
	- **Distributed usage**: When you use [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) in a distributed setting, you should also use [torch.distributed.barrier](https://pytorch.org/docs/stable/distributed?highlight=barrier#torch.distributed.barrier). This ensures the main process performs the mapping, while the other processes load the results, thereby avoiding duplicate work.


>[!example]
>Now use [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map) to apply the `add_prefix` function to the entire dataset:
>```python
>
>def add_prefix(example):
>	example["sentence1"] = 'My sentence: ' + example["sentence1"]
>	return example
>	
>updated_dataset = small_dataset.map(add_prefix)
>```


>[!example] 
>You’ll remove a column with [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map). When you remove a column, it is **only removed after** the example has been provided to the mapped function. This allows the mapped function to **use the content** of the columns **before they are removed.**
>- Specify the column to remove with the `remove_columns` parameter in [map()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.map):
>```python
>
>updated_dataset = dataset.map(lambda example: {"new_sentence": example["sentence1"]}, remove_columns=["sentence1"])
>```


>[!example] Chunking
>When examples are too long, you may want to split them into several smaller chunks. Begin by creating a function that:
> 
> 1. **Splits** the `sentence1` field into chunks of 50 characters.
> 2. **Stacks** all the chunks together to create the new dataset.
> 
>```python
>
>def chunk_examples(examples):
>	chunks = []
>	for sentence in examples["sentence1"]:
>		chunks += [sentence[i:i + 50] for i in range(0, len(sentence), 50)]
>	return {"chunks": chunks}
>
>chunked_dataset = dataset.map(chunk_examples, batched=True, remove_columns=dataset.column_names)
>```


>[!example] Distributed Usage 
>The following example shows how you can use `torch.distributed.barrier` to synchronize the processes:
> 
>```python
>from datasets import Dataset
>import torch.distributed
>
>dataset1 = Dataset.from_dict({"a": [0, 1, 2]})
>if training_args.local_rank > 0:
>	print("Waiting for main process to perform the mapping")
>	torch.distributed.barrier()
>
>dataset2 = dataset1.map(lambda x: {"a": x["a"] + 1})	
>if training_args.local_rank == 0:
>	print("Loading results from main process")
>	torch.distributed.barrier()
>```

- **Save**: Once you are done processing your dataset, you can save and reuse it later with [save_to_disk()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.save_to_disk).

- **Export**: `to_csv`, `to_json`, `to_paraquet` ,`to_sql`

- **Format**: The [set_format()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.set_format) function changes the format of a column to be compatible with some common data formats. Specify the output you’d like in the `type` parameter and the columns you want to format. Formatting is applied on-the-fly.
	- support **Pytorch, NumPy, Pandas, and JAX**
	- The [with_format()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.with_format) function also changes the format of a column, except it returns a **new [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) object**:
	  
- **Format transform**: The [set_transform()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset.set_transform) function applies a custom formatting transform on-the-fly. This function replaces any previously specified format.
  
- **Concatenate**: Separate datasets can be concatenated if they **share the same column types.** Concatenate datasets with [concatenate_datasets()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.concatenate_datasets)
  
- **Interleave**: You can also mix several datasets together by **taking alternating examples from each one** to create a new dataset. This is known as _interleaving_, which is enabled by the [interleave_datasets()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.interleave_datasets) function.
	- Both [interleave_datasets()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.interleave_datasets) and [concatenate_datasets()](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.concatenate_datasets) work with regular [Dataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.Dataset) and [IterableDataset](https://huggingface.co/docs/datasets/v2.18.0/en/package_reference/main_classes#datasets.IterableDataset) objects.


## Highlights

>[!Important] Highlights
>Commonly used methods
>- **Split**, **Sort**, **Shuffle**
>- Select, **Filter**
>- Rename, Remove, Select Columns
>- **Save**, **Export**
>- **Map**
>- **Concatenate**
>- Format



-----------
##  Recommended Notes

[^1]: Many functions use the same syntax as the **Pandas Dataframe**.  

- `ARROW` format [doc](https://huggingface.co/docs/datasets/about_arrow)
- `Dataset` and `IterableDataset` [doc](https://huggingface.co/docs/datasets/about_mapstyle_vs_iterable)
- **Dataset Features** [doc](https://huggingface.co/docs/datasets/about_dataset_features)
- **Batch Mapping** [doc](https://huggingface.co/docs/datasets/about_map_batch)


----------
##  Citations

**Hugging face** `datasets` package documentation
- Home page [link](https://huggingface.co/docs/datasets/index)
- overview [doc](https://huggingface.co/docs/datasets/how_to)



